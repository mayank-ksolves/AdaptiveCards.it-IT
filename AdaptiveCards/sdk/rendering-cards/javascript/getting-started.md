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
# <a name="getting-started---javascript"></a>Guida introduttiva-JavaScript

Come descritto in [Introduzione](../../../authoring-cards/getting-started.md) pagina, una scheda adattiva è un modello a oggetti della scheda serializzato JSON. Si tratta di un SDK JavaScript per la generazione di HTML sul lato client nel browser.

## <a name="install"></a>Installazione

### <a name="node"></a>Node

[![installazione di NPM](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)

```console
npm install adaptivecards
```

### <a name="cdn"></a>RETE CDN

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a>Utilizzo

### <a name="import-the-module"></a>Importare il modulo

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a>Passaggi successivi

Per i passaggi successivi, vedi [Eseguire il rendering di una scheda](render-a-card.md).
