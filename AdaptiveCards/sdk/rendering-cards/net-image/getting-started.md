---
title: SDK per il rendering di immagini .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: bf97d851b954b861b01b1f7ff8ce79dc9ec6413b
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454394"
---
# <a name="getting-started---net-image"></a><span data-ttu-id="e3753-102">Guida introduttiva-immagine .NET</span><span class="sxs-lookup"><span data-stu-id="e3753-102">Getting started - .NET Image</span></span>

<span data-ttu-id="e3753-103">Come descritto in [Introduzione](../../../authoring-cards/getting-started.md) pagina, una scheda adattiva è un modello a oggetti della scheda serializzato JSON.</span><span class="sxs-lookup"><span data-stu-id="e3753-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="e3753-104">Questa libreria semplifica il rendering di tale JSON in un'immagine PNG.</span><span class="sxs-lookup"><span data-stu-id="e3753-104">This library makes it easy to render that JSON into into a PNG image.</span></span>

<span data-ttu-id="e3753-105">Questo pacchetto può essere usato anche in un server per generare immagini e implementa tutto il "thread STA Magic" per l'utente.</span><span class="sxs-lookup"><span data-stu-id="e3753-105">This package can even be used on a server to generate images, and implements all the "magic STA thread" goo for you.</span></span> 

## <a name="nuget-install"></a><span data-ttu-id="e3753-106">Installazione di NuGet</span><span class="sxs-lookup"><span data-stu-id="e3753-106">NuGet install</span></span>

<span data-ttu-id="e3753-107">[![Installazione di Nuget](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span><span class="sxs-lookup"><span data-stu-id="e3753-107">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Wpf -IncludePrerelease
```

## <a name="next-steps"></a><span data-ttu-id="e3753-108">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="e3753-108">Next steps</span></span>

<span data-ttu-id="e3753-109">Per i passaggi successivi, vedi [Eseguire il rendering di una scheda](render-a-card.md).</span><span class="sxs-lookup"><span data-stu-id="e3753-109">See [Render a card](render-a-card.md) for the next steps!</span></span>