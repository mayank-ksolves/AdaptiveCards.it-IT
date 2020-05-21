---
title: Estensibilità Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 1281a31c333474c1899831acab28c962ce8e4514
ms.sourcegitcommit: c921a7bb15a95c0ceb803ad375501ee3b8bef028
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2020
ms.locfileid: "83631313"
---
# <a name="extensibility---android"></a>Estendibilità - Android

Il renderer Android può essere esteso per supportare più scenari, tra cui:
* [Analisi personalizzata degli elementi della scheda](#custom-parsing-of-card-elements)
* [Rendering personalizzato degli elementi della scheda](#custom-rendering-of-card-elements)
* [Rendering personalizzato delle azioni (a](#custom-rendering-of-actions) partire dalla versione 1.2)
* [Caricamento di immagini personalizzate](#custom-image-loading) (a partire dalla versione 1.0.1)
* [Caricamento di supporti personalizzati](#custom-media-loading) (a partire dalla versione 1.1)

## <a name="custom-parsing-of-card-elements"></a>Analisi personalizzata degli elementi della scheda

Puoi estendere il parser per supportare gli elementi della scheda che hai definito. Supponiamo ad esempio di avere un nuovo tipo di elemento che si presenta come segue:
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

Le righe seguenti illustrano come analizzarlo in un CardElement esteso da BaseCardElement:
```java
public class MyCustomCardElement extends BaseCardElement
{

    public MyCustomCardElement(CardElementType type) {
        super(type);
    }

    public String getMyTypeData()
    {
        return myTypeData;
    }

    public void setMyTypeData(String data)
    {
        myTypeData = data;
    }

    private String myTypeData;
}

public class MyCardElementParser extends BaseCardElementParser
{
    @Override
    public BaseCardElement Deserialize(ElementParserRegistration elementParserRegistration, ActionParserRegistration actionParserRegistration, JsonValue value)
    {
        MyCustomCardElement element = new CustomCardElement(CardElementType.Custom);
        element.SetElementTypeString("MyType");
        String val = value.getString();
        try {
            JSONObject obj = new JSONObject(val);
            element.setMyTypeData(obj.getString("secret"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setMyTypeData("Failed");
        }
        return element;
    }
}
```

Ecco come registrare il parser e ottenere un oggetto AdaptiveCard che contiene l'elemento personalizzato:
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

Viene quindi eseguito il rendering dell'elemento personalizzato

## <a name="custom-rendering-of-card-elements"></a>Rendering personalizzato degli elementi della scheda

> [!IMPORTANT]
>
> **Elenco di modifiche di rilievo**
>
> [Modifiche importanti per la versione 1.2](#breaking-changes-for-v12)

Per definire un renderer personalizzato per il tipo, è necessario innanzitutto creare una classe che si estende da ```BaseCardElementRenderer``` :
```java
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(Context context, FragmentManager fragmentManager, ViewGroup viewGroup, BaseCardElement baseCardElement, Vector<IInputHandler> inputActionHandlerList, ICardActionHandler cardActionHandler, HostConfig hostConfig, ContainerStyle containerStyle) {

        //Call findImplObj on baseCardElement to get the instance we returned at parse. We can then cast that object to our type
        CustomCardElement element = (CustomCardElement) baseCardElement.findImplObj();

        //Create some view and add it to the view group
        TextView textView = new TextView(context);
        textView.setText(element.getMyTypeData());
        textView.setAllCaps(true);
        viewGroup.addView(textView);

        //return the view
        return textView;
    }
}
```

Possiamo quindi registrare il renderer come segue:
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler,  hostConfig);
```

### <a name="breaking-changes-for-v12"></a>Modifiche importanti per la versione 1.2

Il ```render``` metodo è stato modificato in modo da includere il ```RenderedAdaptiveCard``` parametro ed ```ContainerStyle``` è stato modificato per un RenderArgs in cui ContainerStyle è ora contenuto, quindi una classe che estende BaseCardElementRenderer dovrebbe essere simile alla seguente

```
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(RenderedAdaptiveCard renderedAdaptiveCard, Context context, FragmentManager fragmentManager, ViewGroup viewGroup,
                       BaseCardElement baseCardElement, ICardActionHandler cardActionHandler, HostConfig hostConfig, RenderArgs renderArgs)
    { }
}
```

## <a name="custom-parsing-of-card-actions"></a>Analisi personalizzata delle azioni della scheda

Analogamente all'analisi degli elementi della scheda personalizzati nella versione 1.2, è stata introdotta la possibilità di analizzare le azioni personalizzate. Ad esempio, supponiamo di avere un nuovo tipo di azione simile al seguente:
```json
{
    "type" : "MyAction",
    "ActionData" : "My data"
}
```

Nelle righe seguenti viene illustrato come analizzarlo in un Actionelement che si estende da ```BaseActionElement``` :
```java
public class MyActionElement extends BaseActionElement
{
    public MyActionElement(ActionType type) 
    {
        super(type);
    }

    public String getActionData()
    {
        return mActionData;
    }

    public void setActionData(String s)
    {
        mActionData = s;
    }

    private String mActionData;
    public static final String MyActionId = "myAction";
}

public class MyActionParser extends ActionElementParser
{
    @Override
    public BaseActionElement Deserialize(ParseContext context, JsonValue value)
    {
        MyActionElement element = new MyActionElement(ActionType.Custom);
        element.SetElementTypeString(MyActionElement.MyActionId);
        String val = value.getString();
        try {
            JSONObject obj = new JSONObject(val);
            element.setActionData(obj.getString("ActionData"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setActionData("Failure");
        }
        return element;
    }

    @Override
    public BaseActionElement DeserializeFromString(ParseContext context, String jsonString)
    {
        MyActionElement element = new MyActionElement(ActionType.Custom);
        element.SetElementTypeString(MyActionElement.MyActionId);
        try {
            JSONObject obj = new JSONObject(jsonString);
            element.setBackwardString(obj.getString("ActionData"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setBackwardString("Failure");
        }
        return element;
    }
}
```

E le righe successive dimostrano come registrare il parser e ottenere un oggetto AdaptiveCard che contiene l'elemento azione personalizzata:
```java
// Create an ActionParserRegistration and add your parser to it
ActionParserRegistration actionParserRegistration = new ActionParserRegistration();
actionParserRegistration.AddParser(MyActionElement.MyActionId, new MyActionParser());

ParseContext context = new ParseContext(null, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

Viene quindi eseguito il rendering dell'azione personalizzata

## <a name="custom-rendering-of-actions"></a>Rendering personalizzato delle azioni

Per definire il renderer dell'azione personalizzata per il tipo, è necessario innanzitutto creare una classe che si estende da ```BaseActionElementRenderer``` :
```java
public class MyActionRenderer extends BaseActionElementRenderer
{
    @Override
    public Button render(RenderedAdaptiveCard renderedCard,
                         Context context,
                         FragmentManager fragmentManager,
                         ViewGroup viewGroup,
                         BaseActionElement baseActionElement,
                         ICardActionHandler cardActionHandler,
                         HostConfig hostConfig,
                         RenderArgs renderArgs)
    {
        Button myActionButton = new Button(context);

        CustomActionElement customAction = (CustomActionElement) baseActionElement.findImplObj();

        myActionButton.setBackgroundColor(getResources().getColor(R.color.greenActionColor));
        myActionButton.setText(customAction.getMessage());
        myActionButton.setAllCaps(false);
        myActionButton.setOnClickListener(new BaseActionElementRenderer.ActionOnClickListener(renderedCard, baseActionElement, cardActionHandler));

        viewGroup.addView(myActionButton);

        return myActionButton;
    }
}
```

Possiamo quindi registrare il renderer come segue:
```java
CardRendererRegistration.getInstance().registerActionRenderer("myAction", new CustomActionRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
```

## <a name="custom-rendering-of-actions"></a>Rendering personalizzato di azioni

> [!IMPORTANT]
> Per la versione 1.2 sono previste modifiche del rendering personalizzato delle azioni, che tuttavia non sono state ancora completate

## <a name="custom-image-loading"></a>Caricamento di immagini personalizzate

### <a name="ionlineimageloader"></a>IOnlineImageLoader

> [!IMPORTANT]
> **È possibile registrare un solo IOnlineImageLoader, che ha la precedenza rispetto alla modalità predefinita di recupero delle immagini**

IOnlineImageLoader è stato aggiunto per consentire agli sviluppatori di ottenere immagini che non è semplicemente possibile scaricare o recuperare da un'origine online o che richiedono passaggi precedenti prima del recupero. Per implementare OnlineImageLoader, è sufficiente implementare il metodo 

```java
public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
```

Di seguito è riportato un esempio di un elemento OnlineImageLoader che cambia tutte le immagini nell'immagine di un gatto

```java
public class OnlineImageLoader implements IOnlineImageLoader
{
    public OnlineImageLoader(){}

    @Override
    public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
    {
        String catImageUri = "http://adaptivecards.io/content/cats/1.png";
        byte[] bytes = HttpRequestHelper.get(catImageUri);
        if (bytes == null)
        {
            throw new IOException("Failed to retrieve content from " + catImageUri);
        }

        Bitmap bitmap = BitmapFactory.decodeByteArray(bytes, 0, bytes.length);

        if (bitmap == null)
        {
            throw new IOException("Failed to convert content to bitmap: " + new String(bytes));
        }

        return new HttpRequestResult<>(bitmap);
    }
}
```

Infine, per registrare il caricatore di immagini, basta aggiungere questa riga nel codice.

```java
CardRendererRegistration.getInstance().registerOnlineImageLoader(new OnlineImageLoader());
```

### <a name="iresourceresolver-deprecates-ionlineimageloader"></a>IResourceResolver (rende deprecato IOnlineImageLoader)

Per la versione 1.2, al renderer di Android è stato aggiunto il supporto completo per i ResourceResolver. L'implementazione di un resolver di risorse è molto simile a quella di un IOnlineImageLoader, ma l'uso dei ResourceResolver consente agli sviluppatori di aggiungere diversi modi per recuperare le immagini da qualsiasi tipo di origine in una sola scheda. Questa operazione viene eseguita mediante il collegamento di ogni ResourceResolver a un prefisso univoco, a cui verrà inviata una query durante il tentativo di recuperare un'immagine. 

È possibile implementare un ResourceResolver simile al seguente

```java
public class ResourceResolver implements IResourceResolver
{
    @Override
    public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
    {
        Bitmap bitmap;
        String dataUri = AdaptiveBase64Util.ExtractDataFromUri(uri);
        CharVector decodedDataUri = AdaptiveBase64Util.Decode(dataUri);
        byte[] decodedByteArray = Util.getBytes(decodedDataUri);
        bitmap = BitmapFactory.decodeByteArray(decodedByteArray, 0, decodedByteArray.length);

        return new HttpRequestResult<>(bitmap);
    }

    @Override
    public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
    {
        Bitmap bitmap;
        String dataUri = AdaptiveBase64Util.ExtractDataFromUri(uri);
        CharVector decodedDataUri = AdaptiveBase64Util.Decode(dataUri);

        if (uri.startsWith("data:image/svg")) {
            String svgString = AdaptiveBase64Util.ExtractDataFromUri(uri);
            String decodedSvgString = URLDecoder.decode(svgString, "UTF-8");
            Sharp sharp = Sharp.loadString(decodedSvgString);
            Drawable drawable = sharp.getDrawable();
            bitmap = ImageUtil.drawableToBitmap(drawable, maxWidth);
        }
        else
        {
            try
            {
                return genericImageLoaderAsync.loadDataUriImage(uri);
            }
            catch (Exception e)
            {
                return new HttpRequestResult<>(e);
            }
        }

        return new HttpRequestResult<>(bitmap);
    }
}
```

Come accennato in precedenza, è possibile registrare più ResourceResolver. Per registrare un ResourceResolver, puoi procedere come segue

```java
 CardRendererRegistration.getInstance().registerResourceResolver("data", new ResourceResolver());
 CardRendererRegistration.getInstance().registerResourceResolver("anotherPrefix", new AnotherResourceResolver());
```

#### <a name="transforming-an-ionlineimageloader-to-an-iresourceresolver"></a>Trasformazione di un IOnlineImageLoader in un IResourceResolver 

Trasformare un IOnlineImageLoader in un IResourceResolver è un'attività piuttosto semplice, perché i metodi di quest'ultimo sono stati mantenuti quanto più simili possibile a quelli di IOnlineImageLoader

```java
 // IOnlineImageLoader
 public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException

 // IResourceResolver
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
```

Come puoi notare, le modifiche principali sono

* ```loadOnlineImage(String, GenericImageLoaderAsync)``` è stato rinominato ```resolveImageResource(String, GenericImageLoaderAsync)```
* un overload per ```resolveImageResource(String, GenericImageLoaderAsync)``` è stato aggiunto come per ```resolveImageResource(String, GenericImageLoaderAsync, int)``` supportare scenari in cui è richiesta la larghezza massima

## <a name="custom-media-loading"></a>Caricamento di file multimediali personalizzati

> [!IMPORTANT]
> **```IOnlineMediaLoader```È necessario ricordare ```MediaDataSource``` che è stato aggiunto a livello API 23 o Android M**

Oltre all'inclusione dell'elemento per i file multimediali, è stata anche inclusa l'interfaccia IOnlineMediaLoader, che consente agli sviluppatori di eseguire l'override dell'oggetto [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) usato per l'elemento mediaPlayer sottostante. **(Richiede Android M)**

La prima operazione che è necessario eseguire è creare una classe che implementa IOnlineImageLoader

```java
@RequiresApi(api = Build.VERSION_CODES.M)
public class OnlineMediaLoader implements IOnlineMediaLoader
{
    /* This class checks if the media source exists */
    public class OnlineFileAvailableChecker extends AsyncTask<String, Void, Boolean>
    {
        public OnlineFileAvailableChecker(String uri)
        {
            m_uri = uri;
        }

        @Override
        protected Boolean doInBackground(String... strings) {
            // if the provided uri is a valid uri or is valid with the resource resolver, then use that
            // otherwise, try to get the media from a local file
            try
            {
                HttpRequestHelper.query(m_uri);
                return true;
            }
            catch (Exception e)
            {
                // Do nothing if the media was not found at all
                e.printStackTrace();
                return false;
            }
        }

        private String m_uri;
   }

       
   @Override
   public MediaDataSource loadOnlineMedia(MediaSourceVector mediaSources, IMediaDataSourceOnPreparedListener mediaDataSourceOnPreparedListener)
   {
       final long mediaSourcesSize = mediaSources.size();
       for(int i = 0; i < mediaSourcesSize; i++)
       {
           String mediaUri = mediaSources.get(i).GetUrl();

           OnlineFileAvailableChecker checker = new OnlineFileAvailableChecker(mediaUri);
           try
           {
               Boolean fileExists = checker.execute("").get();
               if(fileExists)
               {
                   return new MediaDataSourceImpl(mediaUri, mediaDataSourceOnPreparedListener);
               }
           }
           catch (Exception e) { }
       }
       return null;
    }
}
```

Una volta implementata questa classe, puoi registrare la classe OnlineMediaLoader aggiungendo 
```java
  CardRendererRegistration.getInstance().registerOnlineMediaLoader(new OnlineMediaLoader());
```
