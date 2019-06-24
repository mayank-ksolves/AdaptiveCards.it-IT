---
title: Estendibilità - .NET WPF SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 4f89784f711727deb538b2ed2195007ca8e6aca1
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134317"
---
# <a name="extensibility---net-wpf"></a><span data-ttu-id="69da6-102">Estendibilità - WPF .NET</span><span class="sxs-lookup"><span data-stu-id="69da6-102">Extensibility - .NET WPF</span></span>

## <a name="custom-element-rendering"></a><span data-ttu-id="69da6-103">Rendering di elementi personalizzati</span><span class="sxs-lookup"><span data-stu-id="69da6-103">Custom Element Rendering</span></span>

<span data-ttu-id="69da6-104">Per un controllo completo del renderer, puoi usare la proprietà `ElementRenderers` per **aggiungere**, **rimuovere** o **eseguire l'override** del renderer predefinito.</span><span class="sxs-lookup"><span data-stu-id="69da6-104">For full control of the renderer you can use the `ElementRenderers` property to **add**, **remove**, or **override** default renderers.</span></span>

<span data-ttu-id="69da6-105">L'esempio seguente mostra come definire un elemento `"type": "Rating"` personalizzato ed eseguirne il rendering.</span><span class="sxs-lookup"><span data-stu-id="69da6-105">The following example shows how you could define a custom `"type": "Rating"` element and render it.</span></span>

```csharp
// Register the new type with the JSON parser
AdaptiveTypedElementConverter.RegisterTypedElement<MyCustomRating>();

// Add the new type to the element renderer registry
renderer.ElementRenderers.Set<MyCustomRating>(MyCustomRating.Render);

// Define a custom Rating element type
public class MyCustomRating : AdaptiveElement
{
    public MyCustomRating() { Type = "Rating"; }

    public override string Type { get; set; }

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
