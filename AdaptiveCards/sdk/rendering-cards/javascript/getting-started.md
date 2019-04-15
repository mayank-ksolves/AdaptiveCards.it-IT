---
title: JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 9684b96bba5168a1f07549468274ce5d74c01820
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553463"
---
# <a name="getting-started---javascript"></a><span data-ttu-id="7a691-102">Getting started - JavaScript</span><span class="sxs-lookup"><span data-stu-id="7a691-102">Getting started - JavaScript</span></span>

<span data-ttu-id="7a691-103">Come descritto [introduttiva](../../../authoring-cards/getting-started.md) pagina, una scheda adattiva è un modello a oggetti serializzati con JSON smart card.</span><span class="sxs-lookup"><span data-stu-id="7a691-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="7a691-104">Si tratta di una versione di SDK JavaScript per la generazione lato client HTML nel browser.</span><span class="sxs-lookup"><span data-stu-id="7a691-104">This is a JavaScript SDK for generating client-side HTML in the browser.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7a691-105">**Modifiche di rilievo rispetto versione 0.5**</span><span class="sxs-lookup"><span data-stu-id="7a691-105">**Breaking changes from v0.5**</span></span>
> 
> 1. <span data-ttu-id="7a691-106">Pacchetto rinominato da `microsoft-adaptivecards` a `adaptivecards`</span><span class="sxs-lookup"><span data-stu-id="7a691-106">Package renamed from `microsoft-adaptivecards` to `adaptivecards`</span></span>
> 1. <span data-ttu-id="7a691-107">Il metodo statico `AdaptiveCards.setHostConfig()` sono state spostate in un membro di istanza `AdaptiveCard`.</span><span class="sxs-lookup"><span data-stu-id="7a691-107">The static `AdaptiveCards.setHostConfig()` has been moved to an instance member of `AdaptiveCard`.</span></span> <span data-ttu-id="7a691-108">E.g., `myCard.hostConfig = {}`</span><span class="sxs-lookup"><span data-stu-id="7a691-108">E.g., `myCard.hostConfig = {}`</span></span> 
> 1. <span data-ttu-id="7a691-109">`HostConfig` è andato anche se diversi ridenominazione e spostamento.</span><span class="sxs-lookup"><span data-stu-id="7a691-109">`HostConfig` has gone though various renames and moves.</span></span> <span data-ttu-id="7a691-110">Vedere le [Sample. JSON](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) configurazione Host per la struttura corrente</span><span class="sxs-lookup"><span data-stu-id="7a691-110">See the [sample.json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) Host Config for current structure</span></span>
> 1. <span data-ttu-id="7a691-111">Sono state apportate anche alcune modifiche dello schema dalla versione di anteprima versione 0.5, ovvero [descritti qui](https://github.com/Microsoft/AdaptiveCards/pull/633)</span><span class="sxs-lookup"><span data-stu-id="7a691-111">There have also been some schema changes from the v0.5 preview, which are [outlined here](https://github.com/Microsoft/AdaptiveCards/pull/633)</span></span>
> 1. <span data-ttu-id="7a691-112">Il metodo statico `renderCard()` funzione è stata rimossa quanto ridondante con i metodi della classe.</span><span class="sxs-lookup"><span data-stu-id="7a691-112">The static `renderCard()` function was removed as it was redundant with the class methods.</span></span> <span data-ttu-id="7a691-113">Usare `adaptiveCard.render()` come descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="7a691-113">Use `adaptiveCard.render()` as described below.</span></span> 


## <a name="install"></a><span data-ttu-id="7a691-114">Installazione</span><span class="sxs-lookup"><span data-stu-id="7a691-114">Install</span></span>

### <a name="node"></a><span data-ttu-id="7a691-115">Node</span><span class="sxs-lookup"><span data-stu-id="7a691-115">Node</span></span>

<span data-ttu-id="7a691-116">[![installazione di npm](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span><span class="sxs-lookup"><span data-stu-id="7a691-116">[![npm install](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span></span>

```console
npm install adaptivecards --save
```

### <a name="cdn"></a><span data-ttu-id="7a691-117">CDN</span><span class="sxs-lookup"><span data-stu-id="7a691-117">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a><span data-ttu-id="7a691-118">Uso</span><span class="sxs-lookup"><span data-stu-id="7a691-118">Usage</span></span>

### <a name="import-the-module"></a><span data-ttu-id="7a691-119">Importare il modulo</span><span class="sxs-lookup"><span data-stu-id="7a691-119">Import the module</span></span>

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a><span data-ttu-id="7a691-120">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="7a691-120">Next steps</span></span>

<span data-ttu-id="7a691-121">Visualizzare [eseguire il rendering di una scheda](render-a-card.md) per i passaggi successivi.</span><span class="sxs-lookup"><span data-stu-id="7a691-121">See [Render a card](render-a-card.md) for the next steps!</span></span>
