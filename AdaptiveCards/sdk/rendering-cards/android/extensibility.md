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
# <a name="extensibility---android"></a><span data-ttu-id="0f9e1-102">Estendibilità - Android</span><span class="sxs-lookup"><span data-stu-id="0f9e1-102">Extensibility - Android</span></span>

## <a name="custom-parsing-of-card-elements"></a><span data-ttu-id="0f9e1-103">Analisi personalizzata degli elementi della scheda</span><span class="sxs-lookup"><span data-stu-id="0f9e1-103">Custom Parsing of Card Elements</span></span>

<span data-ttu-id="0f9e1-104">Puoi estendere il parser per supportare gli elementi della scheda che hai definito.</span><span class="sxs-lookup"><span data-stu-id="0f9e1-104">You may extend the parser to support card elements that you have defined.</span></span> <span data-ttu-id="0f9e1-105">Supponiamo ad esempio di avere un nuovo tipo di elemento che si presenta come segue:</span><span class="sxs-lookup"><span data-stu-id="0f9e1-105">For example, say we have a new element type that looks like this:</span></span>
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

<span data-ttu-id="0f9e1-106">Le righe seguenti illustrano come analizzarlo in un CardElement esteso da BaseCardElement:</span><span class="sxs-lookup"><span data-stu-id="0f9e1-106">Then the following lines demonstrate how to parse it into a CardElement that extends from the BaseCardElement:</span></span>
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

<span data-ttu-id="0f9e1-107">Ecco come registrare il parser e ottenere un oggetto AdaptiveCard che contiene l'elemento personalizzato:</span><span class="sxs-lookup"><span data-stu-id="0f9e1-107">And this is how to register the parser and get an AdaptiveCard object that contains the custom element:</span></span>
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

<span data-ttu-id="0f9e1-108">Viene quindi eseguito il rendering dell'elemento personalizzato</span><span class="sxs-lookup"><span data-stu-id="0f9e1-108">Next comes rendering the custom element</span></span>

## <a name="custom-rendering-of-card-elements"></a><span data-ttu-id="0f9e1-109">Rendering personalizzato degli elementi della scheda</span><span class="sxs-lookup"><span data-stu-id="0f9e1-109">Custom Rendering of Card Elements</span></span>

<span data-ttu-id="0f9e1-110">Per definire un renderer personalizzato per il tipo, è innanzitutto necessario creare una classe estesa da BaseCardElementParser:</span><span class="sxs-lookup"><span data-stu-id="0f9e1-110">To define our own custom renderer for our type, we must first create a class that extends from BaseCardElementParser:</span></span>
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

