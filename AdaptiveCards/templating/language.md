---
title: Linguaggio del modello di Schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: ffd2ec065550f483bf602483eebf622565f7f47a
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2020
ms.locfileid: "82136177"
---
# <a name="adaptive-cards-template-language"></a><span data-ttu-id="3ef83-102">Linguaggio del modello di Schede adattive</span><span class="sxs-lookup"><span data-stu-id="3ef83-102">Adaptive Cards Template Language</span></span>

<span data-ttu-id="3ef83-103">La creazione di modelli consente di separare i **dati** dal **layout** nella scheda adattiva.</span><span class="sxs-lookup"><span data-stu-id="3ef83-103">Templating enables the separation of **data** from **layout** in your Adaptive Card.</span></span> <span data-ttu-id="3ef83-104">Il linguaggio del modello è la sintassi usata per creare un modello.</span><span class="sxs-lookup"><span data-stu-id="3ef83-104">The template langauge is the syntax used to author a template.</span></span> 

> <span data-ttu-id="3ef83-105">Per una [panoramica della creazione di modelli di schede adattive](index.md), leggi l'argomento specifico.</span><span class="sxs-lookup"><span data-stu-id="3ef83-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="3ef83-106">Queste funzionalità sono disponibili **in anteprima e sono soggette a modifiche**.</span><span class="sxs-lookup"><span data-stu-id="3ef83-106">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="3ef83-107">Il tuo feedback non solo è apprezzato, ma è anche fondamentale per aiutarci a offrire le funzionalità di cui **tu** hai bisogno.</span><span class="sxs-lookup"><span data-stu-id="3ef83-107">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

