---
title: SDK di creazione di modelli
author: matthidinger
ms.author: mahiding
ms.date: 05/15/2020
ms.topic: article
ms.openlocfilehash: d04b38d6b2a389ca31b690d3298f64b3fced7c9a
ms.sourcegitcommit: eb71aebe40a592649461e468a87993a10cbe6187
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/03/2020
ms.locfileid: "84318181"
---
# <a name="adaptive-card-templating-sdks"></a>SDK per la creazione di modelli di schede adattive

Gli SDK per la creazione di modelli di schede adattive consentono di popolare con facilità un [modello di scheda](language.md) con dati reali su qualsiasi piattaforma supportata.

> Per una [panoramica della creazione di modelli di schede adattive](index.md), leggi l'argomento specifico.

> [!IMPORTANT] 
> 
> **Modifiche importanti** apportate alla **versione finale candidata di maggio 2020**
>
> Abbiamo lavorato intensamente per il rilascio della creazione di modelli e abbiamo finalmente raggiunto l'obiettivo. Abbiamo dovuto apportare alcune piccole modifiche importanti, man mano che ci avvicinavamo alla data del rilascio.

## <a name="breaking-changes-as-of-may-2020"></a>Modifiche importanti della versione di maggio 2020

1. La sintassi di binding è cambiata da `{...}` a `${...}`. 
    * Ad esempio, `"text": "Hello {name}"` diventa `"text": "Hello ${name}"`
2. L'API JavaScript non contiene più un oggetto `EvaluationContext`. Passa semplicemente i dati alla funzione `expand`. Per informazioni dettagliate, vedi la [pagina dell'SDK](sdk.md).
3. L'API .NET è stata riprogettata in modo da corrispondere più strettamente all'API JavaScript. Per informazioni dettagliate, leggi di seguito.

## <a name="javascript"></a>JavaScript

La libreria [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) è disponibile in npm e tramite CDN. Per la documentazione completa, vedi il collegamento al pacchetto.

### <a name="npm"></a>npm

[![Installazione di NPM](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a>CDN

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 


### <a name="usage"></a>Utilizzo

Nell'esempio seguente si presuppone che tu abbia installato anche la libreria [adaptivecards](https://www.npmjs.com/package/adaptivecards) per eseguire il rendering della scheda. 

Se non prevedi di eseguire il rendering della scheda, puoi rimuovere il codice relativo a `parse` e `render`. 

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
            "text": "Hello ${name}!"
        }
    ]
};
 
// Create a Template instance from the template payload
var template = new ACData.Template(templatePayload);
 
// Expand the template with your `$root` data object.
// This binds it to the data and produces the final Adaptive Card payload
var cardPayload = template.expand({
   $root: {
      name: "Matt Hidinger"
   }
});
 
// OPTIONAL: Render the card (requires that the adaptivecards library be loaded)
var adaptiveCard = new AdaptiveCards.AdaptiveCard();
adaptiveCard.parse(cardPayload);
document.getElementById('exampleDiv').appendChild(adaptiveCard.render());
```

## <a name="net"></a>.NET 

> [!IMPORTANT] 
> 
> La versione finale candidata di .NET sarà disponibile intorno al 23 maggio. Cerca la versione `1.0.0-RC1`.
>

[![Installazione di Nuget](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)

```console
dotnet add package AdaptiveCards.Templating
```

### <a name="usage"></a>Utilizzo

```cs
// Import the library 
using AdaptiveCards.Templating;
```

```cs
var templateJson = @"
{
    ""type"": ""AdaptiveCard"",
    ""version"": ""1.2"",
    ""body"": [
        {
            ""type"": ""TextBlock"",
            ""text"": ""Hello ${name}!""
        }
    ]
}";

// Create a Template instance from the template payload
AdaptiveCardTemplate template = new AdaptiveCardTemplate(templateJson);

// You can use any serializable object as your data
var myData = new
{
    Name = "Matt Hidinger"
};

// "Expand" the template - this generates the final Adaptive Card payload
string cardJson = template.Expand(myData);
```

### <a name="custom-functions"></a>Funzioni personalizzate

Le funzioni personalizzate possono essere aggiunte alla libreria di espressioni adattive, oltre alle funzioni predefinite.

Nell'esempio seguente viene aggiunta la funzione personalizzata stringFormat, usata per formattare una stringa.
```cs
string jsonTemplate = @"{
    ""type"": ""AdaptiveCard"",
    ""version"": ""1.0"",
    ""body"": [{
        ""type"": ""TextBlock"",
        ""text"": ""${stringFormat(strings.myName, person.firstName, person.lastName)}""
    }]
}";

string jsonData = @"{
    ""strings"": {
        ""myName"": ""My name is {0} {1}""
    },
    ""person"": {
        ""firstName"": ""Andrew"",
        ""lastName"": ""Leader""
    }
}";

AdaptiveCardTemplate template = new AdaptiveCardTemplate(jsonTemplate);

var context = new EvaluationContext
{
    Root = jsonData
};

// a custom function is added
AdaptiveExpressions.Expression.Functions.Add("stringFormat", (args) =>
{
    string formattedString = "";

    // argument is packed in sequential order as defined in the template
    // For example, suppose we have "${stringFormat(strings.myName, person.firstName, person.lastName)}"
    // args will have following entries
    // args[0]: strings.myName
    // args[1]: person.firstName
    // args[2]: strings.lastName
    if (args[0] != null && args[1] != null && args[2] != null) 
    {
        string formatString = args[0];
        string[] stringArguments = {args[1], args[2] };
        formattedString = string.Format(formatString, stringArguments);
    }
    return formattedString;
});

string cardJson = template.Expand(context);
```

## <a name="troubleshooting"></a>Risoluzione dei problemi
D: Perché mi sono imbattuto in un'eccezione di tipo AdaptiveTemplateException con chiamata a ```expand()```?   
A. Se il messaggio di errore è simile a '\<offending item>' alla riga '\<line number>' ha un **formato non valido per la coppia '$data : '** ".   
Verifica che per "$data" sia stato specificato un valore JSON valido, ad esempio numero, valore booleano, oggetto e matrice, oppure che segua la sintassi corretta per il linguaggio del modello adattivo e che la voce esista nel contesto dati al numero di riga. Tieni presente che ${LineItem} e '8' possono cambiare.

D: Perché mi sono imbattuto in un'eccezione di tipo ArgumentNullException con chiamata a ```expand()```?   
A. Se il messaggio di errore è simile a "**Controlla se il contesto dati padre è impostato oppure immetti un valore diverso da null per** '\<offending item>' alla riga '\<line number>'".   
Indica che non esiste alcun contesto dati per il data binding richiesto. Verifica che il contesto dati radice sia impostato, se esistente, e che qualsiasi contesto dati sia disponibile per il binding corrente come indicato dal numero di riga.