<span data-ttu-id="0f9e1-111">Possiamo quindi registrare il renderer come segue:</span><span class="sxs-lookup"><span data-stu-id="0f9e1-111">We then register this renderer like so:</span></span>
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
```

## <a name="custom-rendering-of-actions"></a><span data-ttu-id="0f9e1-112">Rendering personalizzato di azioni</span><span class="sxs-lookup"><span data-stu-id="0f9e1-112">Custom rendering of actions</span></span>

[!IMPORTANT]
> <span data-ttu-id="0f9e1-113">Per la versione 1.2 sono previste modifiche del rendering personalizzato delle azioni, che tuttavia non sono state ancora completate</span><span class="sxs-lookup"><span data-stu-id="0f9e1-113">Changes to the custom rendering of actions are planned for v1.2 but are not completed yet</span></span>

## <a name="custom-image-loading"></a><span data-ttu-id="0f9e1-114">Caricamento di immagini personalizzate</span><span class="sxs-lookup"><span data-stu-id="0f9e1-114">Custom image loading</span></span>

### <a name="ionlineimageloader"></a><span data-ttu-id="0f9e1-115">IOnlineImageLoader</span><span class="sxs-lookup"><span data-stu-id="0f9e1-115">IOnlineImageLoader</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0f9e1-116">**È possibile registrare un solo IOnlineImageLoader, che ha la precedenza rispetto alla modalità predefinita di recupero delle immagini**</span><span class="sxs-lookup"><span data-stu-id="0f9e1-116">**Only one IOnlineImageLoader can be registered and it takes precedence against the default way of retrieving images**</span></span>

<span data-ttu-id="0f9e1-117">IOnlineImageLoader è stato aggiunto per consentire agli sviluppatori di ottenere immagini che non è semplicemente possibile scaricare o recuperare da un'origine online o che richiedono passaggi precedenti prima del recupero.</span><span class="sxs-lookup"><span data-stu-id="0f9e1-117">In order to allow developers to get images that could not just be downloaded or retrieved from an online source or required previous steps before they could be retrieved, the IOnlineImageLoader was added to solve this kind of situations.</span></span> <span data-ttu-id="0f9e1-118">Per implementare OnlineImageLoader, è sufficiente implementare il metodo</span><span class="sxs-lookup"><span data-stu-id="0f9e1-118">To implement an OnlineImageLoader you must only implement the method</span></span> 

```java
public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
```

<span data-ttu-id="0f9e1-119">Di seguito è riportato un esempio di un elemento OnlineImageLoader che cambia tutte le immagini nell'immagine di un gatto</span><span class="sxs-lookup"><span data-stu-id="0f9e1-119">Here's an example of an OnlineImageLoader which changes all images for a cat image</span></span>

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

<span data-ttu-id="0f9e1-120">Infine, per registrare il caricatore di immagini, basta aggiungere questa riga nel codice.</span><span class="sxs-lookup"><span data-stu-id="0f9e1-120">Finally, to register this image loader, you must only add this line to your code.</span></span>

```java
CardRendererRegistration.getInstance().registerOnlineImageLoader(new OnlineImageLoader());
```

### <a name="iresourceresolver-deprecates-ionlineimageloader"></a><span data-ttu-id="0f9e1-121">IResourceResolver (rende deprecato IOnlineImageLoader)</span><span class="sxs-lookup"><span data-stu-id="0f9e1-121">IResourceResolver (deprecates IOnlineImageLoader)</span></span>

<span data-ttu-id="0f9e1-122">Per la versione 1.2, al renderer di Android è stato aggiunto il supporto completo per i ResourceResolver.</span><span class="sxs-lookup"><span data-stu-id="0f9e1-122">For v1.2, the support for full ResourceResolvers was added to the android renderer.</span></span> <span data-ttu-id="0f9e1-123">L'implementazione di un resolver di risorse è molto simile a quella di un IOnlineImageLoader, ma l'uso dei ResourceResolver consente agli sviluppatori di aggiungere diversi modi per recuperare le immagini da qualsiasi tipo di origine in una sola scheda. Questa operazione viene eseguita mediante il collegamento di ogni ResourceResolver a un prefisso univoco, a cui verrà inviata una query durante il tentativo di recuperare un'immagine.</span><span class="sxs-lookup"><span data-stu-id="0f9e1-123">The implementation of a resource resolver is really similar to that of a IOnlineImageLoader but having ResourceResolvers allows a developer to add multiple ways to retrieve images from any kind of source in a single card, this is done by linking each ResourceResolver to a unique prefix which will be queried when trying to retrieve an image.</span></span> 

<span data-ttu-id="0f9e1-124">È possibile implementare un ResourceResolver simile al seguente</span><span class="sxs-lookup"><span data-stu-id="0f9e1-124">You can implement a ResourceResolver similar to this</span></span>

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

<span data-ttu-id="0f9e1-125">Come accennato in precedenza, è possibile registrare più ResourceResolver. Per registrare un ResourceResolver, puoi procedere come segue</span><span class="sxs-lookup"><span data-stu-id="0f9e1-125">As mentioned previously, you can register multiple ResourceResolvers, to register a ResourceResolver you can do this</span></span>

```java
 CardRendererRegistration.getInstance().registerResourceResolver("data", new ResourceResolver());
 CardRendererRegistration.getInstance().registerResourceResolver("anotherPrefix", new AnotherResourceResolver());