<span data-ttu-id="3ef83-108">Quando crei un modello, puoi specificare i dati inline con il payload di `AdaptiveCard` oppure in fase di esecuzione usando gli [SDK per la creazione di modelli](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="3ef83-108">When authoring a template you can specify the data inline with the `AdaptiveCard` payload, or at runtime using the [Templating SDKs](sdk.md).</span></span>

## <a name="specify-data-within-the-card"></a><span data-ttu-id="3ef83-109">Specificare dati all'interno della scheda</span><span class="sxs-lookup"><span data-stu-id="3ef83-109">Specify data within the card</span></span>

<span data-ttu-id="3ef83-110">Per fornire i dati direttamente all'interno del payload della scheda, aggiungi semplicemente un attributo `$data` ad `AdaptiveCard` (vedi più avanti).</span><span class="sxs-lookup"><span data-stu-id="3ef83-110">To provide data directly within the card payload, simply add a `$data` attribute to your `AdaptiveCard` (seen below).</span></span>

## <a name="binding-to-the-data"></a><span data-ttu-id="3ef83-111">Binding ai dati</span><span class="sxs-lookup"><span data-stu-id="3ef83-111">Binding to the data</span></span>

<span data-ttu-id="3ef83-112">Puoi eseguire il binding ai dati all'interno di `body` o `actions` della scheda.</span><span class="sxs-lookup"><span data-stu-id="3ef83-112">You can bind to the data within the `body` or `actions` of the card.</span></span>

* <span data-ttu-id="3ef83-113">La sintassi di binding inizia con `{` e termina con `}`,</span><span class="sxs-lookup"><span data-stu-id="3ef83-113">Binding syntax starts with `{` and ends with `}`.</span></span> <span data-ttu-id="3ef83-114">ad esempio `{myProperty}`</span><span class="sxs-lookup"><span data-stu-id="3ef83-114">E.g., `{myProperty}`</span></span>
* <span data-ttu-id="3ef83-115">Notazione Dot per accedere ai sotto-oggetti</span><span class="sxs-lookup"><span data-stu-id="3ef83-115">Dot-notation to access sub-objects</span></span>
* <span data-ttu-id="3ef83-116">Sintassi dell'indicizzatore per recuperare le proprietà in base alla chiave o agli elementi di una matrice</span><span class="sxs-lookup"><span data-stu-id="3ef83-116">Indexer syntax to retrieve properties by key or items in an array</span></span>
* <span data-ttu-id="3ef83-117">Gestione automatica dei valori null per le gerarchie profonde</span><span class="sxs-lookup"><span data-stu-id="3ef83-117">Graceful null handling for deep hierarchies</span></span>
* <span data-ttu-id="3ef83-118">*Documentazione relativa alla sintassi di escape presto disponibile*</span><span class="sxs-lookup"><span data-stu-id="3ef83-118">*Escape syntax documentation to come soon*</span></span>

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
            "text": "Hi {employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: {employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: {employee.peers[0].name}, {employee.peers[1].name}, {employee.peers[2].name}"
        }
    ]
}
```

## <a name="separating-the-template-from-the-data"></a><span data-ttu-id="3ef83-119">Separazione del modello dai dati</span><span class="sxs-lookup"><span data-stu-id="3ef83-119">Separating the template from the data</span></span>

<span data-ttu-id="3ef83-120">In alternativa (e con maggiore probabilità), creerai un modello di scheda riutilizzabile senza includere i dati.</span><span class="sxs-lookup"><span data-stu-id="3ef83-120">Alternatively (and more likely), you will create a re-usable card "template" without including the data.</span></span> <span data-ttu-id="3ef83-121">Questo modello può essere archiviato come file e aggiunto al controllo del codice sorgente.</span><span class="sxs-lookup"><span data-stu-id="3ef83-121">This template could be stored as a file and added to source control.</span></span>

<span data-ttu-id="3ef83-122">**EmployeeCardTemplate.json**</span><span class="sxs-lookup"><span data-stu-id="3ef83-122">**EmployeeCardTemplate.json**</span></span>

```json
{
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hi {employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: {employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: {employee.peers[0].name}, {employee.peers[1].name}, {employee.peers[2].name}"
        }
    ]
}
```

<span data-ttu-id="3ef83-123">Puoi quindi caricarlo e fornire i dati in fase di esecuzione tramite gli [SDK per la creazione di modelli](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="3ef83-123">Then load it up and provide the data at runtime using the [Templating SDKs](sdk.md).</span></span>

<span data-ttu-id="3ef83-124">**Esempio di JavaScript**</span><span class="sxs-lookup"><span data-stu-id="3ef83-124">**JavaScript example**</span></span>

<span data-ttu-id="3ef83-125">Uso del pacchetto [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating).</span><span class="sxs-lookup"><span data-stu-id="3ef83-125">Using the [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating) package.</span></span>

```js
var template = new ACData.Template({ 
    // EmployeeCardTemplate goes here
});

// Specify data at runtime
var dataContext = new ACData.EvaluationContext();
dataContext.$root = {
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
};

