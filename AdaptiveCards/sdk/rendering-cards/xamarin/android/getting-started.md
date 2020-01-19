---
title: Xamarin.Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: a7fd40ac7f026e2a325e7dc52e10defe550fd43a
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146005"
---
# <a name="getting-started---xamarinandroid"></a><span data-ttu-id="c2d33-102">Guida introduttiva-Novell. Android</span><span class="sxs-lookup"><span data-stu-id="c2d33-102">Getting started - Xamarin.Android</span></span>

<span data-ttu-id="c2d33-103">Si tratta di una libreria renderer che è destinata alle applicazioni native Novell Android ed è basata sul renderer Android che è possibile trovare [qui](../../android/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="c2d33-103">This is a renderer library which targets native xamarin android applications and is based on the Android renderer that you can find [here](../../android/getting-started.md).</span></span> 

## <a name="nuget-install"></a><span data-ttu-id="c2d33-104">Installazione di NuGet</span><span class="sxs-lookup"><span data-stu-id="c2d33-104">NuGet install</span></span>

<span data-ttu-id="c2d33-105">[![Installazione di Nuget](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Xamarin.Android.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Xamarin.Android)</span><span class="sxs-lookup"><span data-stu-id="c2d33-105">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Xamarin.Android.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Xamarin.Android)</span></span>

<span data-ttu-id="c2d33-106">[Qui](http://nuget.org) è possibile trovare i pacchetti pubblicati</span><span class="sxs-lookup"><span data-stu-id="c2d33-106">You can find the published packages [here](http://nuget.org)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Xamarin.Android -Version 0.1.0-alpha
```

## <a name="namespace"></a><span data-ttu-id="c2d33-107">Spazio dei nomi</span><span class="sxs-lookup"><span data-stu-id="c2d33-107">Namespace</span></span>

<span data-ttu-id="c2d33-108">Gli spazi dei nomi necessari per l'utilizzo di questa libreria sono</span><span class="sxs-lookup"><span data-stu-id="c2d33-108">The necessary namespaces for using this library are</span></span>
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

## <a name="xamarinandroid-visualizer-sample"></a><span data-ttu-id="c2d33-109">Esempio del Visualizzatore Novell. Android</span><span class="sxs-lookup"><span data-stu-id="c2d33-109">Xamarin.Android Visualizer Sample</span></span>

<span data-ttu-id="c2d33-110">L' [esempio di Visualizzatore Novell. Android](https://github.com/Microsoft/AdaptiveCards/tree/master/source/xamarin/Xamarin.Droid.Sample) consente di visualizzare le schede usando Novell. Android.</span><span class="sxs-lookup"><span data-stu-id="c2d33-110">The [Xamarin.Android Visualizer sample](https://github.com/Microsoft/AdaptiveCards/tree/master/source/xamarin/Xamarin.Droid.Sample) lets you visualize cards using Xamarin.Android.</span></span> <span data-ttu-id="c2d33-111">Se hai mai usato l'applicazione di esempio Android, scoprirai che l'esperienza è molto simile.</span><span class="sxs-lookup"><span data-stu-id="c2d33-111">If you have ever used the Android sample application you'll find the experience to be really similar.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c2d33-112">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="c2d33-112">Next steps</span></span>

<span data-ttu-id="c2d33-113">Per un controllo introduttivo, [eseguire il rendering di una scheda](render-a-card.md) per i passaggi successivi.</span><span class="sxs-lookup"><span data-stu-id="c2d33-113">For a quick start check [Render a card](render-a-card.md) for the next steps!</span></span>

<span data-ttu-id="c2d33-114">Per una visualizzazione più approfondita delle classi associate alla libreria renderer Novell. Android, è possibile verificare alcune delle classi associate facendo clic su di esse sotto:</span><span class="sxs-lookup"><span data-stu-id="c2d33-114">For a more in depth view of the classes that have been binded for the Xamarin.Android renderer library, you can check some of the binded classes by clicking on them below:</span></span>
* [```AdaptiveCard```](adaptivecards-rendering-xamarin-android-objectmodel-adaptivecard.md)
* [```AdaptiveCardRenderer```](adaptivecards-rendering-xamarin-android-renderer-adaptivecardrenderer.md)
* [```CardRendererRegistration```](adaptivecards-rendering-xamarin-android-renderer-cardrendererregistration.md)
* [```FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md)
* [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md)
* [```RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md)