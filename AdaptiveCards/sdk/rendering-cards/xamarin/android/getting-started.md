---
title: Xamarin.Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: cd8dccd2aece23dd67ee8d601e8efaa2a1bcd4f2
ms.sourcegitcommit: 588f3e97ed3de96dfff54906ac666ce42ef1e7f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928831"
---
# <a name="getting-started---xamarinandroid"></a>Guida introduttiva-Novell. Android

Si tratta di una libreria renderer che è destinata alle applicazioni native Novell Android ed è basata sul renderer Android che è possibile trovare [qui](../../android/getting-started.md). 

## <a name="nuget-install"></a>Installazione di NuGet

[![Installazione di Nuget](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Xamarin.Android.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Xamarin.Android)

[Qui](http://nuget.org) è possibile trovare i pacchetti pubblicati

```console
Install-Package AdaptiveCards.Rendering.Xamarin.Android -Version 0.1.0-alpha
```

## <a name="namespace"></a>Spazio dei nomi

Gli spazi dei nomi necessari per l'utilizzo di questa libreria sono
```csharp
// To import the base object model classes as AdaptiveCard, TextBlock, Column, ShowCardAction, ...
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;

// To import the AdaptiveCardRenderer class
using AdaptiveCards.Rendering.Xamarin.Android.Renderer;

// To import the ICardActionHandler interface
using AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler;

// To use feature registration and register custom behaviour 
using AdaptiveCards.Rendering.Xamarin.Android.Renderer.Registration;
```

## <a name="xamarinandroid-visualizer-sample"></a>Esempio del Visualizzatore Novell. Android

L' [esempio di Visualizzatore Novell. Android](https://github.com/Microsoft/AdaptiveCards/tree/main/source/xamarin/Xamarin.Droid.Sample) consente di visualizzare le schede usando Novell. Android. Se hai mai usato l'applicazione di esempio Android, scoprirai che l'esperienza è molto simile.

## <a name="next-steps"></a>Passaggi successivi

Per un controllo introduttivo, [eseguire il rendering di una scheda](render-a-card.md) per i passaggi successivi.

Per una visualizzazione più approfondita delle classi associate alla libreria renderer Novell. Android, è possibile verificare alcune delle classi associate facendo clic su di esse sotto:
* [```AdaptiveCard```](adaptivecards-rendering-xamarin-android-objectmodel-adaptivecard.md)
* [```AdaptiveCardRenderer```](adaptivecards-rendering-xamarin-android-renderer-adaptivecardrenderer.md)
* [```CardRendererRegistration```](adaptivecards-rendering-xamarin-android-renderer-cardrendererregistration.md)
* [```FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md)
* [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md)
* [```RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md)
