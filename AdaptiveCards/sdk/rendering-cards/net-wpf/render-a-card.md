---
title: Eseguire il rendering di una scheda - .NET WPF SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: f847b83a17456dbf80f869ef8ef0df699e57f50e
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134292"
---
# <a name="render-a-card---net-wpf"></a><span data-ttu-id="67412-102">Eseguire il rendering di una scheda - WPF .NET</span><span class="sxs-lookup"><span data-stu-id="67412-102">Render a card - .NET WPF</span></span>

<span data-ttu-id="67412-103">Ecco come eseguire il rendering di una scheda usando .NET WPF SDK.</span><span class="sxs-lookup"><span data-stu-id="67412-103">Here's how to render a card using the .NET WPF SDK.</span></span>

> [!NOTE]
> <span data-ttu-id="67412-104">**`Media` con gli URL HTTPS non funziona in WPF**</span><span class="sxs-lookup"><span data-stu-id="67412-104">**`Media` with HTTPS URLs will not work in WPF**</span></span>
> 
> <span data-ttu-id="67412-105">A causa di un [bug nel controllo WPF MediaElement](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception), non è possibile eseguire il rendering dei file multimediali resi disponibili tramite HTTPS.</span><span class="sxs-lookup"><span data-stu-id="67412-105">Due to a [bug in the WPF MediaElement control](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception) we aren't able to render media that is served via HTTPS.</span></span> <span data-ttu-id="67412-106">È consigliabile usare URL HTTP nell'elemento `Media` finché il problema non verrà risolto.</span><span class="sxs-lookup"><span data-stu-id="67412-106">You should use HTTP URLs in the `Media` element until this is addressed.</span></span>  

## <a name="instantiate-a-renderer"></a><span data-ttu-id="67412-107">Creare un'istanza di un renderer</span><span class="sxs-lookup"><span data-stu-id="67412-107">Instantiate a renderer</span></span>

<span data-ttu-id="67412-108">Crea un'istanza della libreria del renderer.</span><span class="sxs-lookup"><span data-stu-id="67412-108">Create an instance of the renderer library.</span></span> 

```csharp
using AdaptiveCards;
using AdaptiveCards.Rendering;
using AdaptiveCards.Rendering.Wpf;
// ...

// Create a card renderer
AdaptiveCardRenderer renderer = new AdaptiveCardRenderer();

// If using the Xceed package, enable the enhanced input
renderer.UseXceedElementRenderers();

// For fun, check the schema version this renderer supports
AdaptiveSchemaVersion schemaVersion = renderer.SupportedSchemaVersion;
```

## <a name="render-a-card-to-xaml"></a><span data-ttu-id="67412-109">Eseguire il rendering di una scheda in XAML</span><span class="sxs-lookup"><span data-stu-id="67412-109">Render a card to XAML</span></span>

```csharp
// Build a simple card
// In the real world this would probably be provided as JSON
AdaptiveCard card = new AdaptiveCard("1.0")
{
    Body = { new AdaptiveTextBlock() { Text = "Hello World" } }
};

try
{
    // Render the card
    RenderedAdaptiveCard renderedCard = renderer.RenderCard(card);

    // Get the FrameworkElement
    // Add this to your app's UI somewhere
    FrameworkElement fe = renderedCard.FrameworkElement;

    // (Optional) Check for any renderer warnings
    // This includes things like an unknown element type found in the card
    // Or the card exceeded the maximum number of supported actions, etc
    IList<AdaptiveWarning> warnings = renderedCard.Warnings;
}
catch(AdaptiveException ex)
{
    // Failed rendering
}
```