var card = template.expand(dataContext);
// Now you have an AdaptiveCard ready to render!
```

## <a name="designer-support"></a><span data-ttu-id="3ef83-126">Supporto per Designer</span><span class="sxs-lookup"><span data-stu-id="3ef83-126">Designer Support</span></span>

<span data-ttu-id="3ef83-127">Adaptive Cards Designer è stato aggiornato per supportare la creazione di modelli.</span><span class="sxs-lookup"><span data-stu-id="3ef83-127">The Adaptive Card Designer has been updated to support templating.</span></span> 

> <span data-ttu-id="3ef83-128">Provala all'indirizzo: **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)** .</span><span class="sxs-lookup"><span data-stu-id="3ef83-128">Try it out at: **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**</span></span>

<span data-ttu-id="3ef83-129">[![Immagine](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="3ef83-129">[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span></span>

* <span data-ttu-id="3ef83-130">**Sample Data Editor**: specifica qui i dati di esempio per visualizzare la scheda associata ai dati quando si trova in modalità di anteprima.</span><span class="sxs-lookup"><span data-stu-id="3ef83-130">**Sample Data Editor** - Specify sample data here to view the data-bound card when in "Preview Mode."</span></span> <span data-ttu-id="3ef83-131">Il piccolo pulsante presente in questo riquadro consente di popolare la struttura dati dai dati di esempio esistenti.</span><span class="sxs-lookup"><span data-stu-id="3ef83-131">There is a small button in this pane to populate the Data Structure from the existing sample data.</span></span>
* <span data-ttu-id="3ef83-132">**Data Structure**: è la struttura dei dati di esempio.</span><span class="sxs-lookup"><span data-stu-id="3ef83-132">**Data Structure** - This is the structure of your sample data.</span></span> <span data-ttu-id="3ef83-133">I campi possono essere trascinati nell'area di progettazione per creare un binding.</span><span class="sxs-lookup"><span data-stu-id="3ef83-133">Fields can be dragged onto the design surface to create a binding to them</span></span> 
* <span data-ttu-id="3ef83-134">**Preview Mode**: premi il pulsante della barra degli strumenti per passare dall'esperienza di modifica a quella di anteprima dei dati di esempio e viceversa.</span><span class="sxs-lookup"><span data-stu-id="3ef83-134">**Preview Mode** - Press the toolbar button to toggle between the edit-experience and the sample-data-preview experience</span></span>
* <span data-ttu-id="3ef83-135">**Open Sample**: fai clic su questo pulsante per aprire vari payload di esempio.</span><span class="sxs-lookup"><span data-stu-id="3ef83-135">**Open Sample** - click this button to open various sample payloads</span></span>

## <a name="advanced-binding"></a><span data-ttu-id="3ef83-136">Binding avanzato</span><span class="sxs-lookup"><span data-stu-id="3ef83-136">Advanced binding</span></span>

### <a name="binding-scopes"></a><span data-ttu-id="3ef83-137">Ambiti di binding</span><span class="sxs-lookup"><span data-stu-id="3ef83-137">Binding scopes</span></span>

<span data-ttu-id="3ef83-138">Esistono alcune parole chiave riservate per accedere a diversi ambiti di binding.</span><span class="sxs-lookup"><span data-stu-id="3ef83-138">There are a few reserved keywords to access various binding scopes.</span></span> 

<span data-ttu-id="3ef83-139">*Nota:* non tutti sono implementati nella versione di anteprima.</span><span class="sxs-lookup"><span data-stu-id="3ef83-139">*Note:* not all of these are implemented in the preview.</span></span>

```json
{
    "{<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating",
    "$host": "Access properties of the host *(not working yet)*"
}
```

### <a name="assigning-a-data-context-to-elements"></a><span data-ttu-id="3ef83-140">Assegnazione di un contesto dati agli elementi</span><span class="sxs-lookup"><span data-stu-id="3ef83-140">Assigning a data context to elements</span></span>

<span data-ttu-id="3ef83-141">Per assegnare un contesto dati a qualsiasi elemento, aggiungi all'elemento un attributo `$data`.</span><span class="sxs-lookup"><span data-stu-id="3ef83-141">To assign a "data context" to any element add a `$data` attribute to the element.</span></span>

```json
{
    "type": "Container",
    "$data": "{mySubObject}",
    "items": [
        {
            "type": "TextBlock",
            "text": "This TextBlock is now scoped directly to 'mySubObject': {mySubObjectProperty}"
        },
        {
            "type": "TextBlock",
            "text": "To break-out and access the root data, use: {$root}"
        }
    ]
}
```

## <a name="repeating-items-in-an-array"></a><span data-ttu-id="3ef83-142">Ripetizione di elementi in una matrice</span><span class="sxs-lookup"><span data-stu-id="3ef83-142">Repeating items in an array</span></span>

<span data-ttu-id="3ef83-143">Questa parte presenta numerosi aspetti da chiarire.</span><span class="sxs-lookup"><span data-stu-id="3ef83-143">This part is a bit of "dark magic".</span></span> <span data-ttu-id="3ef83-144">Ringraziamo in anticipo per il feedback che vorrete fornirci.</span><span class="sxs-lookup"><span data-stu-id="3ef83-144">Feedback welcome.</span></span>

* <span data-ttu-id="3ef83-145">Se la proprietà `$data` di un elemento Adaptive Card è associata a una **matrice**, l'**elemento Adaptive Card verrà ripetuto per ciascun elemento della matrice**.</span><span class="sxs-lookup"><span data-stu-id="3ef83-145">If an Adaptive Card element's `$data` property is bound to an **array**, then the **element itself will be repeated for each item in the array.**</span></span> 
* <span data-ttu-id="3ef83-146">Tutte le espressioni di binding (`{myProperty}`) usate nei valori delle proprietà saranno limitate all'ambito del **singolo elemento** all'interno della matrice.</span><span class="sxs-lookup"><span data-stu-id="3ef83-146">Any binding expressions (`{myProperty}`) used in property values will be scoped to the **individual item** within the array.</span></span>
* <span data-ttu-id="3ef83-147">Se è stato eseguito il binding a una matrice di stringhe, usa `{$data}` per accedere al singolo elemento stringa,</span><span class="sxs-lookup"><span data-stu-id="3ef83-147">If binding to an array of strings, use `{$data}` to access the individual string element.</span></span> <span data-ttu-id="3ef83-148">ad esempio `"text": "{$data}"`</span><span class="sxs-lookup"><span data-stu-id="3ef83-148">E.g., `"text": "{$data}"`</span></span>

<span data-ttu-id="3ef83-149">Ad esempio, l'elemento `TextBlock` seguente sarà ripetuto tre volte poiché il relativo `$data` è una matrice.</span><span class="sxs-lookup"><span data-stu-id="3ef83-149">For example, the `TextBlock` below will be repeated 3 times since it's `$data` is an array.</span></span> <span data-ttu-id="3ef83-150">Si noti che la proprietà `text` è associata alla proprietà `name` di un singolo oggetto all'interno della matrice.</span><span class="sxs-lookup"><span data-stu-id="3ef83-150">Notice how the `text` property is bound to the `name` property of an individual object within the array.</span></span> 

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
            "text": "{name}"
        }
    ]
}
```

