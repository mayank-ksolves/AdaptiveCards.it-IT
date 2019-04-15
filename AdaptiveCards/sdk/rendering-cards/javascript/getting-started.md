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
# <a name="getting-started---javascript"></a>Getting started - JavaScript

Come descritto [introduttiva](../../../authoring-cards/getting-started.md) pagina, una scheda adattiva è un modello a oggetti serializzati con JSON smart card. Si tratta di una versione di SDK JavaScript per la generazione lato client HTML nel browser.

> [!IMPORTANT]
> **Modifiche di rilievo rispetto versione 0.5**
> 
> 1. Pacchetto rinominato da `microsoft-adaptivecards` a `adaptivecards`
> 1. Il metodo statico `AdaptiveCards.setHostConfig()` sono state spostate in un membro di istanza `AdaptiveCard`. E.g., `myCard.hostConfig = {}` 
> 1. `HostConfig` è andato anche se diversi ridenominazione e spostamento. Vedere le [Sample. JSON](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) configurazione Host per la struttura corrente
> 1. Sono state apportate anche alcune modifiche dello schema dalla versione di anteprima versione 0.5, ovvero [descritti qui](https://github.com/Microsoft/AdaptiveCards/pull/633)
> 1. Il metodo statico `renderCard()` funzione è stata rimossa quanto ridondante con i metodi della classe. Usare `adaptiveCard.render()` come descritto di seguito. 


## <a name="install"></a>Installazione

### <a name="node"></a>Node

[![installazione di npm](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)

```console
npm install adaptivecards --save
```

### <a name="cdn"></a>CDN

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a>Uso

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

Visualizzare [eseguire il rendering di una scheda](render-a-card.md) per i passaggi successivi.
