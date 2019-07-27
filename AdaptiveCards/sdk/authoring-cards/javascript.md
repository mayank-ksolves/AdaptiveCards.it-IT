---
title: JavaScript SDK per schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 07/26/2019
ms.topic: article
ms.openlocfilehash: 039171d895fac0975bf9eff4fe84fdf8b6f7e4af
ms.sourcegitcommit: f8de9c02b92cd8927a18e59e5650c92b2b78db06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2019
ms.locfileid: "68523840"
---
# <a name="javascript-sdk-for-creating-cards"></a>JavaScript SDK per la creazione di schede

> [!IMPORTANT]
> La libreria per la serializzazione di JSON è ancora in fase di sviluppo e i chilometraggio possono variare.

Come descritto in [Introduzione](../../authoring-cards/getting-started.md), una scheda adattiva non è nient'altro che un oggetto JSON serializzato di un modello a oggetti della scheda.  Per semplificare la manipolazione del modello a oggetti sono state definite alcune librerie che definiscono una gerarchia di classi fortemente tipizzata che è facile da serializzare/deserializzare JSON.

È possibile usare qualsiasi strumento per creare il file JSON della scheda adattiva.

Il `adaptivecards` pacchetto NPM definisce una libreria per l'uso di schede adattive in JavaScript

## <a name="to-install"></a>Per installare
```console
npm install adaptivecards
```

## <a name="example"></a>Esempio

L'API seguente mostra come costruire una scheda adattiva usando il modello a oggetti e come serializzarla in JSON.

```typescript
let card = new Adaptive.AdaptiveCard();
card.version = new Adaptive.Version(1, 0);

let textBlock = new Adaptive.TextBlock();
textBlock.text = "Hello World";

card.addItem(textBlock);

let json = card.toJSON();
```