<span data-ttu-id="3ef83-151">**Risultato:**</span><span class="sxs-lookup"><span data-stu-id="3ef83-151">**Resulting in:**</span></span>

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

## <a name="functions"></a><span data-ttu-id="3ef83-152">Funzioni</span><span class="sxs-lookup"><span data-stu-id="3ef83-152">Functions</span></span>

<span data-ttu-id="3ef83-153">Nessun linguaggio per la creazione di modelli è completo senza alcune funzioni helper.</span><span class="sxs-lookup"><span data-stu-id="3ef83-153">No templating language is complete without some helper functions.</span></span> <span data-ttu-id="3ef83-154">Forniremo un set di funzioni standard utili per ogni SDK.</span><span class="sxs-lookup"><span data-stu-id="3ef83-154">We will provide a standard set of functions that work on every SDK.</span></span> 

<span data-ttu-id="3ef83-155">La sintassi non è stata ancora definita, pertanto ricontrolla a breve. Ecco uno schema preliminare delle funzioni pianificate:</span><span class="sxs-lookup"><span data-stu-id="3ef83-155">The syntax here is still up in the air so please check back soon, but here's a start of what we're planning:</span></span>

### <a name="string-functions"></a><span data-ttu-id="3ef83-156">Funzioni stringa</span><span class="sxs-lookup"><span data-stu-id="3ef83-156">String functions</span></span>

