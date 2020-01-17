---
title: Eseguire il rendering di una scheda Novell. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: dc1d48e05e99d6254b9253efa7145cefeb2ed17c
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145975"
---
# <a name="render-a-card---xamarinandroid"></a><span data-ttu-id="09f71-102">Eseguire il rendering di una scheda-Novell. Android</span><span class="sxs-lookup"><span data-stu-id="09f71-102">Render a card - Xamarin.Android</span></span>

<span data-ttu-id="09f71-103">Di seguito viene illustrato come eseguire il rendering di una scheda utilizzando Novell. Android SDK.</span><span class="sxs-lookup"><span data-stu-id="09f71-103">Here's how to render a card using the Xamarin.Android SDK.</span></span>

## <a name="create-adaptive-card-object-instance-from-json-text"></a><span data-ttu-id="09f71-104">Creare l'istanza dell'oggetto della scheda adattiva da testo JSON</span><span class="sxs-lookup"><span data-stu-id="09f71-104">Create Adaptive Card Object Instance from JSON Text</span></span>

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
AdaptiveCard adaptiveCard = parseResult.AdaptiveCard;
```

<span data-ttu-id="09f71-105">in alternativa, è anche possibile usare un oggetto ```ParseContext``` per poter deserializzare gli elementi personalizzati inclusi nella scheda adattiva, come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="09f71-105">or you can also use a ```ParseContext``` object to be able to deserialize custom elements that are included in your adaptive card like this:</span></span>

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

ParseContext context = new ParseContext(); // Empty parseContext so only known elements up to v1.2 will be parsed
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version, context);
```

<span data-ttu-id="09f71-106">o</span><span class="sxs-lookup"><span data-stu-id="09f71-106">or</span></span>

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version, context);
```

## <a name="render-a-card"></a><span data-ttu-id="09f71-107">Eseguire il rendering di una scheda</span><span class="sxs-lookup"><span data-stu-id="09f71-107">Render a card</span></span>

<span data-ttu-id="09f71-108">Per poter eseguire il rendering di una scheda, sono necessarie alcune informazioni</span><span class="sxs-lookup"><span data-stu-id="09f71-108">To be able to render a card you'll need some information</span></span>
* <span data-ttu-id="09f71-109">contesto: ottenibile dall'attività in cui è ospitata la scheda</span><span class="sxs-lookup"><span data-stu-id="09f71-109">context: Obtainable from the Activity the card is hosted in</span></span>
* <span data-ttu-id="09f71-110">fragmentManager: può essere recuperato anche dall'attività host</span><span class="sxs-lookup"><span data-stu-id="09f71-110">fragmentManager: can also be retrieved from the hosting activity</span></span>
* <span data-ttu-id="09f71-111">cardActionHandler: istanza di [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md) per gestire il comportamento dell'azione</span><span class="sxs-lookup"><span data-stu-id="09f71-111">cardActionHandler: instance of [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md) to manage the action behaviour</span></span>

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
using AdaptiveCards.Rendering.Xamarin.Android.Renderer;
using AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler;
// ...

var renderedCard = AdaptiveCardRenderer.Instance.Render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
View v = renderedCard.View;
```
