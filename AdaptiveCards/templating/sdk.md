---
title: SDK di creazione di modelli
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 3a9bfcd1bf8f87959a747997e04f5c5ad2a79980
ms.sourcegitcommit: 90afb3729931b0e4cae19b17ef9e49453c2d2bf6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163617"
---
# <a name="adaptive-card-templating-sdks"></a>SDK per modelli di schede adattive

Gli SDK per modelli di schede adattive semplificano la compilazione di un [modello di scheda](language.md) con dati reali su qualsiasi piattaforma supportata.

> Per una [Panoramica del modello di scheda adattivo](index.md) , vedere.

> [!IMPORTANT] 
> 
> Queste funzionalità sono disponibili **in anteprima e sono soggette a modifiche**. Il tuo feedback non solo è apprezzato, ma è anche fondamentale per aiutarci a offrire le funzionalità di cui **tu** hai bisogno.
> 
> Durante l'anteprima iniziale è disponibile solo JavaScript SDK, ma a breve arriverà un SDK .NET.

## <a name="javascript"></a>JavaScript

La libreria [adaptivecards-template](https://www.npmjs.com/package/adaptivecards-templating) è disponibile in NPM e tramite la rete CDN. Per la documentazione completa, vedere il collegamento al pacchetto.

### <a name="npm"></a>NPM

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a>CDN

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 

### <a name="usage"></a>Utilizzo

Nell'esempio seguente si presuppone che sia stata installata anche la libreria [adaptivecards](https://www.npmjs.com/package/adaptivecards) per eseguire il rendering della scheda. 

Se non si prevede di eseguire il rendering della scheda, è possibile rimuovere il codice `parse` e `render`. 

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

## <a name="net"></a>.NET 

```console
dotnet add package AdaptiveCards.Templating --version 0.1.0-alpha1
```

> [!NOTE]
>
> Provare a modificare la versione precedente alla versione pubblicata più recente

Importa la libreria 

```cs
using AdaptiveCards.Templating
```

Usare il motore di creazione del modello passando il modello JSON e i dati JSON.

```cs
var templateJson = @"
{
    ""type"": ""AdaptiveCard"",
    ""version"": ""1.0"",
    ""body"": [
        {
            ""type"": ""TextBlock"",
            ""text"": ""Hello {name}""
        }
    ]
}";

var dataJson = @"
{
    ""name"": ""Mickey Mouse""
}";

var transformer = new AdaptiveTransformer();
var cardJson = transformer.Transform(templateJson, dataJson);
```