* <span data-ttu-id="3ef83-157">substr</span><span class="sxs-lookup"><span data-stu-id="3ef83-157">substr</span></span>
* <span data-ttu-id="3ef83-158">indexOf *(non ancora funzionante)*</span><span class="sxs-lookup"><span data-stu-id="3ef83-158">indexOf *(not working yet)*</span></span>
* <span data-ttu-id="3ef83-159">toUpper *(non ancora funzionante)*</span><span class="sxs-lookup"><span data-stu-id="3ef83-159">toUpper *(not working yet)*</span></span>
* <span data-ttu-id="3ef83-160">toLower *(non ancora funzionante)*</span><span class="sxs-lookup"><span data-stu-id="3ef83-160">toLower *(not working yet)*</span></span>

### <a name="number-functions"></a><span data-ttu-id="3ef83-161">Funzioni numero</span><span class="sxs-lookup"><span data-stu-id="3ef83-161">Number functions</span></span>

* <span data-ttu-id="3ef83-162">Formattazione (valuta, decimale e così via) *(non ancora funzionante)*</span><span class="sxs-lookup"><span data-stu-id="3ef83-162">Formatting (currency, decimal, etc) *(not working yet)*</span></span>

### <a name="date-functions"></a><span data-ttu-id="3ef83-163">Funzioni data</span><span class="sxs-lookup"><span data-stu-id="3ef83-163">Date functions</span></span>

* <span data-ttu-id="3ef83-164">Analisi dei formati di stringa di data noti *(non ancora funzionante)*</span><span class="sxs-lookup"><span data-stu-id="3ef83-164">Parsing well-known date string formats *(not working yet)*</span></span>
* <span data-ttu-id="3ef83-165">Formattazione delle rappresentazioni di data/ora note *(non ancora funzionante)*</span><span class="sxs-lookup"><span data-stu-id="3ef83-165">Formatting for well-known date/time representations *(not working yet)*</span></span>

### <a name="conditional-functions"></a><span data-ttu-id="3ef83-166">Funzioni condizionali</span><span class="sxs-lookup"><span data-stu-id="3ef83-166">Conditional functions</span></span>

* <span data-ttu-id="3ef83-167">if(*expression*, *trueValue*, *falseValue*)</span><span class="sxs-lookup"><span data-stu-id="3ef83-167">if(*expression*, *trueValue*, *falseValue*)</span></span>

<span data-ttu-id="3ef83-168">**Esempio di `if`**</span><span class="sxs-lookup"><span data-stu-id="3ef83-168">**`if` example**</span></span>

