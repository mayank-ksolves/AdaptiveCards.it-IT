---
title: Eseguire il rendering di una scheda - .NET HTML SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 1bc1a225fc731aeb8e66bde1ef21a9443e74c8b1
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134173"
---
# <a name="render-a-card---net-html"></a><span data-ttu-id="067ec-102">Eseguire il rendering di una scheda - HTML .NET</span><span class="sxs-lookup"><span data-stu-id="067ec-102">Render a card - .NET HTML</span></span>

<span data-ttu-id="067ec-103">Ecco come eseguire il rendering di una scheda usando .NET HTML SDK.</span><span class="sxs-lookup"><span data-stu-id="067ec-103">Here's how to render a card using the .NET HTML SDK.</span></span>

## <a name="instantiate-a-renderer"></a><span data-ttu-id="067ec-104">Creare un'istanza di un renderer</span><span class="sxs-lookup"><span data-stu-id="067ec-104">Instantiate a renderer</span></span>

<span data-ttu-id="067ec-105">Il passaggio successivo consiste nel creare un'istanza del renderer.</span><span class="sxs-lookup"><span data-stu-id="067ec-105">The next step is to create an instance of the renderer.</span></span> 

```csharp
using AdaptiveCards;
using AdaptiveCards.Rendering;
using AdaptiveCards.Rendering.Html;
// ... 

// Create a card renderer
AdaptiveCardRenderer renderer = new AdaptiveCardRenderer();

// For fun, check the schema version this renderer supports
AdaptiveSchemaVersion schemaVersion = renderer.SupportedSchemaVersion; // 1.0
```

## <a name="render-a-card-to-html"></a><span data-ttu-id="067ec-106">Eseguire il rendering di una scheda in HTML</span><span class="sxs-lookup"><span data-stu-id="067ec-106">Render a card to HTML</span></span>

```csharp
// Build a simple card
// In the real world this would probably be provided as JSON
AdaptiveCard card = new AdaptiveCard()
{
    Body = { new AdaptiveTextBlock() { Text = "Hello World" } }
};

try
{
    // Render the card
    RenderedAdaptiveCard renderedCard = renderer.RenderCard(card);

    // Get the output HTML 
    HtmlTag html = renderedCard.Html;

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
