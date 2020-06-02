---
title: Linguaggio del modello di Schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 05/18/2020
ms.topic: article
ms.openlocfilehash: 1b5a7df25eedb96ec6edfe02912d328ab59d2801
ms.sourcegitcommit: c921a7bb15a95c0ceb803ad375501ee3b8bef028
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2020
ms.locfileid: "83631342"
---
# <a name="adaptive-cards-template-language"></a><span data-ttu-id="bf2fa-102">Linguaggio del modello di Schede adattive</span><span class="sxs-lookup"><span data-stu-id="bf2fa-102">Adaptive Cards Template Language</span></span>

<span data-ttu-id="bf2fa-103">La creazione di modelli consente di separare i **dati** dal **layout** nella scheda adattiva.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-103">Templating enables the separation of **data** from **layout** in your Adaptive Card.</span></span> <span data-ttu-id="bf2fa-104">Il linguaggio del modello è la sintassi usata per creare un modello.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-104">The template langauge is the syntax used to author a template.</span></span> 

> <span data-ttu-id="bf2fa-105">Per una [panoramica della creazione di modelli di schede adattive](index.md), leggi l'argomento specifico.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="bf2fa-106">**Modifiche importanti** apportate alla **versione finale candidata di maggio 2020**</span><span class="sxs-lookup"><span data-stu-id="bf2fa-106">**Breaking changes** in the **May 2020 Release Candidate**</span></span>
>
> <span data-ttu-id="bf2fa-107">Abbiamo lavorato intensamente per il rilascio della creazione di modelli e abbiamo finalmente raggiunto l'obiettivo.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-107">We've been hard at work getting templating released, and we're finally in the home stretch!</span></span> <span data-ttu-id="bf2fa-108">Abbiamo dovuto apportare alcune piccole modifiche importanti, man mano che ci avvicinavamo alla data del rilascio.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-108">We had to make some minor breaking changes as we close on the release.</span></span>

## <a name="breaking-changes-as-of-may-2020"></a><span data-ttu-id="bf2fa-109">Modifiche importanti della versione di maggio 2020</span><span class="sxs-lookup"><span data-stu-id="bf2fa-109">Breaking changes as of May 2020</span></span>

1. <span data-ttu-id="bf2fa-110">La sintassi di binding è cambiata da `{...}` a `${...}`.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-110">The binding syntax changed from `{...}` to `${...}`</span></span>
    * <span data-ttu-id="bf2fa-111">Ad esempio, `"text": "Hello {name}"` diventa `"text": "Hello ${name}"`</span><span class="sxs-lookup"><span data-stu-id="bf2fa-111">For Example: `"text": "Hello {name}"` becomes `"text": "Hello ${name}"`</span></span>
    
## <a name="binding-to-data"></a><span data-ttu-id="bf2fa-112">Binding ai dati</span><span class="sxs-lookup"><span data-stu-id="bf2fa-112">Binding to data</span></span>

<span data-ttu-id="bf2fa-113">La scrittura di un modello è semplice quanto la sostituzione del contenuto "non statico" della scheda con "espressioni di binding".</span><span class="sxs-lookup"><span data-stu-id="bf2fa-113">Writing a template is as simple as replacing the "non-static" content of your card with "binding expressions".</span></span>

### <a name="static-card-payload"></a><span data-ttu-id="bf2fa-114">Payload scheda statica</span><span class="sxs-lookup"><span data-stu-id="bf2fa-114">Static card payload</span></span>

```json
{
   "type": "TextBlock",
   "text": "Matt"
}
```

### <a name="template-payload"></a><span data-ttu-id="bf2fa-115">Payload modello</span><span class="sxs-lookup"><span data-stu-id="bf2fa-115">Template payload</span></span>

```json
{
   "type": "TextBlock",
   "text": "${firstName}"
}
```

