---
title: .NET WPF SDK
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
# <a name="getting-started---net-wpf"></a><span data-ttu-id="7fbac-102">Getting started - WPF .NET</span><span class="sxs-lookup"><span data-stu-id="7fbac-102">Getting started - .NET WPF</span></span>

<span data-ttu-id="7fbac-103">Come descritto [introduttiva](../../../authoring-cards/getting-started.md) pagina, una scheda adattiva è un modello a oggetti serializzati con JSON smart card.</span><span class="sxs-lookup"><span data-stu-id="7fbac-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="7fbac-104">Questa libreria semplifica eseguire il rendering di tale codice JSON nella UI WPF che è possibile usare all'interno dell'app.</span><span class="sxs-lookup"><span data-stu-id="7fbac-104">This library makes it easy to render that JSON into WPF UI that you can use within your app.</span></span>

## <a name="nuget-install"></a><span data-ttu-id="7fbac-105">Installazione di NuGet</span><span class="sxs-lookup"><span data-stu-id="7fbac-105">NuGet install</span></span>

<span data-ttu-id="7fbac-106">[![Installazione di NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span><span class="sxs-lookup"><span data-stu-id="7fbac-106">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Wpf
```

### <a name="xceed-enhanced-input-package"></a><span data-ttu-id="7fbac-107">Pacchetto di input migliorato di Xceed</span><span class="sxs-lookup"><span data-stu-id="7fbac-107">Xceed enhanced input package</span></span>

<span data-ttu-id="7fbac-108">Questo pacchetto facoltativo consente di migliorare i controlli adattivi scheda Input oltre offerte da WPF predefiniti.</span><span class="sxs-lookup"><span data-stu-id="7fbac-108">This optional package enhances the Adaptive Card Input controls beyond what WPF provides out of the box.</span></span> <span data-ttu-id="7fbac-109">E presenta una dipendenza `Extended.Wpf.Toolkit`</span><span class="sxs-lookup"><span data-stu-id="7fbac-109">It has a dependency on `Extended.Wpf.Toolkit`</span></span>

<span data-ttu-id="7fbac-110">[![Installazione di NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)</span><span class="sxs-lookup"><span data-stu-id="7fbac-110">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Wpf.Xceed
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="7fbac-111">Esempio di Visualizzatore WPF</span><span class="sxs-lookup"><span data-stu-id="7fbac-111">WPF Visualizer Sample</span></span>

![Schermata di Visualizzatore](../../../resources/media/tools/wpfvisualizer.png)

<span data-ttu-id="7fbac-113">Il [esempio di Visualizzatore WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) consente di visualizzare le schede con WPF.</span><span class="sxs-lookup"><span data-stu-id="7fbac-113">The [WPF Visualizer sample](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF.</span></span>  <span data-ttu-id="7fbac-114">Oggetto `Host Config` editor è disponibile per la modifica e la visualizzazione delle impostazioni di configurazione host.</span><span class="sxs-lookup"><span data-stu-id="7fbac-114">A `Host Config` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="7fbac-115">Salvare queste impostazioni in un formato JSON per utilizzarle nel rendering nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="7fbac-115">Save these settings as a JSON to use them in rendering in your application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7fbac-116">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="7fbac-116">Next steps</span></span>

<span data-ttu-id="7fbac-117">Visualizzare [eseguire il rendering di una scheda](render-a-card.md) per i passaggi successivi.</span><span class="sxs-lookup"><span data-stu-id="7fbac-117">See [Render a card](render-a-card.md) for the next steps!</span></span>
