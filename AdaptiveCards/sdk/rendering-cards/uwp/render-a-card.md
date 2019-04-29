---
title: Eseguire il rendering di una scheda - UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 1a72cb9ba72811d4e98a48116fa08245e13a6392
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552433"
---
# <a name="render-a-card---uwp"></a><span data-ttu-id="a83b2-102">Eseguire il rendering di una scheda - UWP</span><span class="sxs-lookup"><span data-stu-id="a83b2-102">Render a card - UWP</span></span>

<span data-ttu-id="a83b2-103">Di seguito viene illustrato come eseguire il rendering di una scheda tramite il SDK di piattaforma UWP.</span><span class="sxs-lookup"><span data-stu-id="a83b2-103">Here's how to render a card using the UWP SDK.</span></span>

## <a name="create-an-instance-of-your-renderer"></a><span data-ttu-id="a83b2-104">Creare un'istanza del renderer</span><span class="sxs-lookup"><span data-stu-id="a83b2-104">Create an instance of your renderer</span></span>

<span data-ttu-id="a83b2-105">Creare un'istanza della libreria di renderer.</span><span class="sxs-lookup"><span data-stu-id="a83b2-105">Create an instance of the renderer library.</span></span> 

```csharp
using AdaptiveCards.Rendering.Uwp;
// ...

var renderer = new AdaptiveCardRenderer();
```

## <a name="create-a-card-from-a-json-string"></a><span data-ttu-id="a83b2-106">Creare una scheda da una stringa JSON</span><span class="sxs-lookup"><span data-stu-id="a83b2-106">Create a card from a JSON string</span></span>

```csharp
var card = AdaptiveCard.FromJsonString(jsonString);
```

## <a name="create-a-card-from-a-json-object"></a><span data-ttu-id="a83b2-107">Creare una scheda da un oggetto JSON</span><span class="sxs-lookup"><span data-stu-id="a83b2-107">Create a card from a JSON object</span></span>

```csharp
var card = AdaptiveCard.FromJson(jsonObject);
```

## <a name="render-a-card"></a><span data-ttu-id="a83b2-108">Eseguire il rendering di una scheda</span><span class="sxs-lookup"><span data-stu-id="a83b2-108">Render a card</span></span>

<span data-ttu-id="a83b2-109">Acquisire una carta da un'origine ed eseguirne il rendering.</span><span class="sxs-lookup"><span data-stu-id="a83b2-109">Acquire a card from a source and render it.</span></span>

```csharp
RenderedAdaptiveCard renderedAdaptiveCard =  renderer.RenderAdaptiveCard(card);

// Check if the render was successful
if (renderedAdaptiveCard.FrameworkElement != null)
{
    // Get the framework element
    var uiCard = renderedAdaptiveCard.FrameworkElement;

    // Add it to your UI
    myGrid.Children.Add(uiCard);
}
```

## <a name="example"></a><span data-ttu-id="a83b2-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="a83b2-110">Example</span></span>

<span data-ttu-id="a83b2-111">Ecco un esempio tratto dal renderer UWP.</span><span class="sxs-lookup"><span data-stu-id="a83b2-111">Here is an example from the UWP renderer.</span></span>

```csharp
var renderer = new AdaptiveCardRenderer();
var card = AdaptiveCard.FromJsonString(jsonString);
var renderedAdaptiveCard = renderer.RenderAdaptiveCard(card.AdaptiveCard);
if (renderedAdaptiveCard.FrameworkElement != null)
{
    myGrid.Children.Add(renderedAdaptiveCard.FrameworkElement);
}
...
```