* <span data-ttu-id="bf2fa-116">Le espressioni di binding possono essere posizionate in qualsiasi punto in cui è presente contenuto statico</span><span class="sxs-lookup"><span data-stu-id="bf2fa-116">Binding expressions can be placed just about anywhere that static content can be</span></span>
* <span data-ttu-id="bf2fa-117">La sintassi di binding inizia con `${` e termina con `}`,</span><span class="sxs-lookup"><span data-stu-id="bf2fa-117">The binding syntax starts with `${` and ends with `}`.</span></span> <span data-ttu-id="bf2fa-118">ad esempio `${myProperty}`</span><span class="sxs-lookup"><span data-stu-id="bf2fa-118">E.g., `${myProperty}`</span></span>
* <span data-ttu-id="bf2fa-119">Usa *Notazione Dot* per accedere agli oggetti secondari di una gerarchia di oggetti,</span><span class="sxs-lookup"><span data-stu-id="bf2fa-119">Use *Dot-notation* to access sub-objects of an object hierarchy.</span></span> <span data-ttu-id="bf2fa-120">ad esempio `${myParent.myChild}`</span><span class="sxs-lookup"><span data-stu-id="bf2fa-120">E.g., `${myParent.myChild}`</span></span>
* <span data-ttu-id="bf2fa-121">Una gestione regolare dei valori null garantisce che non vengano generate eccezioni se accedi a una proprietà null in un oggetto grafico</span><span class="sxs-lookup"><span data-stu-id="bf2fa-121">Graceful null handling ensures you won't get exceptions if you access a null property in an object graph</span></span>
* <span data-ttu-id="bf2fa-122">Usa la *sintassi dell'indicizzatore* per recuperare le proprietà in base alla chiave o agli elementi di una matrice,</span><span class="sxs-lookup"><span data-stu-id="bf2fa-122">Use *Indexer syntax* to retrieve properties by key or items in an array.</span></span> <span data-ttu-id="bf2fa-123">ad esempio `${myArray[0]}`</span><span class="sxs-lookup"><span data-stu-id="bf2fa-123">E.g., `${myArray[0]}`</span></span>

## <a name="providing-the-data"></a><span data-ttu-id="bf2fa-124">Specificare i dati</span><span class="sxs-lookup"><span data-stu-id="bf2fa-124">Providing the data</span></span>

<span data-ttu-id="bf2fa-125">Ora che disponi di un modello, devi specificare i dati che lo rendono completo.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-125">Now that you have a template, you'll want to provide the data that makes it complete.</span></span> <span data-ttu-id="bf2fa-126">A questo scopo, sono disponibili due opzioni:</span><span class="sxs-lookup"><span data-stu-id="bf2fa-126">You have two options to do this:</span></span>

1. <span data-ttu-id="bf2fa-127">**Opzione A: inline all'interno del payload del modello**.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-127">**Option A: Inline within the template payload**.</span></span> <span data-ttu-id="bf2fa-128">Puoi specificare i dati inline all'interno del payload del modello `AdaptiveCard`.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-128">You can provide the data inline within the `AdaptiveCard` template payload.</span></span> <span data-ttu-id="bf2fa-129">Per eseguire questa operazione, aggiungi semplicemente un attributo `$data` all'oggetto radice `AdaptiveCard`.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-129">To do so, simply add a `$data` attribute to the root `AdaptiveCard` object.</span></span>
2. <span data-ttu-id="bf2fa-130">**Opzione B: come oggetto dati separato**.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-130">**Option B: As a separate data object**.</span></span> <span data-ttu-id="bf2fa-131">Con questa opzione, puoi specificare due oggetti separati nell'[SDK per la creazione di modelli](sdk.md) in fase di esecuzione: `template` e `data`.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-131">With this option you provide two separate objects to the [Templating SDK](sdk.md) at runtime: the `template` and the `data`.</span></span> <span data-ttu-id="bf2fa-132">Si tratta dell'approccio più comune, dal momento che, in genere, si crea innanzitutto un modello e i dati dinamici vengono specificati in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-132">This will be the more common approach, since typically you will create a template and want to provide dynamic data later.</span></span>

### <a name="option-a-inline-data"></a><span data-ttu-id="bf2fa-133">Opzione A: Dati inline</span><span class="sxs-lookup"><span data-stu-id="bf2fa-133">Option A: Inline data</span></span>

