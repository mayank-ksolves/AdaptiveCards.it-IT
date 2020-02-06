---
title: SDK di creazione di modelli
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 3a9bfcd1bf8f87959a747997e04f5c5ad2a79980
ms.sourcegitcommit: 90afb3729931b0e4cae19b17ef9e49453c2d2bf6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163617"
---
# <a name="adaptive-card-templating-sdks"></a><span data-ttu-id="003dc-102">SDK per la creazione di modelli di schede adattive</span><span class="sxs-lookup"><span data-stu-id="003dc-102">Adaptive Card Templating SDKs</span></span>

<span data-ttu-id="003dc-103">Gli SDK per la creazione di modelli di schede adattive consentono di popolare con facilità un [modello di scheda](language.md) con dati reali su qualsiasi piattaforma supportata.</span><span class="sxs-lookup"><span data-stu-id="003dc-103">The Adaptive Card Templating SDKs make it easy to populate a [card template](language.md) with real data on any supported platform.</span></span>

> <span data-ttu-id="003dc-104">Per una [panoramica della creazione di modelli di schede adattive](index.md), leggi l'argomento specifico.</span><span class="sxs-lookup"><span data-stu-id="003dc-104">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="003dc-105">Queste funzionalità sono disponibili **in anteprima e sono soggette a modifiche**.</span><span class="sxs-lookup"><span data-stu-id="003dc-105">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="003dc-106">Il tuo feedback non solo è apprezzato, ma è anche fondamentale per aiutarci a offrire le funzionalità di cui **tu** hai bisogno.</span><span class="sxs-lookup"><span data-stu-id="003dc-106">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>
> 
> <span data-ttu-id="003dc-107">Durante l'anteprima iniziale è disponibile solo JavaScript SDK, ma a breve dovrebbe arrivare anche .NET SKD.</span><span class="sxs-lookup"><span data-stu-id="003dc-107">During the initial preview only the JavaScript SDK is available, but a .NET SDK should arrive shortly.</span></span>

## <a name="javascript"></a><span data-ttu-id="003dc-108">JavaScript</span><span class="sxs-lookup"><span data-stu-id="003dc-108">JavaScript</span></span>

<span data-ttu-id="003dc-109">La libreria [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) è disponibile in npm e tramite CDN.</span><span class="sxs-lookup"><span data-stu-id="003dc-109">The [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) library is available on npm and via CDN.</span></span> <span data-ttu-id="003dc-110">Per la documentazione completa, vedi il collegamento al pacchetto.</span><span class="sxs-lookup"><span data-stu-id="003dc-110">See the package link for full documentation.</span></span>

### <a name="npm"></a><span data-ttu-id="003dc-111">npm</span><span class="sxs-lookup"><span data-stu-id="003dc-111">npm</span></span>

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a><span data-ttu-id="003dc-112">CDN</span><span class="sxs-lookup"><span data-stu-id="003dc-112">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 

### <a name="usage"></a><span data-ttu-id="003dc-113">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="003dc-113">Usage</span></span>

<span data-ttu-id="003dc-114">Nell'esempio seguente si presuppone che tu abbia installato anche la libreria [adaptivecards](https://www.npmjs.com/package/adaptivecards) per eseguire il rendering della scheda.</span><span class="sxs-lookup"><span data-stu-id="003dc-114">The sample below assumes you've also installed the [adaptivecards](https://www.npmjs.com/package/adaptivecards) library in order to render the card.</span></span> 

<span data-ttu-id="003dc-115">Se non prevedi di eseguire il rendering della scheda, puoi rimuovere il codice relativo a `parse` e `render`.</span><span class="sxs-lookup"><span data-stu-id="003dc-115">If you don't plan on rendering the card then you can remove the `parse` and `render` code.</span></span> 

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

## <a name="net"></a><span data-ttu-id="003dc-116">.NET</span><span class="sxs-lookup"><span data-stu-id="003dc-116">.NET</span></span> 

```console
dotnet add package AdaptiveCards.Templating --version 0.1.0-alpha1
```

> [!NOTE]
>
> <span data-ttu-id="003dc-117">Prova a sostituire la versione indicata in precedenza con l'ultima versione pubblicata.</span><span class="sxs-lookup"><span data-stu-id="003dc-117">Consider changing the version above to the latest published version</span></span>

<span data-ttu-id="003dc-118">Importa la libreria.</span><span class="sxs-lookup"><span data-stu-id="003dc-118">Import the library</span></span> 

```cs
using AdaptiveCards.Templating
```

<span data-ttu-id="003dc-119">Usa il motore per la creazione di modelli passando il codice JSON del modello e dei dati.</span><span class="sxs-lookup"><span data-stu-id="003dc-119">Use the templating engine by passing in your template JSON and data JSON.</span></span>

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
