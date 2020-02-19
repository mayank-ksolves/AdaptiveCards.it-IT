---
title: Estendibilità-.NET HTML SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: d1df38608abde9ad26c78bbc5f66eb3bbb3d1971
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454534"
---
# <a name="extensibility---net-html"></a><span data-ttu-id="050ce-102">Estendibilità-HTML .NET</span><span class="sxs-lookup"><span data-stu-id="050ce-102">Extensibility - .NET HTML</span></span>

## <a name="custom-element-rendering"></a><span data-ttu-id="050ce-103">Rendering di elementi personalizzati</span><span class="sxs-lookup"><span data-stu-id="050ce-103">Custom Element Rendering</span></span>

<span data-ttu-id="050ce-104">Per un controllo completo del renderer, puoi usare la proprietà `ElementRenderers` per **aggiungere**, **rimuovere** o **eseguire l'override** del renderer predefinito.</span><span class="sxs-lookup"><span data-stu-id="050ce-104">For full control of the renderer you can use the `ElementRenderers` property to **add**, **remove**, or **override** default renderers.</span></span>

<span data-ttu-id="050ce-105">L'esempio seguente mostra come definire un elemento `"type": "Rating"` personalizzato ed eseguirne il rendering.</span><span class="sxs-lookup"><span data-stu-id="050ce-105">The following example shows how you could define a custom `"type": "Rating"` element and render it.</span></span>

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
