---
title: Extensibility - HTML .NET SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 5aedc2b0bb19cb7a26caa16c8490d0d2f3c93282
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552533"
---
# <a name="extensibility---net-html"></a><span data-ttu-id="7e5eb-102">Extensibility - .NET HTML</span><span class="sxs-lookup"><span data-stu-id="7e5eb-102">Extensibility - .NET HTML</span></span>

## <a name="custom-element-rendering"></a><span data-ttu-id="7e5eb-103">Rendering di elemento personalizzato</span><span class="sxs-lookup"><span data-stu-id="7e5eb-103">Custom Element Rendering</span></span>

<span data-ttu-id="7e5eb-104">Per il controllo completo del renderer è possibile usare il `ElementRenderers` proprietà **aggiungere**, **rimuovere**, o **override** predefinito renderer.</span><span class="sxs-lookup"><span data-stu-id="7e5eb-104">For full control of the renderer you can use the `ElementRenderers` property to **add**, **remove**, or **override** default renderers.</span></span>

<span data-ttu-id="7e5eb-105">L'esempio seguente mostra come è possibile definire una classe personalizzata `"type": "Rating"` elemento ed eseguirne il rendering.</span><span class="sxs-lookup"><span data-stu-id="7e5eb-105">The following example shows how you could define a custom `"type": "Rating"` element and render it.</span></span>

```csharp
// Register the new type with the JSON parser
AdaptiveTypedElementConverter.RegisterTypedElement<MyCustomRating>();

// Add the new type to the element renderer registry
renderer.ElementRenderers.Set<MyCustomRating>(MyCustomRating.Render);

// Define a custom Rating element type
public class MyCustomRating : AdaptiveElement
{
    public override string Type => "Rating";

    public double Rating { get; set; }

    public AdaptiveTextSize Size { get; set; }

    public AdaptiveTextColor Color { get; set; }

    public static FrameworkElement Render(MyCustomRating rating, AdaptiveRenderContext context)
    {
        var textBlock = new AdaptiveTextBlock
        {
            Size = rating.Size,
            Color = rating.Color
        };
        for (int i = 0; i < rating.Rating; i++)
        {
            textBlock.Text += "\u2605";
        }
        textBlock.Text += $" ({rating.Rating})";
        return context.Render(textBlock);
    }
}
```