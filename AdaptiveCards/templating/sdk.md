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
# <a name="adaptive-card-templating-sdks"></a><span data-ttu-id="074da-102">SDK per la creazione di modelli di schede adattive</span><span class="sxs-lookup"><span data-stu-id="074da-102">Adaptive Card Templating SDKs</span></span>

<span data-ttu-id="074da-103">Gli SDK per la creazione di modelli di schede adattive consentono di popolare con facilità un [modello di scheda](language.md) con dati reali su qualsiasi piattaforma supportata.</span><span class="sxs-lookup"><span data-stu-id="074da-103">The Adaptive Card Templating SDKs make it easy to populate a [card template](language.md) with real data on any supported platform.</span></span>

> <span data-ttu-id="074da-104">Per una [panoramica della creazione di modelli di schede adattive](index.md), leggi l'argomento specifico.</span><span class="sxs-lookup"><span data-stu-id="074da-104">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="074da-105">**Modifiche importanti** apportate alla **versione finale candidata di maggio 2020**</span><span class="sxs-lookup"><span data-stu-id="074da-105">**Breaking changes** in the **May 2020 Release Candidate**</span></span>
>
> <span data-ttu-id="074da-106">Abbiamo lavorato intensamente per il rilascio della creazione di modelli e abbiamo finalmente raggiunto l'obiettivo.</span><span class="sxs-lookup"><span data-stu-id="074da-106">We've been hard at work getting templating released, and we're finally in the home stretch!</span></span> <span data-ttu-id="074da-107">Abbiamo dovuto apportare alcune piccole modifiche importanti, man mano che ci avvicinavamo alla data del rilascio.</span><span class="sxs-lookup"><span data-stu-id="074da-107">We had to make some minor breaking changes as we close on the release.</span></span>

## <a name="breaking-changes-as-of-may-2020"></a><span data-ttu-id="074da-108">Modifiche importanti della versione di maggio 2020</span><span class="sxs-lookup"><span data-stu-id="074da-108">Breaking changes as of May 2020</span></span>

1. <span data-ttu-id="074da-109">La sintassi di binding è cambiata da `{...}` a `${...}`.</span><span class="sxs-lookup"><span data-stu-id="074da-109">The binding syntax changed from `{...}` to `${...}`.</span></span> 
    * <span data-ttu-id="074da-110">Ad esempio, `"text": "Hello {name}"` diventa `"text": "Hello ${name}"`</span><span class="sxs-lookup"><span data-stu-id="074da-110">For Example: `"text": "Hello {name}"` becomes `"text": "Hello ${name}"`</span></span>
2. <span data-ttu-id="074da-111">L'API JavaScript non contiene più un oggetto `EvaluationContext`.</span><span class="sxs-lookup"><span data-stu-id="074da-111">The JavaScript API no longer contains an `EvaluationContext` object.</span></span> <span data-ttu-id="074da-112">Passa semplicemente i dati alla funzione `expand`.</span><span class="sxs-lookup"><span data-stu-id="074da-112">Simply pass your data to the `expand` function.</span></span> <span data-ttu-id="074da-113">Per informazioni dettagliate, vedi la [pagina dell'SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="074da-113">Please see the [SDK page](sdk.md) for full details.</span></span>
3. <span data-ttu-id="074da-114">L'API .NET è stata riprogettata in modo da corrispondere più strettamente all'API JavaScript.</span><span class="sxs-lookup"><span data-stu-id="074da-114">The .NET API was redesigned to more closely match the JavaScript API.</span></span> <span data-ttu-id="074da-115">Per informazioni dettagliate, leggi di seguito.</span><span class="sxs-lookup"><span data-stu-id="074da-115">Please below for full details.</span></span>

## <a name="javascript"></a><span data-ttu-id="074da-116">JavaScript</span><span class="sxs-lookup"><span data-stu-id="074da-116">JavaScript</span></span>

<span data-ttu-id="074da-117">La libreria [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) è disponibile in npm e tramite CDN.</span><span class="sxs-lookup"><span data-stu-id="074da-117">The [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) library is available on npm and via CDN.</span></span> <span data-ttu-id="074da-118">Per la documentazione completa, vedi il collegamento al pacchetto.</span><span class="sxs-lookup"><span data-stu-id="074da-118">See the package link for full documentation.</span></span>

### <a name="npm"></a><span data-ttu-id="074da-119">npm</span><span class="sxs-lookup"><span data-stu-id="074da-119">npm</span></span>