```

#### <a name="transforming-an-ionlineimageloader-to-an-iresourceresolver"></a><span data-ttu-id="0f9e1-126">Trasformazione di un IOnlineImageLoader in un IResourceResolver</span><span class="sxs-lookup"><span data-stu-id="0f9e1-126">Transforming an IOnlineImageLoader to an IResourceResolver</span></span> 

<span data-ttu-id="0f9e1-127">Trasformare un IOnlineImageLoader in un IResourceResolver è un'attività piuttosto semplice, perché i metodi di quest'ultimo sono stati mantenuti quanto più simili possibile a quelli di IOnlineImageLoader</span><span class="sxs-lookup"><span data-stu-id="0f9e1-127">Transforming an IOnlineImageLoader to an IResourceResolver is a fairly easy task as the methods for the latter were tried to keep as similar as the IOnlineImageLoader as possible</span></span>

```java
 // IOnlineImageLoader
 public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException

 // IResourceResolver
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
```

<span data-ttu-id="0f9e1-128">Come puoi notare, le modifiche principali sono</span><span class="sxs-lookup"><span data-stu-id="0f9e1-128">As you can see, the biggest changes are</span></span>
* <span data-ttu-id="0f9e1-129">loadOnlineImage (String, GenericImageLoaderAsync) è stato rinominato resolveImageResource(String, GenericImageLoaderAsync)</span><span class="sxs-lookup"><span data-stu-id="0f9e1-129">loadOnlineImage(String, GenericImageLoaderAsync) was renamed to resolveImageResource(String, GenericImageLoaderAsync)</span></span>
* <span data-ttu-id="0f9e1-130">è stato aggiunto un overload per resolveImageResource(String, GenericImageLoaderAsync) come resolveImageResource(String, GenericImageLoaderAsync, int) per supportare gli scenari in cui è necessaria la larghezza massima</span><span class="sxs-lookup"><span data-stu-id="0f9e1-130">an overload for resolveImageResource(String, GenericImageLoaderAsync) was added as resolveImageResource(String, GenericImageLoaderAsync, int) in order to support scenarios where the max width is required</span></span>

## <a name="custom-media-loading"></a><span data-ttu-id="0f9e1-131">Caricamento di file multimediali personalizzati</span><span class="sxs-lookup"><span data-stu-id="0f9e1-131">Custom media loading</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0f9e1-132">**Ricorda che IOnlineMediaLoader richiede l'aggiunta di MediaDataSource nel livello API 23 o in Android M**</span><span class="sxs-lookup"><span data-stu-id="0f9e1-132">**Remember IOnlineMediaLoader requires MediaDataSource was added in API level 23 or Android M**</span></span>

<span data-ttu-id="0f9e1-133">Oltre all'inclusione dell'elemento per i file multimediali, è stata anche inclusa l'interfaccia IOnlineMediaLoader, che consente agli sviluppatori di eseguire l'override dell'oggetto [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) usato per l'elemento mediaPlayer sottostante.</span><span class="sxs-lookup"><span data-stu-id="0f9e1-133">Along with the inclusion of the media element, also was the inclusion of the IOnlineMediaLoader interface which allows developers to override the [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) used for the underlying mediaPlayer element.</span></span> <span data-ttu-id="0f9e1-134">**(Richiede Android M)**</span><span class="sxs-lookup"><span data-stu-id="0f9e1-134">**(Requires android M)**</span></span>

<span data-ttu-id="0f9e1-135">La prima operazione che è necessario eseguire è creare una classe che implementa IOnlineImageLoader</span><span class="sxs-lookup"><span data-stu-id="0f9e1-135">The first needed thing to do is creating a class that implements IOnlineImageLoader</span></span>

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

<span data-ttu-id="0f9e1-136">Una volta implementata questa classe, puoi registrare la classe OnlineMediaLoader aggiungendo</span><span class="sxs-lookup"><span data-stu-id="0f9e1-136">Once this class has been implemented, you can register your OnlineMediaLoader class by adding</span></span> 
```java
  CardRendererRegistration.getInstance().registerOnlineMediaLoader(new OnlineMediaLoader());
```
