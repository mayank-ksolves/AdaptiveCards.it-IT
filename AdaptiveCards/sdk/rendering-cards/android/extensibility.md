---
title: Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 735f0f8ed1f0d3fdc78f1c840a7aba1892faa5d4
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553363"
---
# <a name="extensibility---android"></a><span data-ttu-id="9e37a-102">Extensibility - Android</span><span class="sxs-lookup"><span data-stu-id="9e37a-102">Extensibility - Android</span></span>

## <a name="custom-parsing-of-card-elements"></a><span data-ttu-id="9e37a-103">L'analisi personalizzata di elementi Smart Card</span><span class="sxs-lookup"><span data-stu-id="9e37a-103">Custom Parsing of Card Elements</span></span>

<span data-ttu-id="9e37a-104">È possibile estendere il parser agli elementi di carta del supporto che sono state definite.</span><span class="sxs-lookup"><span data-stu-id="9e37a-104">You may extend the parser to suport card elements that you have defined.</span></span> <span data-ttu-id="9e37a-105">Ad esempio, supponiamo di che avere un nuovo tipo di elemento che si presenta come segue:</span><span class="sxs-lookup"><span data-stu-id="9e37a-105">For example, say we have a new element type that looks like this:</span></span>
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

<span data-ttu-id="9e37a-106">Quindi le righe seguenti viene illustrato come analizzare in un CardElement compreso tra il BaseCardElement:</span><span class="sxs-lookup"><span data-stu-id="9e37a-106">Then the following lines demonstrate how to parse it into a CardElement that extends from the BaseCardElement:</span></span>
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

<span data-ttu-id="9e37a-107">E qui viene illustrato come registrare il parser e ottenere un oggetto AdaptiveCard che contiene l'elemento personalizzato:</span><span class="sxs-lookup"><span data-stu-id="9e37a-107">And this is how to register the parser and get an AdaptiveCard object that contains the custom element:</span></span>
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

<span data-ttu-id="9e37a-108">Segue quindi il rendering dell'elemento personalizzato</span><span class="sxs-lookup"><span data-stu-id="9e37a-108">Next comes rendering the custom element</span></span>

## <a name="custom-rendering-of-card-elements"></a><span data-ttu-id="9e37a-109">Per il Rendering personalizzata di elementi Smart Card</span><span class="sxs-lookup"><span data-stu-id="9e37a-109">Custom Rendering of Card Elements</span></span>

<span data-ttu-id="9e37a-110">Per definire un renderer personalizzato per il tipo, è necessario creare innanzitutto una classe che si estende dal BaseCardElementParser:</span><span class="sxs-lookup"><span data-stu-id="9e37a-110">To define our own custom renderer for our type, we must first create a class that extends from BaseCardElementParser:</span></span>
```java
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(Context context, FragmentManager fragmentManager, ViewGroup viewGroup, BaseCardElement baseCardElement, Vector<IInputHandler> inputActionHandlerList, ICardActionHandler cardActionHandler, HostConfig hostConfig, ContainerStyle containerStyle) {

        //Call findImplObj on baseCardElement to get the instace we returned at parse. We can then cast that object to our type
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

<span data-ttu-id="9e37a-111">Abbiamo quindi registrare questo renderer come segue:</span><span class="sxs-lookup"><span data-stu-id="9e37a-111">We then register this renderer like so:</span></span>
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
```