<span data-ttu-id="074da-120">[![Installazione di NPM](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)</span><span class="sxs-lookup"><span data-stu-id="074da-120">[![npm install](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)</span></span>

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a><span data-ttu-id="074da-121">CDN</span><span class="sxs-lookup"><span data-stu-id="074da-121">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 


### <a name="usage"></a><span data-ttu-id="074da-122">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="074da-122">Usage</span></span>

<span data-ttu-id="074da-123">Nell'esempio seguente si presuppone che tu abbia installato anche la libreria [adaptivecards](https://www.npmjs.com/package/adaptivecards) per eseguire il rendering della scheda.</span><span class="sxs-lookup"><span data-stu-id="074da-123">The sample below assumes you've also installed the [adaptivecards](https://www.npmjs.com/package/adaptivecards) library in order to render the card.</span></span> 

<span data-ttu-id="074da-124">Se non prevedi di eseguire il rendering della scheda, puoi rimuovere il codice relativo a `parse` e `render`.</span><span class="sxs-lookup"><span data-stu-id="074da-124">If you don't plan on rendering the card then you can remove the `parse` and `render` code.</span></span> 

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

## <a name="net"></a><span data-ttu-id="074da-125">.NET</span><span class="sxs-lookup"><span data-stu-id="074da-125">.NET</span></span> 

> [!IMPORTANT] 
> 
> <span data-ttu-id="074da-126">La versione finale candidata di .NET sarà disponibile intorno al 23 maggio.</span><span class="sxs-lookup"><span data-stu-id="074da-126">The .NET Release Candidate will be available around 05/23.</span></span> <span data-ttu-id="074da-127">Cerca la versione `1.0.0-RC1`.</span><span class="sxs-lookup"><span data-stu-id="074da-127">Look for version `1.0.0-RC1`</span></span>
>

<span data-ttu-id="074da-128">[![Installazione di Nuget](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)</span><span class="sxs-lookup"><span data-stu-id="074da-128">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)</span></span>

```console
dotnet add package AdaptiveCards.Templating
```

### <a name="usage"></a><span data-ttu-id="074da-129">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="074da-129">Usage</span></span>

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

### <a name="custom-functions"></a><span data-ttu-id="074da-130">Funzioni personalizzate</span><span class="sxs-lookup"><span data-stu-id="074da-130">Custom Functions</span></span>

<span data-ttu-id="074da-131">Le funzioni personalizzate possono essere aggiunte alla libreria di espressioni adattive, oltre alle funzioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="074da-131">Custom functions can be added to Adaptive Expression Library in addition to the prebuilt functions.</span></span>

<span data-ttu-id="074da-132">Nell'esempio seguente viene aggiunta la funzione personalizzata stringFormat, usata per formattare una stringa.</span><span class="sxs-lookup"><span data-stu-id="074da-132">In the below example, stringFormat custom function is added, and the funtion is used to format a string.</span></span>
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

## <a name="troubleshooting"></a><span data-ttu-id="074da-133">Risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="074da-133">Troubleshooting</span></span>
<span data-ttu-id="074da-134">D:</span><span class="sxs-lookup"><span data-stu-id="074da-134">Q.</span></span> <span data-ttu-id="074da-135">Perché mi sono imbattuto in un'eccezione di tipo AdaptiveTemplateException con chiamata a ```expand()```?</span><span class="sxs-lookup"><span data-stu-id="074da-135">Why am I running into an AdaptiveTemplateException calling ```expand()```?</span></span>   
<span data-ttu-id="074da-136">A.</span><span class="sxs-lookup"><span data-stu-id="074da-136">A.</span></span> <span data-ttu-id="074da-137">Se il messaggio di errore è simile a '\<offending item>' alla riga '\<line number>' ha un **formato non valido per la coppia '$data : '** ".</span><span class="sxs-lookup"><span data-stu-id="074da-137">If your error message looks like '\<offending item>' at line, '\<line number>' is **malformed for '$data : ' pair**".</span></span>   
<span data-ttu-id="074da-138">Verifica che per "$data" sia stato specificato un valore JSON valido, ad esempio numero, valore booleano, oggetto e matrice, oppure che segua la sintassi corretta per il linguaggio del modello adattivo e che la voce esista nel contesto dati al numero di riga.</span><span class="sxs-lookup"><span data-stu-id="074da-138">Please ensure that value provided for "$data" is valid json such as number, boolean, object, and array, or follows correct syntax for Adaptive Template language,  and the entry exists in the data context at the line number.</span></span> <span data-ttu-id="074da-139">Tieni presente che ${LineItem} e '8' possono cambiare.</span><span class="sxs-lookup"><span data-stu-id="074da-139">Please note that ${LineItem} and '8' can change.</span></span>

<span data-ttu-id="074da-140">D:</span><span class="sxs-lookup"><span data-stu-id="074da-140">Q.</span></span> <span data-ttu-id="074da-141">Perché mi sono imbattuto in un'eccezione di tipo ArgumentNullException con chiamata a ```expand()```?</span><span class="sxs-lookup"><span data-stu-id="074da-141">Why am I running into an ArgumentNullException calling ```expand()```?</span></span>   
<span data-ttu-id="074da-142">A.</span><span class="sxs-lookup"><span data-stu-id="074da-142">A.</span></span> <span data-ttu-id="074da-143">Se il messaggio di errore è simile a "**Controlla se il contesto dati padre è impostato oppure immetti un valore diverso da null per** '\<offending item>' alla riga '\<line number>'".</span><span class="sxs-lookup"><span data-stu-id="074da-143">If your error message looks like" **Check if parent data context is set, or please enter a non-null value for** '\<offending item>' at line, '\<line number>'".</span></span>   
<span data-ttu-id="074da-144">Indica che non esiste alcun contesto dati per il data binding richiesto.</span><span class="sxs-lookup"><span data-stu-id="074da-144">It indicates that there doesn't exist data context for the requested data binding.</span></span> <span data-ttu-id="074da-145">Verifica che il contesto dati radice sia impostato, se esistente, e che qualsiasi contesto dati sia disponibile per il binding corrente come indicato dal numero di riga.</span><span class="sxs-lookup"><span data-stu-id="074da-145">Please ensure that root data context is set, if exists, ensure that any data context is available for current binding as indicated by the line number.</span></span>
