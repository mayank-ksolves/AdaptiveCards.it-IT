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
# <a name="render-a-card---xamarinandroid"></a>Eseguire il rendering di una scheda-Novell. Android

Di seguito viene illustrato come eseguire il rendering di una scheda utilizzando Novell. Android SDK.

## <a name="create-adaptive-card-object-instance-from-json-text"></a>Creare l'istanza dell'oggetto della scheda adattiva da testo JSON

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
AdaptiveCard adaptiveCard = parseResult.AdaptiveCard;
```

in alternativa, è anche possibile usare un oggetto ```ParseContext``` per poter deserializzare gli elementi personalizzati inclusi nella scheda adattiva, come indicato di seguito:

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

ParseContext context = new ParseContext(); // Empty parseContext so only known elements up to v1.2 will be parsed
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version, context);
```

o

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version, context);
```

## <a name="render-a-card"></a>Eseguire il rendering di una scheda

Per poter eseguire il rendering di una scheda, sono necessarie alcune informazioni
* contesto: ottenibile dall'attività in cui è ospitata la scheda
* fragmentManager: può essere recuperato anche dall'attività host
* cardActionHandler: istanza di [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md) per gestire il comportamento dell'azione

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
using AdaptiveCards.Rendering.Xamarin.Android.Renderer;
using AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler;
// ...

var renderedCard = AdaptiveCardRenderer.Instance.Render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
View v = renderedCard.View;
```