```json
{
    "type": "AdaptiveCard",
    "$data": {
        "employee": {
            "name": "Matt",
            "manager": { "name": "Thomas" },
            "peers": [{
                "name": "Andrew" 
            }, { 
                "name": "Lei"
            }, { 
                "name": "Mary Anne"
            }, { 
                "name": "Adam"
            }]
        }
    },
    "body": [
        {
            "type": "TextBlock",
            "text": "Hi ${employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: ${employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: ${employee.peers[0].name}, ${employee.peers[1].name}, ${employee.peers[2].name}"
        }
    ]
}
```

### <a name="option-b-separating-the-template-from-the-data"></a><span data-ttu-id="bf2fa-134">Opzione B: Separazione del modello dai dati</span><span class="sxs-lookup"><span data-stu-id="bf2fa-134">Option B: Separating the template from the data</span></span>

<span data-ttu-id="bf2fa-135">In alternativa (e con maggiore probabilità), creerai un modello di scheda riutilizzabile senza includere i dati.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-135">Alternatively (and more likely), you'll create a re-usable card template without including the data.</span></span> <span data-ttu-id="bf2fa-136">Questo modello può essere archiviato come file e aggiunto al controllo del codice sorgente.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-136">This template could be stored as a file and added to source control.</span></span>

<span data-ttu-id="bf2fa-137">**EmployeeCardTemplate.json**</span><span class="sxs-lookup"><span data-stu-id="bf2fa-137">**EmployeeCardTemplate.json**</span></span>

```json
{
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hi ${employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: ${employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: ${employee.peers[0].name}, ${employee.peers[1].name}, ${employee.peers[2].name}"
        }
    ]
}
```

