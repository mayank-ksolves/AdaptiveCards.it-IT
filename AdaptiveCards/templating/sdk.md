---
title: SDK di creazione di modelli
author: matthidinger
ms.author: mahiding
ms.date: 05/15/2020
ms.topic: article
ms.openlocfilehash: a8db2f5ef84203187ed1b9d0fc8dd3ce63ee3569
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417574"
---
# <a name="adaptive-card-templating-sdks"></a><span data-ttu-id="8e785-102">SDK per la creazione di modelli di schede adattive</span><span class="sxs-lookup"><span data-stu-id="8e785-102">Adaptive Card Templating SDKs</span></span>

<span data-ttu-id="8e785-103">Gli SDK per la creazione di modelli di schede adattive consentono di popolare con facilità un [modello di scheda](language.md) con dati reali su qualsiasi piattaforma supportata.</span><span class="sxs-lookup"><span data-stu-id="8e785-103">The Adaptive Card Templating SDKs make it easy to populate a [card template](language.md) with real data on any supported platform.</span></span>

> <span data-ttu-id="8e785-104">Per una [panoramica della creazione di modelli di schede adattive](index.md), leggi l'argomento specifico.</span><span class="sxs-lookup"><span data-stu-id="8e785-104">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="8e785-105">**Modifiche importanti** apportate alla **versione finale candidata di maggio 2020**</span><span class="sxs-lookup"><span data-stu-id="8e785-105">**Breaking changes** in the **May 2020 Release Candidate**</span></span>
>
> <span data-ttu-id="8e785-106">Abbiamo lavorato intensamente per il rilascio della creazione di modelli e abbiamo finalmente raggiunto l'obiettivo.</span><span class="sxs-lookup"><span data-stu-id="8e785-106">We've been hard at work getting templating released, and we're finally in the home stretch!</span></span> <span data-ttu-id="8e785-107">Abbiamo dovuto apportare alcune piccole modifiche importanti, man mano che ci avvicinavamo alla data del rilascio.</span><span class="sxs-lookup"><span data-stu-id="8e785-107">We had to make some minor breaking changes as we close on the release.</span></span>

## <a name="breaking-changes-as-of-may-2020"></a><span data-ttu-id="8e785-108">Modifiche importanti della versione di maggio 2020</span><span class="sxs-lookup"><span data-stu-id="8e785-108">Breaking changes as of May 2020</span></span>

1. <span data-ttu-id="8e785-109">La sintassi di binding è cambiata da `{...}` a `${...}`.</span><span class="sxs-lookup"><span data-stu-id="8e785-109">The binding syntax changed from `{...}` to `${...}`.</span></span> 
    * <span data-ttu-id="8e785-110">Ad esempio, `"text": "Hello {name}"` diventa `"text": "Hello ${name}"`</span><span class="sxs-lookup"><span data-stu-id="8e785-110">For Example: `"text": "Hello {name}"` becomes `"text": "Hello ${name}"`</span></span>
2. <span data-ttu-id="8e785-111">L'API JavaScript non contiene più un oggetto `EvaluationContext`.</span><span class="sxs-lookup"><span data-stu-id="8e785-111">The JavaScript API no longer contains an `EvaluationContext` object.</span></span> <span data-ttu-id="8e785-112">Passa semplicemente i dati alla funzione `expand`.</span><span class="sxs-lookup"><span data-stu-id="8e785-112">Simply pass your data to the `expand` function.</span></span> <span data-ttu-id="8e785-113">Per informazioni dettagliate, vedi la [pagina dell'SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="8e785-113">Please see the [SDK page](sdk.md) for full details.</span></span>
3. <span data-ttu-id="8e785-114">L'API .NET è stata riprogettata in modo da corrispondere più strettamente all'API JavaScript.</span><span class="sxs-lookup"><span data-stu-id="8e785-114">The .NET API was redesigned to more closely match the JavaScript API.</span></span> <span data-ttu-id="8e785-115">Per informazioni dettagliate, leggi di seguito.</span><span class="sxs-lookup"><span data-stu-id="8e785-115">Please below for full details.</span></span>

## <a name="javascript"></a><span data-ttu-id="8e785-116">JavaScript</span><span class="sxs-lookup"><span data-stu-id="8e785-116">JavaScript</span></span>

<span data-ttu-id="8e785-117">La libreria [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) è disponibile in npm e tramite CDN.</span><span class="sxs-lookup"><span data-stu-id="8e785-117">The [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) library is available on npm and via CDN.</span></span> <span data-ttu-id="8e785-118">Per la documentazione completa, vedi il collegamento al pacchetto.</span><span class="sxs-lookup"><span data-stu-id="8e785-118">See the package link for full documentation.</span></span>

