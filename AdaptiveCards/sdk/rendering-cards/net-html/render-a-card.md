---
title: Eseguire il rendering di una scheda - .NET HTML SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 3ecc0e3bc30c8750cbe40dbf94946ab604b492ce
ms.sourcegitcommit: c921a7bb15a95c0ceb803ad375501ee3b8bef028
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2020
ms.locfileid: "83631337"
---
# <a name="render-a-card---net-html"></a>Eseguire il rendering di una scheda - HTML .NET

Ecco come eseguire il rendering di una scheda usando .NET HTML SDK.

## <a name="instantiate-a-renderer"></a>Creare un'istanza di un renderer

Il passaggio successivo consiste nel creare un'istanza del renderer. 

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

## <a name="render-a-card-to-html"></a>Eseguire il rendering di una scheda in HTML

```csharp
// Build a simple card
// In the real world this would probably be provided as JSON
AdaptiveCard card = new AdaptiveCard(renderer.SupportedSchemaVersion)
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
