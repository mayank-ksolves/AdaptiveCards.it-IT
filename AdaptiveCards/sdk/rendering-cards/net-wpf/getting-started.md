---
title: SDK WPF .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: a3f63fc812c97014af06dd1a197b24c5d07361c2
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553623"
---
# <a name="getting-started---net-wpf"></a><span data-ttu-id="47edd-102">Introduzione-WPF .NET</span><span class="sxs-lookup"><span data-stu-id="47edd-102">Getting started - .NET WPF</span></span>

<span data-ttu-id="47edd-103">Come descritto in [Introduzione](../../../authoring-cards/getting-started.md) pagina, una scheda adattiva è un modello a oggetti della scheda serializzato JSON.</span><span class="sxs-lookup"><span data-stu-id="47edd-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="47edd-104">Questa libreria semplifica il rendering di tale JSON nell'interfaccia utente WPF che è possibile usare all'interno dell'app.</span><span class="sxs-lookup"><span data-stu-id="47edd-104">This library makes it easy to render that JSON into WPF UI that you can use within your app.</span></span>

## <a name="nuget-install"></a><span data-ttu-id="47edd-105">Installazione di NuGet</span><span class="sxs-lookup"><span data-stu-id="47edd-105">NuGet install</span></span>

<span data-ttu-id="47edd-106">[![Installazione di NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span><span class="sxs-lookup"><span data-stu-id="47edd-106">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Wpf
```

### <a name="xceed-enhanced-input-package"></a><span data-ttu-id="47edd-107">Pacchetto di input migliorato Xceed</span><span class="sxs-lookup"><span data-stu-id="47edd-107">Xceed enhanced input package</span></span>

<span data-ttu-id="47edd-108">Questo pacchetto facoltativo consente di migliorare i controlli di input della scheda adattivo oltre a quelli forniti da WPF.</span><span class="sxs-lookup"><span data-stu-id="47edd-108">This optional package enhances the Adaptive Card Input controls beyond what WPF provides out of the box.</span></span> <span data-ttu-id="47edd-109">Ha una dipendenza da`Extended.Wpf.Toolkit`</span><span class="sxs-lookup"><span data-stu-id="47edd-109">It has a dependency on `Extended.Wpf.Toolkit`</span></span>

<span data-ttu-id="47edd-110">[![Installazione di NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)</span><span class="sxs-lookup"><span data-stu-id="47edd-110">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Wpf.Xceed
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="47edd-111">Esempio di visualizzatore WPF</span><span class="sxs-lookup"><span data-stu-id="47edd-111">WPF Visualizer Sample</span></span>

![Screenshot del Visualizzatore](../../../resources/media/tools/wpfvisualizer.png)

<span data-ttu-id="47edd-113">L' [esempio visualizzatore WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) consente di visualizzare le schede utilizzando WPF.</span><span class="sxs-lookup"><span data-stu-id="47edd-113">The [WPF Visualizer sample](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF.</span></span>  <span data-ttu-id="47edd-114">Un `Host Config` Editor è integrato per la modifica e la visualizzazione delle impostazioni di configurazione host.</span><span class="sxs-lookup"><span data-stu-id="47edd-114">A `Host Config` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="47edd-115">Salvare queste impostazioni come JSON per usarle nel rendering nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="47edd-115">Save these settings as a JSON to use them in rendering in your application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="47edd-116">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="47edd-116">Next steps</span></span>

<span data-ttu-id="47edd-117">Per i passaggi successivi, vedi [Eseguire il rendering di una scheda](render-a-card.md).</span><span class="sxs-lookup"><span data-stu-id="47edd-117">See [Render a card](render-a-card.md) for the next steps!</span></span>