### <a name="npm"></a><span data-ttu-id="8e785-119">npm</span><span class="sxs-lookup"><span data-stu-id="8e785-119">npm</span></span>

<span data-ttu-id="8e785-120">[![Installazione di NPM](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)</span><span class="sxs-lookup"><span data-stu-id="8e785-120">[![npm install](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)</span></span>

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a><span data-ttu-id="8e785-121">CDN</span><span class="sxs-lookup"><span data-stu-id="8e785-121">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 


### <a name="usage"></a><span data-ttu-id="8e785-122">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="8e785-122">Usage</span></span>

<span data-ttu-id="8e785-123">Nell'esempio seguente si presuppone che tu abbia installato anche la libreria [adaptivecards](https://www.npmjs.com/package/adaptivecards) per eseguire il rendering della scheda.</span><span class="sxs-lookup"><span data-stu-id="8e785-123">The sample below assumes you've also installed the [adaptivecards](https://www.npmjs.com/package/adaptivecards) library in order to render the card.</span></span> 

<span data-ttu-id="8e785-124">Se non prevedi di eseguire il rendering della scheda, puoi rimuovere il codice relativo a `parse` e `render`.</span><span class="sxs-lookup"><span data-stu-id="8e785-124">If you don't plan on rendering the card then you can remove the `parse` and `render` code.</span></span> 

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

## <a name="net"></a><span data-ttu-id="8e785-125">.NET</span><span class="sxs-lookup"><span data-stu-id="8e785-125">.NET</span></span> 

> [!IMPORTANT] 
> 
> <span data-ttu-id="8e785-126">La versione finale candidata di .NET sarà disponibile intorno al 23 maggio.</span><span class="sxs-lookup"><span data-stu-id="8e785-126">The .NET Release Candidate will be available around 05/23.</span></span> <span data-ttu-id="8e785-127">Cerca la versione `1.0.0-RC1`.</span><span class="sxs-lookup"><span data-stu-id="8e785-127">Look for version `1.0.0-RC1`</span></span>
>

<span data-ttu-id="8e785-128">[![Installazione di Nuget](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)</span><span class="sxs-lookup"><span data-stu-id="8e785-128">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)</span></span>

```console
dotnet add package AdaptiveCards.Templating
```

### <a name="usage"></a><span data-ttu-id="8e785-129">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="8e785-129">Usage</span></span>

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

### <a name="custom-functions"></a><span data-ttu-id="8e785-130">Funzioni personalizzate</span><span class="sxs-lookup"><span data-stu-id="8e785-130">Custom Functions</span></span>

<span data-ttu-id="8e785-131">Le funzioni personalizzate possono essere aggiunte alla libreria di espressioni adattive, oltre alle funzioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="8e785-131">Custom functions can be added to Adaptive Expression Library in addition to the prebuilt functions.</span></span>

<span data-ttu-id="8e785-132">Nell'esempio seguente viene aggiunta la funzione personalizzata stringFormat, usata per formattare una stringa.</span><span class="sxs-lookup"><span data-stu-id="8e785-132">In the below example, stringFormat custom function is added, and the funtion is used to format a string.</span></span>
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

## <a name="troubleshooting"></a><span data-ttu-id="8e785-133">Risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="8e785-133">Troubleshooting</span></span>
<span data-ttu-id="8e785-134">D:</span><span class="sxs-lookup"><span data-stu-id="8e785-134">Q.</span></span> <span data-ttu-id="8e785-135">Perché mi sono imbattuto in un'eccezione di tipo AdaptiveTemplateException con chiamata a ```expand()```?</span><span class="sxs-lookup"><span data-stu-id="8e785-135">Why am I running into an AdaptiveTemplateException calling ```expand()```?</span></span>   
<span data-ttu-id="8e785-136">A.</span><span class="sxs-lookup"><span data-stu-id="8e785-136">A.</span></span> <span data-ttu-id="8e785-137">Se il messaggio di errore è simile a '\<offending item>' alla riga '\<line number>' ha un **formato non valido per la coppia '$data : '** ".</span><span class="sxs-lookup"><span data-stu-id="8e785-137">If your error message looks like '\<offending item>' at line, '\<line number>' is **malformed for '$data : ' pair**".</span></span>   
<span data-ttu-id="8e785-138">Verifica che per "$data" sia stato specificato un valore JSON valido, ad esempio numero, valore booleano, oggetto e matrice, oppure che segua la sintassi corretta per il linguaggio del modello adattivo e che la voce esista nel contesto dati al numero di riga.</span><span class="sxs-lookup"><span data-stu-id="8e785-138">Please ensure that value provided for "$data" is valid json such as number, boolean, object, and array, or follows correct syntax for Adaptive Template language,  and the entry exists in the data context at the line number.</span></span>

<span data-ttu-id="8e785-139">D:</span><span class="sxs-lookup"><span data-stu-id="8e785-139">Q.</span></span> <span data-ttu-id="8e785-140">Perché mi sono imbattuto in un'eccezione di tipo ArgumentNullException con chiamata a ```expand()```?</span><span class="sxs-lookup"><span data-stu-id="8e785-140">Why am I running into an ArgumentNullException calling ```expand()```?</span></span>   
<span data-ttu-id="8e785-141">A.</span><span class="sxs-lookup"><span data-stu-id="8e785-141">A.</span></span> <span data-ttu-id="8e785-142">Se il messaggio di errore è simile a "**Controlla se il contesto dati padre è impostato oppure immetti un valore diverso da null per** '\<offending item>' alla riga '\<line number>'".</span><span class="sxs-lookup"><span data-stu-id="8e785-142">If your error message looks like" **Check if parent data context is set, or please enter a non-null value for** '\<offending item>' at line, '\<line number>'".</span></span>   
<span data-ttu-id="8e785-143">Indica che non esiste alcun contesto dati per il data binding richiesto.</span><span class="sxs-lookup"><span data-stu-id="8e785-143">It indicates that there doesn't exist data context for the requested data binding.</span></span> <span data-ttu-id="8e785-144">Verifica che il contesto dati radice sia impostato, se esistente, e che qualsiasi contesto dati sia disponibile per il binding corrente come indicato dal numero di riga.</span><span class="sxs-lookup"><span data-stu-id="8e785-144">Please ensure that root data context is set, if exists, ensure that any data context is available for current binding as indicated by the line number.</span></span>

<span data-ttu-id="8e785-145">D:</span><span class="sxs-lookup"><span data-stu-id="8e785-145">Q.</span></span> <span data-ttu-id="8e785-146">Perché l'indicazione data/ora in formato RFC 3389, ad esempio "2017-02-14T06:08:00Z", se usata con un modello non funziona con le funzioni TIME/DATE?</span><span class="sxs-lookup"><span data-stu-id="8e785-146">Why date/time in RFC 3389 format e.g "2017-02-14T06:08:00Z" when used with template doesn't works with TIME/DATE functions?</span></span>   
<span data-ttu-id="8e785-147">A.</span><span class="sxs-lookup"><span data-stu-id="8e785-147">A.</span></span> <span data-ttu-id="8e785-148">Il pacchetto NuGet di .NET SDK versione 1.0.0-rc.0 presenta questo comportamento,</span><span class="sxs-lookup"><span data-stu-id="8e785-148">.NET sdk nuget version 1.0.0-rc.0 exhibits this behavior.</span></span> <span data-ttu-id="8e785-149">che è stato corretto nelle versioni successive.</span><span class="sxs-lookup"><span data-stu-id="8e785-149">this behavior is corrected in the subsequent releases.</span></span> <span data-ttu-id="8e785-150">Il comportamento predefinito del deserializzatore json.Net modifica la stringa del formato data/ora e viene disabilitato per le versioni successive.</span><span class="sxs-lookup"><span data-stu-id="8e785-150">json.Net deserilizer's default behavior changes date/time format string, and it's disabled for the subsequent releases.</span></span> <span data-ttu-id="8e785-151">Usare la funzione formatDateTime() per formattare la stringa data/ora con RFC 3389 come illustrato in [questo esempio](https://github.com/microsoft/AdaptiveCards/blob/db99ee07dadf317fe45e114a508e3de6e4325d0f/samples/Templates/Elements/Template.Functions.DateFunctions.json#L28). In alternativa, è possibile ignorare le funzioni TIME/DATE e usare semplicemente formatDateTime().</span><span class="sxs-lookup"><span data-stu-id="8e785-151">Please use formatDateTime() function to format the date/time string to RFC 3389 as seen in [this example](https://github.com/microsoft/AdaptiveCards/blob/db99ee07dadf317fe45e114a508e3de6e4325d0f/samples/Templates/Elements/Template.Functions.DateFunctions.json#L28), or you can bypass TIME/DATE functions, and just use formatDateTime().</span></span> <span data-ttu-id="8e785-152">Per altre informazioni su formatDateTime(), visitare [qui](https://docs.microsoft.com/azure/bot-service/adaptive-expressions/adaptive-expressions-prebuilt-functions?view=azure-bot-service-4.0#date-and-time-functions).</span><span class="sxs-lookup"><span data-stu-id="8e785-152">For more information on formatDateTime(), please go [here](https://docs.microsoft.com/azure/bot-service/adaptive-expressions/adaptive-expressions-prebuilt-functions?view=azure-bot-service-4.0#date-and-time-functions).</span></span>
