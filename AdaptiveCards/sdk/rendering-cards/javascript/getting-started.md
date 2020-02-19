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
# <a name="getting-started---javascript"></a>Guida introduttiva-JavaScript

Come descritto in [Introduzione](../../../authoring-cards/getting-started.md) pagina, una scheda adattiva è un modello a oggetti della scheda serializzato JSON. Si tratta di un SDK JavaScript per la generazione di HTML sul lato client nel browser.

## <a name="install"></a>Installazione

### <a name="node"></a>Nodo

[![Installazione di NPM](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)

```console
npm install adaptivecards
```

### <a name="cdn"></a>CDN

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
