---
title: JavaScript SDK per schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 07/26/2019
ms.topic: article
ms.openlocfilehash: 4ddff841ec073c60a8aa6184f309e94052cb002d
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454804"
---
# <a name="javascript-sdk-for-creating-cards"></a>JavaScript SDK per la creazione di schede

> [!IMPORTANT]
> La libreria per la serializzazione di JSON è ancora in fase di sviluppo e i chilometraggio possono variare.

Come descritto in [Introduzione](../../authoring-cards/getting-started.md), una scheda adattiva non è nient'altro che un oggetto JSON serializzato di un modello a oggetti della scheda.  Per semplificare la manipolazione del modello a oggetti sono state definite alcune librerie che definiscono una gerarchia di classi fortemente tipizzata che è facile da serializzare/deserializzare JSON.

È possibile usare qualsiasi strumento per creare il file JSON della scheda adattiva.

Il pacchetto NPM `adaptivecards` definisce una libreria per l'uso di schede adattive in JavaScript

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
