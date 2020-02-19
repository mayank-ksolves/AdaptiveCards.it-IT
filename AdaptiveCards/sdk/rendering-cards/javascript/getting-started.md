---
title: JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 29786fe5e533e67558df88f58b1330aa6646b532
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454623"
---
# <a name="getting-started---javascript"></a><span data-ttu-id="cbb52-102">Guida introduttiva-JavaScript</span><span class="sxs-lookup"><span data-stu-id="cbb52-102">Getting started - JavaScript</span></span>

<span data-ttu-id="cbb52-103">Come descritto in [Introduzione](../../../authoring-cards/getting-started.md) pagina, una scheda adattiva è un modello a oggetti della scheda serializzato JSON.</span><span class="sxs-lookup"><span data-stu-id="cbb52-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="cbb52-104">Si tratta di un SDK JavaScript per la generazione di HTML sul lato client nel browser.</span><span class="sxs-lookup"><span data-stu-id="cbb52-104">This is a JavaScript SDK for generating client-side HTML in the browser.</span></span>

## <a name="install"></a><span data-ttu-id="cbb52-105">Installazione</span><span class="sxs-lookup"><span data-stu-id="cbb52-105">Install</span></span>

### <a name="node"></a><span data-ttu-id="cbb52-106">Nodo</span><span class="sxs-lookup"><span data-stu-id="cbb52-106">Node</span></span>

<span data-ttu-id="cbb52-107">[![Installazione di NPM](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span><span class="sxs-lookup"><span data-stu-id="cbb52-107">[![npm install](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span></span>

```console
npm install adaptivecards
```

### <a name="cdn"></a><span data-ttu-id="cbb52-108">CDN</span><span class="sxs-lookup"><span data-stu-id="cbb52-108">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a><span data-ttu-id="cbb52-109">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="cbb52-109">Usage</span></span>

### <a name="import-the-module"></a><span data-ttu-id="cbb52-110">Importare il modulo</span><span class="sxs-lookup"><span data-stu-id="cbb52-110">Import the module</span></span>

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a><span data-ttu-id="cbb52-111">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="cbb52-111">Next steps</span></span>

<span data-ttu-id="cbb52-112">Per i passaggi successivi, vedi [Eseguire il rendering di una scheda](render-a-card.md).</span><span class="sxs-lookup"><span data-stu-id="cbb52-112">See [Render a card](render-a-card.md) for the next steps!</span></span>
