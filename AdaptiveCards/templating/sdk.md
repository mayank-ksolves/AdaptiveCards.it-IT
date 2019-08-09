---
title: SDK per modelli
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 5f60a458af99f1b88e8ee428a8f29f1849be9b62
ms.sourcegitcommit: a16f53ba10a8607deacde5c8cc78927cac58657c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68878878"
---
# <a name="adaptive-card-templating-sdks"></a>SDK per modelli di schede adattive

Gli SDK per modelli di schede adattive semplificano la compilazione di un [modello di scheda](language.md) con dati reali su qualsiasi piattaforma supportata.

> Per una [Panoramica del modello di scheda adattivo](index.md) , vedere.

> [!IMPORTANT] 
> 
> Queste funzionalità sono **in anteprima e sono soggette a modifiche**. Il feedback non è solo Benvenuto, ma è fondamentale per garantire la fornitura delle funzionalità necessarie.
> 
> Durante l'anteprima iniziale è disponibile solo JavaScript SDK, ma a breve arriverà un SDK .NET.

## <a name="javascript"></a>JavaScript

La libreria [adaptivecards-template](https://www.npmjs.com/package/adaptivecards-templating) è disponibile in NPM e tramite la rete CDN. Per la documentazione completa, vedere il collegamento al pacchetto.

### <a name="npm"></a>NPM

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a>RETE CDN

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 

### <a name="usage"></a>Uso

Nell'esempio seguente si presuppone che sia stata installata anche la libreria [adaptivecards](https://www.npmjs.com/package/adaptivecards) per eseguire il rendering della scheda. 

Se non si prevede di eseguire il rendering della scheda, è possibile `parse` rimuovere `render` il codice e. 

```js
import * as ACData from "adaptivecards-templating";
import * as AdaptiveCards from "adaptivecards";
 
// Define a template payload
var templatePayload = {
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hello {name}!"
        }
    ]
};
 
// Create a Template instamce from the template payload
var template = new ACData.Template(templatePayload);
 
// Create a data binding context, and set its $root property to the
// data object to bind the template to
var context = new ACData.EvaluationContext();
context.$root = {
    "name": "Mickey Mouse"
};
 
// "Expand" the template - this generates the final Adaptive Card,
// ready to render
var card = template.expand(context);
 
// Render the card
var adaptiveCard = new AdaptiveCards.AdaptiveCard();
adaptiveCard.parse(card);
 
var htmlElement = adaptiveCard.render();
```

## <a name="net-coming-soon"></a>.NET (*presto disponibile*)

NON FUNZIONA ANCORA: 

```console
nuget install AdaptiveCards.Templating
```