<span data-ttu-id="bf2fa-138">Puoi quindi caricarlo e fornire i dati in fase di esecuzione tramite gli [SDK per la creazione di modelli](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="bf2fa-138">Then load it up and provide the data at runtime using the [Templating SDKs](sdk.md).</span></span>

<span data-ttu-id="bf2fa-139">**Esempio di JavaScript**</span><span class="sxs-lookup"><span data-stu-id="bf2fa-139">**JavaScript example**</span></span>

<span data-ttu-id="bf2fa-140">Uso del pacchetto [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating).</span><span class="sxs-lookup"><span data-stu-id="bf2fa-140">Using the [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating) package.</span></span>

```js
var template = new ACData.Template({ 
    // EmployeeCardTemplate goes here
});

// Specify data at runtime
var card = template.expand({
    $root: {
        "employee": {
            "name": "Matt",
            "manager": { "name": "Thomas" },
            "peers": [{
                "name": "Andrew" 
            }, { 
                "name": "Lei"
            }, { 
                "name": "Mary Anne"
            }, { 
                "name": "Adam"
            }]
        }
    }
});

// Now you have an AdaptiveCard ready to render!
```

## <a name="designer-support"></a><span data-ttu-id="bf2fa-141">Supporto per Designer</span><span class="sxs-lookup"><span data-stu-id="bf2fa-141">Designer Support</span></span>

<span data-ttu-id="bf2fa-142">Adaptive Cards Designer è stato aggiornato per supportare la creazione di modelli.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-142">The Adaptive Card Designer has been updated to support templating.</span></span> 

> <span data-ttu-id="bf2fa-143">Provala all'indirizzo: **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)** .</span><span class="sxs-lookup"><span data-stu-id="bf2fa-143">Try it out at: **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**</span></span>

<span data-ttu-id="bf2fa-144">[![Immagine](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="bf2fa-144">[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span></span>

* <span data-ttu-id="bf2fa-145">**Sample Data Editor**: specifica qui i dati di esempio per visualizzare la scheda associata ai dati quando si trova in modalità di anteprima.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-145">**Sample Data Editor** - Specify sample data here to view the data-bound card when in "Preview Mode."</span></span> <span data-ttu-id="bf2fa-146">Il piccolo pulsante presente in questo riquadro consente di popolare la struttura dati dai dati di esempio esistenti.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-146">There is a small button in this pane to populate the Data Structure from the existing sample data.</span></span>
* <span data-ttu-id="bf2fa-147">**Preview Mode**: premi il pulsante della barra degli strumenti per passare dall'esperienza di modifica a quella di anteprima dei dati di esempio e viceversa.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-147">**Preview Mode** - Press the toolbar button to toggle between the edit-experience and the sample-data-preview experience</span></span>
* <span data-ttu-id="bf2fa-148">**Open Sample**: fai clic su questo pulsante per aprire vari payload di esempio.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-148">**Open Sample** - click this button to open various sample payloads</span></span>

## <a name="advanced-binding"></a><span data-ttu-id="bf2fa-149">Binding avanzato</span><span class="sxs-lookup"><span data-stu-id="bf2fa-149">Advanced binding</span></span>

### <a name="binding-scopes"></a><span data-ttu-id="bf2fa-150">Ambiti di binding</span><span class="sxs-lookup"><span data-stu-id="bf2fa-150">Binding scopes</span></span>

<span data-ttu-id="bf2fa-151">Esistono alcune parole chiave riservate per accedere a diversi ambiti di binding.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-151">There are a few reserved keywords to access various binding scopes.</span></span> 

```json
{
    "${<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating"
}
```

### <a name="assigning-a-data-context-to-elements"></a><span data-ttu-id="bf2fa-152">Assegnazione di un contesto dati agli elementi</span><span class="sxs-lookup"><span data-stu-id="bf2fa-152">Assigning a data context to elements</span></span>

<span data-ttu-id="bf2fa-153">Per assegnare un contesto dati a qualsiasi elemento, aggiungi all'elemento un attributo `$data`.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-153">To assign a "data context" to any element add a `$data` attribute to the element.</span></span>

```json
{
    "type": "Container",
    "$data": "${mySubObject}",
    "items": [
        {
            "type": "TextBlock",
            "text": "This TextBlock is now scoped directly to 'mySubObject': ${mySubObjectProperty}"
        },
        {
            "type": "TextBlock",
            "text": "To break-out and access the root data, use: ${$root}"
        }
    ]
}
```

## <a name="repeating-items-in-an-array"></a><span data-ttu-id="bf2fa-154">Ripetizione di elementi in una matrice</span><span class="sxs-lookup"><span data-stu-id="bf2fa-154">Repeating items in an array</span></span>

* <span data-ttu-id="bf2fa-155">Se la proprietà `$data` di un elemento Adaptive Card è associata a una **matrice**, l'**elemento Adaptive Card verrà ripetuto per ciascun elemento della matrice**.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-155">If an Adaptive Card element's `$data` property is bound to an **array**, then the **element itself will be repeated for each item in the array.**</span></span> 
* <span data-ttu-id="bf2fa-156">Tutte le espressioni di binding (`${myProperty}`) usate nei valori delle proprietà saranno limitate all'ambito del **singolo elemento** all'interno della matrice.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-156">Any binding expressions (`${myProperty}`) used in property values will be scoped to the **individual item** within the array.</span></span>
* <span data-ttu-id="bf2fa-157">Se è stato eseguito il binding a una matrice di stringhe, usa `${$data}` per accedere al singolo elemento stringa,</span><span class="sxs-lookup"><span data-stu-id="bf2fa-157">If binding to an array of strings, use `${$data}` to access the individual string element.</span></span> <span data-ttu-id="bf2fa-158">ad esempio `"text": "${$data}"`</span><span class="sxs-lookup"><span data-stu-id="bf2fa-158">E.g., `"text": "${$data}"`</span></span>

<span data-ttu-id="bf2fa-159">Ad esempio, l'elemento `TextBlock` seguente sarà ripetuto tre volte poiché il relativo `$data` è una matrice.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-159">For example, the `TextBlock` below will be repeated 3 times since it's `$data` is an array.</span></span> <span data-ttu-id="bf2fa-160">Si noti che la proprietà `text` è associata alla proprietà `name` di un singolo oggetto all'interno della matrice.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-160">Notice how the `text` property is bound to the `name` property of an individual object within the array.</span></span> 

```json
{
    "type": "Container",
    "items": [
        {
            "type": "TextBlock",
            "$data": [
                { "name": "Matt" }, 
                { "name": "David" }, 
                { "name": "Thomas" }
            ],
            "text": "${name}"
        }
    ]
}
```

<span data-ttu-id="bf2fa-161">**Risultato:**</span><span class="sxs-lookup"><span data-stu-id="bf2fa-161">**Resulting in:**</span></span>

```json
{
    "type": "Container",
    "items": [ 
        {
            "type": "TextBlock",
            "text": "Matt"
        },
        {
            "type": "TextBlock",
            "text": "David"
        }
        {
            "type": "TextBlock",
            "text": "Thomas"
        }
    ]
}
```

## <a name="built-in-functions"></a><span data-ttu-id="bf2fa-162">Funzioni integrate</span><span class="sxs-lookup"><span data-stu-id="bf2fa-162">Built-in functions</span></span>

<span data-ttu-id="bf2fa-163">Nessun linguaggio per la creazione di modelli è completo senza una suite completa di funzioni helper.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-163">No templating language is complete without a rich suite of helper functions.</span></span> <span data-ttu-id="bf2fa-164">La creazione di modelli di schede adattive si basa sul [linguaggio di espressioni adattive](https://aka.ms/adaptive-expressions), uno standard aperto per la dichiarazione di espressioni che possono essere valutate su molte piattaforme diverse.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-164">Adaptive Card Templating is built on top of the [Adaptive Expression Language](https://aka.ms/adaptive-expressions) (AEL), which is an open standard for declaring expressions that can be evaluated on many different platforms.</span></span> <span data-ttu-id="bf2fa-165">Si tratta di un superset appropriato di "app per la logica", quindi puoi usare una sintassi simile a quella di Power Automate e così via.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-165">And it's a proper superset of "Logic Apps", so you can use similar syntax as Power Automate, etc.</span></span>

<span data-ttu-id="bf2fa-166">**Ecco un piccolo campionamento delle funzioni predefinite.**</span><span class="sxs-lookup"><span data-stu-id="bf2fa-166">**This is just a small sampling of the built-in functions.**</span></span>

<span data-ttu-id="bf2fa-167">Vedi l'elenco completo delle [funzioni predefinite del linguaggio delle espressioni adattive](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-concept-adaptive-expressions?view=azure-bot-service-4.0).</span><span class="sxs-lookup"><span data-stu-id="bf2fa-167">Check out the full list of [Adaptive Expression Language Pre-built functions](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-concept-adaptive-expressions?view=azure-bot-service-4.0).</span></span>

### <a name="conditional-evaluation"></a><span data-ttu-id="bf2fa-168">Valutazione condizionale</span><span class="sxs-lookup"><span data-stu-id="bf2fa-168">Conditional evaluation</span></span>

* <span data-ttu-id="bf2fa-169">if(*expression*, *trueValue*, *falseValue*)</span><span class="sxs-lookup"><span data-stu-id="bf2fa-169">if(*expression*, *trueValue*, *falseValue*)</span></span>

<span data-ttu-id="bf2fa-170">**Esempio di `if`**</span><span class="sxs-lookup"><span data-stu-id="bf2fa-170">**`if` example**</span></span>

```json
{
    "type": "TextBlock",
    "color": "${if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="parsing-json"></a><span data-ttu-id="bf2fa-171">Analisi del contenuto JSON</span><span class="sxs-lookup"><span data-stu-id="bf2fa-171">Parsing JSON</span></span>

* <span data-ttu-id="bf2fa-172">json(*jsonString*) - Analizza una stringa JSON</span><span class="sxs-lookup"><span data-stu-id="bf2fa-172">json(*jsonString*) - Parse a JSON string</span></span>

<span data-ttu-id="bf2fa-173">**Esempio di `json`**</span><span class="sxs-lookup"><span data-stu-id="bf2fa-173">**`json` example**</span></span>

<span data-ttu-id="bf2fa-174">Si tratta di una risposta DevOps di Azure in cui la proprietà `message` è una stringa serializzata in JSON.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-174">This is an Azure DevOps response where the `message` property is a JSON-serialized string.</span></span> <span data-ttu-id="bf2fa-175">Per accedere ai valori all'interno della stringa, dobbiamo usare la funzione `json` nel modello.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-175">In order to access values within the string, we need to use the `json` function in our template.</span></span>

<span data-ttu-id="bf2fa-176">**Dati**</span><span class="sxs-lookup"><span data-stu-id="bf2fa-176">**Data**</span></span> 

```json
{
    "id": "1291525457129548",
    "status": 4,
    "author": "Matt Hidinger",
    "message": "{\"type\":\"Deployment\",\"buildId\":\"9542982\",\"releaseId\":\"129\",\"buildNumber\":\"20180504.3\",\"releaseName\":\"Release-104\",\"repoProvider\":\"GitHub\"}",
    "start_time": "2018-05-04T18:05:33.3087147Z",
    "end_time": "2018-05-04T18:05:33.3087147Z"
}
```

<span data-ttu-id="bf2fa-177">**Utilizzo**</span><span class="sxs-lookup"><span data-stu-id="bf2fa-177">**Usage**</span></span>

```json
{
    "type": "TextBlock",
    "text": "${json(message).releaseName}"
}
```

<span data-ttu-id="bf2fa-178">**Risultato**</span><span class="sxs-lookup"><span data-stu-id="bf2fa-178">**Resulting In**</span></span>

```json
{
    "type": "TextBlock",
    "text": "Release-104"
}
```

### <a name="custom-functions"></a><span data-ttu-id="bf2fa-179">Funzioni personalizzate</span><span class="sxs-lookup"><span data-stu-id="bf2fa-179">Custom functions</span></span>

<span data-ttu-id="bf2fa-180">Le funzioni personalizzate sono supportate tramite le API negli [SDK per la creazione di modelli](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="bf2fa-180">Custom functions are supported via APIs in the [Templating SDKs](sdk.md).</span></span> 

## <a name="conditional-layout-with-when"></a><span data-ttu-id="bf2fa-181">Layout condizionale con `$when`</span><span class="sxs-lookup"><span data-stu-id="bf2fa-181">Conditional layout with `$when`</span></span>

<span data-ttu-id="bf2fa-182">Per eliminare un intero elemento nel caso in cui venga soddisfatta una condizione, usa la proprietà `$when`.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-182">To drop an entire element if a condition is met, use the `$when` property.</span></span> <span data-ttu-id="bf2fa-183">Se il valore di `$when` risulta essere `false`, l'elemento non verrà visualizzato per l'utente.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-183">If `$when` evaluates to `false` the element will not appear to the user.</span></span>

```json
{
    "type": "AdaptiveCard",
    "$data": {
        "price": "35"
    },
    "body": [
        {
            "type": "TextBlock",
            "$when": "${price > 30}",
            "text": "This thing is pricy!",
            "color": "attention",
        },
         {
            "type": "TextBlock",
            "$when": "${price <= 30}",
            "text": "Dang, this thing is cheap!",
            "color": "good"
        }
    ]
}
```

### <a name="composing-templates"></a><span data-ttu-id="bf2fa-184">Composizione di modelli</span><span class="sxs-lookup"><span data-stu-id="bf2fa-184">Composing templates</span></span>

<span data-ttu-id="bf2fa-185">Attualmente non è disponibile alcun supporto per la composizione di parti del modello.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-185">Currently there is no support for composing template "parts" together.</span></span> <span data-ttu-id="bf2fa-186">Tuttavia, stiamo esplorando varie opzioni e ci auguriamo di condividere presto altre informazioni.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-186">But we are exploring options and hope to share more soon.</span></span> <span data-ttu-id="bf2fa-187">Si accetta qualsiasi suggerimento.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-187">Any thoughts here welcome!</span></span>

## <a name="examples"></a><span data-ttu-id="bf2fa-188">Esempi</span><span class="sxs-lookup"><span data-stu-id="bf2fa-188">Examples</span></span>

<span data-ttu-id="bf2fa-189">Accedi alla [pagina degli esempi](https://adaptivecards.io/samples) aggiornati per esplorare tutti i tipi di nuove schede basate su modelli.</span><span class="sxs-lookup"><span data-stu-id="bf2fa-189">Browse the updated [Samples page](https://adaptivecards.io/samples) to explore all sorts of new templated cards.</span></span>
