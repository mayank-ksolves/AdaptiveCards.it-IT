---
title: JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 4a6030dda12ab8d9a1e5c387cec63d45e84660d8
ms.sourcegitcommit: aa044167fd0b32b485ea2ce014afcf0b332bf1a2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69529839"
---
# <a name="getting-started---javascript"></a><span data-ttu-id="82fa6-102">Guida introduttiva-JavaScript</span><span class="sxs-lookup"><span data-stu-id="82fa6-102">Getting started - JavaScript</span></span>

<span data-ttu-id="82fa6-103">Come descritto in [Introduzione](../../../authoring-cards/getting-started.md) pagina, una scheda adattiva è un modello a oggetti della scheda serializzato JSON.</span><span class="sxs-lookup"><span data-stu-id="82fa6-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="82fa6-104">Si tratta di un SDK JavaScript per la generazione di HTML sul lato client nel browser.</span><span class="sxs-lookup"><span data-stu-id="82fa6-104">This is a JavaScript SDK for generating client-side HTML in the browser.</span></span>

## <a name="install"></a><span data-ttu-id="82fa6-105">Installazione</span><span class="sxs-lookup"><span data-stu-id="82fa6-105">Install</span></span>

### <a name="node"></a><span data-ttu-id="82fa6-106">Node</span><span class="sxs-lookup"><span data-stu-id="82fa6-106">Node</span></span>

<span data-ttu-id="82fa6-107">[![installazione di NPM](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span><span class="sxs-lookup"><span data-stu-id="82fa6-107">[![npm install](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span></span>

```console
npm install adaptivecards
```

### <a name="cdn"></a><span data-ttu-id="82fa6-108">RETE CDN</span><span class="sxs-lookup"><span data-stu-id="82fa6-108">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a><span data-ttu-id="82fa6-109">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="82fa6-109">Usage</span></span>

### <a name="import-the-module"></a><span data-ttu-id="82fa6-110">Importare il modulo</span><span class="sxs-lookup"><span data-stu-id="82fa6-110">Import the module</span></span>

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a><span data-ttu-id="82fa6-111">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="82fa6-111">Next steps</span></span>

<span data-ttu-id="82fa6-112">Per i passaggi successivi, vedi [Eseguire il rendering di una scheda](render-a-card.md).</span><span class="sxs-lookup"><span data-stu-id="82fa6-112">See [Render a card](render-a-card.md) for the next steps!</span></span>
