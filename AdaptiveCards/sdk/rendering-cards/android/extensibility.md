---
title: Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 378171186599dd8d103111da183b7fc2e6e01c42
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134250"
---
# <a name="extensibility---android"></a>Estendibilità - Android

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

Per definire un renderer personalizzato per il tipo, è innanzitutto necessario creare una classe estesa da BaseCardElementParser:
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

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
```

## <a name="custom-rendering-of-actions"></a>Rendering personalizzato di azioni

[!IMPORTANT]
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
        String catImnageUri = "http://adaptivecards.io/content/cats/1.png";
        byte[] bytes = HttpRequestHelper.get(catImnageUri);
        if (bytes == null)
        {
            throw new IOException("Failed to retrieve content from " + catImnageUri);
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
* loadOnlineImage (String, GenericImageLoaderAsync) è stato rinominato resolveImageResource(String, GenericImageLoaderAsync)
* è stato aggiunto un overload per resolveImageResource(String, GenericImageLoaderAsync) come resolveImageResource(String, GenericImageLoaderAsync, int) per supportare gli scenari in cui è necessaria la larghezza massima

## <a name="custom-media-loading"></a>Caricamento di file multimediali personalizzati

> [!IMPORTANT]
> **Ricorda che IOnlineMediaLoader richiede l'aggiunta di MediaDataSource nel livello API 23 o in Android M**

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