```json
{
    "type": "TextBlock",
    "color": "{if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="data-manipulation"></a><span data-ttu-id="3ef83-169">Manipolazione dei dati</span><span class="sxs-lookup"><span data-stu-id="3ef83-169">Data manipulation</span></span>

* <span data-ttu-id="3ef83-170">JSON.parse: capacità di analizzare una stringa JSON</span><span class="sxs-lookup"><span data-stu-id="3ef83-170">JSON.parse - ability to parse a JSON string</span></span> 

<span data-ttu-id="3ef83-171">**Esempio di `JSON.parse`**</span><span class="sxs-lookup"><span data-stu-id="3ef83-171">**`JSON.parse` example**</span></span>

<span data-ttu-id="3ef83-172">Si tratta di una risposta DevOps di Azure in cui la proprietà `message` è una stringa serializzata in JSON.</span><span class="sxs-lookup"><span data-stu-id="3ef83-172">This is an Azure DevOps response where the `message` property is a JSON-serialized string.</span></span> <span data-ttu-id="3ef83-173">Per accedere ai valori all'interno della stringa, dobbiamo usare la funzione `JSON.parse` nel modello.</span><span class="sxs-lookup"><span data-stu-id="3ef83-173">In order to access values within the string, we need to use the `JSON.parse` function in our template.</span></span>

<span data-ttu-id="3ef83-174">**Dati**</span><span class="sxs-lookup"><span data-stu-id="3ef83-174">**Data**</span></span> 

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

<span data-ttu-id="3ef83-175">**Utilizzo**</span><span class="sxs-lookup"><span data-stu-id="3ef83-175">**Usage**</span></span>

```json
{
    "type": "TextBlock",
    "text": "{JSON.parse(message).releaseName}"
}
```

<span data-ttu-id="3ef83-176">**Risultato**</span><span class="sxs-lookup"><span data-stu-id="3ef83-176">**Resulting In**</span></span>

```json
{
    "type": "TextBlock",
    "text": "Release-104"
}
```

### <a name="custom-functions"></a><span data-ttu-id="3ef83-177">Funzioni personalizzate</span><span class="sxs-lookup"><span data-stu-id="3ef83-177">Custom functions</span></span>

<span data-ttu-id="3ef83-178">Vogliamo assicurarci che gli host possano aggiungere funzioni personalizzate e dobbiamo quindi prevedere un supporto efficace per il fallback nel caso in cui una funzione non sia supportata.</span><span class="sxs-lookup"><span data-stu-id="3ef83-178">We want to make sure Hosts can add custom functions, which means we need robust support for fallback support if a function isn't supported.</span></span> <span data-ttu-id="3ef83-179">Questo aspetto è ancora in fase di valutazione.</span><span class="sxs-lookup"><span data-stu-id="3ef83-179">We are still evaluating this.</span></span>

## <a name="conditional-layout"></a><span data-ttu-id="3ef83-180">Layout condizionale</span><span class="sxs-lookup"><span data-stu-id="3ef83-180">Conditional layout</span></span>

<span data-ttu-id="3ef83-181">Per eliminare un intero elemento nel caso in cui venga soddisfatta una condizione, usa la proprietà `$when`.</span><span class="sxs-lookup"><span data-stu-id="3ef83-181">To drop an entire element if a condition is met, use the `$when` property.</span></span> <span data-ttu-id="3ef83-182">Se il valore di `$when` risulta essere `false`, l'elemento non verrà visualizzato per l'utente.</span><span class="sxs-lookup"><span data-stu-id="3ef83-182">If `$when` evaluates to `false` the element will not appear to the user.</span></span>

```json
{
    "type": "AdaptiveCard",
    "$data": {
        "price": "35"
    },
    "body": [
        {
            "type": "TextBlock",
            "$when": "{price > 30}",
            "text": "This thing is pricy!",
            "color": "attention",
        },
         {
            "type": "TextBlock",
            "$when": "{price <= 30}",
            "text": "Dang, this thing is cheap!",
            "color": "good"
        }
    ]
}
```

### <a name="composing-templates"></a><span data-ttu-id="3ef83-183">Composizione di modelli</span><span class="sxs-lookup"><span data-stu-id="3ef83-183">Composing templates</span></span>

<span data-ttu-id="3ef83-184">Attualmente non è disponibile alcun supporto per la composizione di parti del modello.</span><span class="sxs-lookup"><span data-stu-id="3ef83-184">Currently there is no support for composing template "parts" together.</span></span> <span data-ttu-id="3ef83-185">Tuttavia, stiamo esplorando varie opzioni e ci auguriamo di condividere presto altre informazioni.</span><span class="sxs-lookup"><span data-stu-id="3ef83-185">But we are exploring options and hope to share more soon.</span></span> <span data-ttu-id="3ef83-186">Si accetta qualsiasi suggerimento.</span><span class="sxs-lookup"><span data-stu-id="3ef83-186">Any thoughts here welcome!</span></span>


## <a name="examples"></a><span data-ttu-id="3ef83-187">Esempi</span><span class="sxs-lookup"><span data-stu-id="3ef83-187">Examples</span></span>

<span data-ttu-id="3ef83-188">Accedi alla [pagina degli esempi](https://adaptivecards.io/samples) aggiornati per esplorare tutti i tipi di nuove schede basate su modelli.</span><span class="sxs-lookup"><span data-stu-id="3ef83-188">Browse the updated [Samples page](https://adaptivecards.io/samples) to explore all sorts of new templated cards.</span></span>
