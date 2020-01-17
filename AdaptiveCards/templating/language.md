---
title: Lingua del modello di schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 2c583f774451e60f825cd8fd2c38f2ea34c2f8de
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145401"
---
# <a name="adaptive-cards-template-language"></a><span data-ttu-id="8c715-102">Lingua del modello di schede adattive</span><span class="sxs-lookup"><span data-stu-id="8c715-102">Adaptive Cards Template Language</span></span>

<span data-ttu-id="8c715-103">Il modello consente la separazione dei **dati** dal **layout** nella scheda adattiva.</span><span class="sxs-lookup"><span data-stu-id="8c715-103">Templating enables the separation of **data** from **layout** in your Adaptive Card.</span></span> <span data-ttu-id="8c715-104">Il modello Language è la sintassi utilizzata per creare un modello.</span><span class="sxs-lookup"><span data-stu-id="8c715-104">The template langauge is the syntax used to author a template.</span></span> 

> <span data-ttu-id="8c715-105">Per una [Panoramica del modello di scheda adattivo](index.md) , vedere.</span><span class="sxs-lookup"><span data-stu-id="8c715-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="8c715-106">Queste funzionalità sono disponibili **in anteprima e sono soggette a modifiche**.</span><span class="sxs-lookup"><span data-stu-id="8c715-106">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="8c715-107">Il tuo feedback non solo è apprezzato, ma è anche fondamentale per aiutarci a offrire le funzionalità di cui **tu** hai bisogno.</span><span class="sxs-lookup"><span data-stu-id="8c715-107">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

<span data-ttu-id="8c715-108">Quando si crea un modello, è possibile specificare i dati inline con il payload del `AdaptiveCard` o in fase di esecuzione usando gli SDK per i [modelli](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="8c715-108">When authoring a template you can specify the data inline with the `AdaptiveCard` payload, or at runtime using the [Templating SDKs](sdk.md).</span></span>

## <a name="specify-data-within-the-card"></a><span data-ttu-id="8c715-109">Specificare i dati all'interno della scheda</span><span class="sxs-lookup"><span data-stu-id="8c715-109">Specify data within the card</span></span>

<span data-ttu-id="8c715-110">Per fornire i dati direttamente all'interno del payload della scheda, è sufficiente aggiungere un `$data` attributo al `AdaptiveCard` (illustrato di seguito).</span><span class="sxs-lookup"><span data-stu-id="8c715-110">To provide data directly within the card payload, simply add a `$data` attribute to your `AdaptiveCard` (seen below).</span></span>

## <a name="binding-to-the-data"></a><span data-ttu-id="8c715-111">Associazione ai dati</span><span class="sxs-lookup"><span data-stu-id="8c715-111">Binding to the data</span></span>

<span data-ttu-id="8c715-112">È possibile associare i dati all'interno del `body` o `actions` della scheda.</span><span class="sxs-lookup"><span data-stu-id="8c715-112">You can bind to the data within the `body` or `actions` of the card.</span></span>

* <span data-ttu-id="8c715-113">La sintassi di associazione inizia con `{` e termina con `}`.</span><span class="sxs-lookup"><span data-stu-id="8c715-113">Binding syntax starts with `{` and ends with `}`.</span></span> <span data-ttu-id="8c715-114">Ad esempio, `{myProperty}`</span><span class="sxs-lookup"><span data-stu-id="8c715-114">E.g., `{myProperty}`</span></span>
* <span data-ttu-id="8c715-115">Notazione del punto per accedere agli oggetti secondari</span><span class="sxs-lookup"><span data-stu-id="8c715-115">Dot-notation to access sub-objects</span></span>
* <span data-ttu-id="8c715-116">Sintassi dell'indicizzatore per recuperare le proprietà in base alla chiave o agli elementi di una matrice</span><span class="sxs-lookup"><span data-stu-id="8c715-116">Indexer syntax to retrieve properties by key or items in an array</span></span>
* <span data-ttu-id="8c715-117">Gestione dei valori null normale per le gerarchie complete</span><span class="sxs-lookup"><span data-stu-id="8c715-117">Graceful null handling for deep hierarchies</span></span>
* <span data-ttu-id="8c715-118">*La documentazione della sintassi di escape sarà presto disponibile*</span><span class="sxs-lookup"><span data-stu-id="8c715-118">*Escape syntax documentation to come soon*</span></span>

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

## <a name="separating-the-template-from-the-data"></a><span data-ttu-id="8c715-119">Separazione del modello dai dati</span><span class="sxs-lookup"><span data-stu-id="8c715-119">Separating the template from the data</span></span>

<span data-ttu-id="8c715-120">In alternativa, è possibile creare una scheda riutilizzabile "template" senza includere i dati.</span><span class="sxs-lookup"><span data-stu-id="8c715-120">Alternatively (and more likely), you will create a re-usable card "template" without including the data.</span></span> <span data-ttu-id="8c715-121">Questo modello può essere archiviato come file e aggiunto al controllo del codice sorgente.</span><span class="sxs-lookup"><span data-stu-id="8c715-121">This template could be stored as a file and added to source control.</span></span>

<span data-ttu-id="8c715-122">**EmployeeCardTemplate.json**</span><span class="sxs-lookup"><span data-stu-id="8c715-122">**EmployeeCardTemplate.json**</span></span>

```json
{
    "type": "AdaptivCard",
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

<span data-ttu-id="8c715-123">Quindi caricarlo e fornire i dati in fase di esecuzione usando gli SDK per i [modelli](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="8c715-123">Then load it up and provide the data at runtime using the [Templating SDKs](sdk.md).</span></span>

<span data-ttu-id="8c715-124">**Esempio JavaScript**</span><span class="sxs-lookup"><span data-stu-id="8c715-124">**JavaScript example**</span></span>

<span data-ttu-id="8c715-125">Uso del pacchetto [adaptivecards-template](https://npmjs.com/package/adaptivecards-templating) .</span><span class="sxs-lookup"><span data-stu-id="8c715-125">Using the [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating) package.</span></span>

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

## <a name="designer-support"></a><span data-ttu-id="8c715-126">Supporto della finestra di progettazione</span><span class="sxs-lookup"><span data-stu-id="8c715-126">Designer Support</span></span>

<span data-ttu-id="8c715-127">La finestra di progettazione della scheda Adaptive è stata aggiornata per supportare i modelli.</span><span class="sxs-lookup"><span data-stu-id="8c715-127">The Adaptive Card Designer has been updated to support templating.</span></span> 

> <span data-ttu-id="8c715-128">Per provarlo, vedere:  **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**</span><span class="sxs-lookup"><span data-stu-id="8c715-128">Try it out at: **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**</span></span>

<span data-ttu-id="8c715-129">[immagine di ![](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="8c715-129">[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span></span>

* <span data-ttu-id="8c715-130">**Editor dati di esempio** : specificare qui i dati di esempio per visualizzare la scheda con associazione a dati in "modalità di anteprima".</span><span class="sxs-lookup"><span data-stu-id="8c715-130">**Sample Data Editor** - Specify sample data here to view the data-bound card when in "Preview Mode."</span></span> <span data-ttu-id="8c715-131">In questo riquadro è disponibile un piccolo pulsante per popolare la struttura dei dati dai dati di esempio esistenti.</span><span class="sxs-lookup"><span data-stu-id="8c715-131">There is a small button in this pane to populate the Data Structure from the existing sample data.</span></span>
* <span data-ttu-id="8c715-132">**Struttura dei dati** : questa è la struttura dei dati di esempio.</span><span class="sxs-lookup"><span data-stu-id="8c715-132">**Data Structure** - This is the structure of your sample data.</span></span> <span data-ttu-id="8c715-133">I campi possono essere trascinati nell'area di progettazione per creare un'associazione</span><span class="sxs-lookup"><span data-stu-id="8c715-133">Fields can be dragged onto the design surface to create a binding to them</span></span> 
* <span data-ttu-id="8c715-134">**Modalità di anteprima** : premere il pulsante della barra degli strumenti per passare dall'esperienza di modifica all'esperienza e dall'anteprima dei dati di esempio</span><span class="sxs-lookup"><span data-stu-id="8c715-134">**Preview Mode** - Press the toolbar button to toggle between the edit-experience and the sample-data-preview experience</span></span>
* <span data-ttu-id="8c715-135">**Apri esempio** : fare clic su questo pulsante per aprire diversi payload di esempio</span><span class="sxs-lookup"><span data-stu-id="8c715-135">**Open Sample** - click this button to open various sample payloads</span></span>

## <a name="advanced-binding"></a><span data-ttu-id="8c715-136">Associazione avanzata</span><span class="sxs-lookup"><span data-stu-id="8c715-136">Advanced binding</span></span>

### <a name="binding-scopes"></a><span data-ttu-id="8c715-137">Ambiti di associazione</span><span class="sxs-lookup"><span data-stu-id="8c715-137">Binding scopes</span></span>

<span data-ttu-id="8c715-138">Sono disponibili alcune parole chiave riservate per accedere a diversi ambiti di associazione.</span><span class="sxs-lookup"><span data-stu-id="8c715-138">There are a few reserved keywords to access various binding scopes.</span></span> 

<span data-ttu-id="8c715-139">*Nota:* non tutti questi sono implementati nell'anteprima.</span><span class="sxs-lookup"><span data-stu-id="8c715-139">*Note:* not all of these are implemented in the preview.</span></span>

```json
{
    "{<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating",
    "$host": "Access properties of the host *(not working yet)*"
}
```

### <a name="assigning-a-data-context-to-elements"></a><span data-ttu-id="8c715-140">Assegnazione di un contesto dati agli elementi</span><span class="sxs-lookup"><span data-stu-id="8c715-140">Assigning a data context to elements</span></span>

<span data-ttu-id="8c715-141">Per assegnare un "contesto dati" a qualsiasi elemento, aggiungere un attributo `$data` all'elemento.</span><span class="sxs-lookup"><span data-stu-id="8c715-141">To assign a "data context" to any element add a `$data` attribute to the element.</span></span>

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

## <a name="repeating-items-in-an-array"></a><span data-ttu-id="8c715-142">Ripetizione di elementi in una matrice</span><span class="sxs-lookup"><span data-stu-id="8c715-142">Repeating items in an array</span></span>

<span data-ttu-id="8c715-143">Questa parte è un po' di "magia scura".</span><span class="sxs-lookup"><span data-stu-id="8c715-143">This part is a bit of "dark magic".</span></span> <span data-ttu-id="8c715-144">Commenti e suggerimenti introduttivi.</span><span class="sxs-lookup"><span data-stu-id="8c715-144">Feedback welcome.</span></span>

* <span data-ttu-id="8c715-145">Se la proprietà `$data` di un elemento della scheda adattivo è associata a una **matrice**, l' **elemento stesso verrà ripetuto per ogni elemento nella matrice.**</span><span class="sxs-lookup"><span data-stu-id="8c715-145">If an Adaptive Card element's `$data` property is bound to an **array**, then the **element itself will be repeated for each item in the array.**</span></span> 
* <span data-ttu-id="8c715-146">Tutte le espressioni di associazione (`{myProperty}`) utilizzate nei valori delle proprietà verranno limitate a un **singolo elemento** all'interno della matrice.</span><span class="sxs-lookup"><span data-stu-id="8c715-146">Any binding expressions (`{myProperty}`) used in property values will be scoped to the **individual item** within the array.</span></span>
* <span data-ttu-id="8c715-147">Se si associa a una matrice di stringhe, usare `{$data}` per accedere al singolo elemento stringa.</span><span class="sxs-lookup"><span data-stu-id="8c715-147">If binding to an array of strings, use `{$data}` to access the individual string element.</span></span> <span data-ttu-id="8c715-148">Ad esempio, `"text": "{$data}"`</span><span class="sxs-lookup"><span data-stu-id="8c715-148">E.g., `"text": "{$data}"`</span></span>

<span data-ttu-id="8c715-149">Ad esempio, la `TextBlock` seguente verrà ripetuta 3 volte poiché è `$data` è una matrice.</span><span class="sxs-lookup"><span data-stu-id="8c715-149">For example, the `TextBlock` below will be repeated 3 times since it's `$data` is an array.</span></span> <span data-ttu-id="8c715-150">Si noti che la proprietà `text` è associata alla proprietà `name` di un singolo oggetto all'interno della matrice.</span><span class="sxs-lookup"><span data-stu-id="8c715-150">Notice how the `text` property is bound to the `name` property of an individual object within the array.</span></span> 

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

<span data-ttu-id="8c715-151">**Risultato:**</span><span class="sxs-lookup"><span data-stu-id="8c715-151">**Resulting in:**</span></span>

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

## <a name="functions"></a><span data-ttu-id="8c715-152">Funzioni</span><span class="sxs-lookup"><span data-stu-id="8c715-152">Functions</span></span>

<span data-ttu-id="8c715-153">Nessun linguaggio del modello è completo senza alcune funzioni helper.</span><span class="sxs-lookup"><span data-stu-id="8c715-153">No templating language is complete without some helper functions.</span></span> <span data-ttu-id="8c715-154">Si fornirà un set standard di funzioni che funzionano in ogni SDK.</span><span class="sxs-lookup"><span data-stu-id="8c715-154">We will provide a standard set of functions that work on every SDK.</span></span> 

<span data-ttu-id="8c715-155">La sintassi qui è ancora in aria, quindi riprovare a breve, ma ecco un inizio di ciò che stiamo pianificando:</span><span class="sxs-lookup"><span data-stu-id="8c715-155">The syntax here is still up in the air so please check back soon, but here's a start of what we're planning:</span></span>

### <a name="string-functions"></a><span data-ttu-id="8c715-156">Funzioni per i valori stringa</span><span class="sxs-lookup"><span data-stu-id="8c715-156">String functions</span></span>

* <span data-ttu-id="8c715-157">substr</span><span class="sxs-lookup"><span data-stu-id="8c715-157">substr</span></span>
* <span data-ttu-id="8c715-158">indexOf *(non funzionante)*</span><span class="sxs-lookup"><span data-stu-id="8c715-158">indexOf *(not working yet)*</span></span>
* <span data-ttu-id="8c715-159">ToUpper *(non funzionante)*</span><span class="sxs-lookup"><span data-stu-id="8c715-159">toUpper *(not working yet)*</span></span>
* <span data-ttu-id="8c715-160">ToLower *(non funzionante)*</span><span class="sxs-lookup"><span data-stu-id="8c715-160">toLower *(not working yet)*</span></span>

### <a name="number-functions"></a><span data-ttu-id="8c715-161">Funzioni numeriche</span><span class="sxs-lookup"><span data-stu-id="8c715-161">Number functions</span></span>

* <span data-ttu-id="8c715-162">Formattazione (valuta, decimale e così via) *(non ancora funzionante)*</span><span class="sxs-lookup"><span data-stu-id="8c715-162">Formatting (currency, decimal, etc) *(not working yet)*</span></span>

### <a name="date-functions"></a><span data-ttu-id="8c715-163">Funzioni di data</span><span class="sxs-lookup"><span data-stu-id="8c715-163">Date functions</span></span>

* <span data-ttu-id="8c715-164">Analisi di formati di stringa di data noti *(non ancora funzionante)*</span><span class="sxs-lookup"><span data-stu-id="8c715-164">Parsing well-known date string formats *(not working yet)*</span></span>
* <span data-ttu-id="8c715-165">Formattazione delle rappresentazioni di data/ora note *(non ancora in esecuzione)*</span><span class="sxs-lookup"><span data-stu-id="8c715-165">Formatting for well-known date/time representations *(not working yet)*</span></span>

### <a name="conditional-functions"></a><span data-ttu-id="8c715-166">Funzioni condizionali</span><span class="sxs-lookup"><span data-stu-id="8c715-166">Conditional functions</span></span>

* <span data-ttu-id="8c715-167">if (*Expression*, *TrueValue*, *FalseValue*)</span><span class="sxs-lookup"><span data-stu-id="8c715-167">if(*expression*, *trueValue*, *falseValue*)</span></span>

<span data-ttu-id="8c715-168">**esempio di `if`**</span><span class="sxs-lookup"><span data-stu-id="8c715-168">**`if` example**</span></span>

```json
{
    "type": "TextBlock",
    "color": "{if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="data-manipulation"></a><span data-ttu-id="8c715-169">Manipolazione dei dati</span><span class="sxs-lookup"><span data-stu-id="8c715-169">Data manipulation</span></span>

* <span data-ttu-id="8c715-170">JSON. Parse-possibilità di analizzare una stringa JSON</span><span class="sxs-lookup"><span data-stu-id="8c715-170">JSON.parse - ability to parse a JSON string</span></span> 

<span data-ttu-id="8c715-171">**esempio di `JSON.parse`**</span><span class="sxs-lookup"><span data-stu-id="8c715-171">**`JSON.parse` example**</span></span>

<span data-ttu-id="8c715-172">Si tratta di una risposta DevOps di Azure in cui la proprietà `message` è una stringa serializzata in JSON.</span><span class="sxs-lookup"><span data-stu-id="8c715-172">This is an Azure DevOps response where the `message` property is a JSON-serialized string.</span></span> <span data-ttu-id="8c715-173">Per accedere ai valori all'interno della stringa, è necessario usare la funzione `JSON.parse` nel modello.</span><span class="sxs-lookup"><span data-stu-id="8c715-173">In order to access values within the string, we need to use the `JSON.parse` function in our template.</span></span>

<span data-ttu-id="8c715-174">**Dati**</span><span class="sxs-lookup"><span data-stu-id="8c715-174">**Data**</span></span> 

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

<span data-ttu-id="8c715-175">**Uso**</span><span class="sxs-lookup"><span data-stu-id="8c715-175">**Usage**</span></span>

```json
{
    "type": "TextBlock",
    "text": "{JSON.parse(message).releaseName}"
}
```

<span data-ttu-id="8c715-176">**Risultato**</span><span class="sxs-lookup"><span data-stu-id="8c715-176">**Resulting In**</span></span>

```json
{
    "type": "TextBlock",
    "text": "Release-104"
}
```

### <a name="custom-functions"></a><span data-ttu-id="8c715-177">Funzioni personalizzate</span><span class="sxs-lookup"><span data-stu-id="8c715-177">Custom functions</span></span>

<span data-ttu-id="8c715-178">È necessario assicurarsi che gli host possano aggiungere funzioni personalizzate, il che significa che è necessario un supporto efficace per il supporto di fallback se una funzione non è supportata.</span><span class="sxs-lookup"><span data-stu-id="8c715-178">We want to make sure Hosts can add custom functions, which means we need robust support for fallback support if a function isn't supported.</span></span> <span data-ttu-id="8c715-179">Stiamo ancora valutando questo problema.</span><span class="sxs-lookup"><span data-stu-id="8c715-179">We are still evaluating this.</span></span>

## <a name="conditional-layout"></a><span data-ttu-id="8c715-180">Layout condizionale</span><span class="sxs-lookup"><span data-stu-id="8c715-180">Conditional layout</span></span>

<span data-ttu-id="8c715-181">Per eliminare un intero elemento se viene soddisfatta una condizione, utilizzare la proprietà `$when`.</span><span class="sxs-lookup"><span data-stu-id="8c715-181">To drop an entire element if a condition is met, use the `$when` property.</span></span> <span data-ttu-id="8c715-182">Se `$when` restituisce `false` l'elemento non verrà visualizzato all'utente.</span><span class="sxs-lookup"><span data-stu-id="8c715-182">If `$when` evaluates to `false` the element will not appear to the user.</span></span>

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

### <a name="composing-templates"></a><span data-ttu-id="8c715-183">Composizione di modelli</span><span class="sxs-lookup"><span data-stu-id="8c715-183">Composing templates</span></span>

<span data-ttu-id="8c715-184">Attualmente non è disponibile alcun supporto per la composizione di "parti" del modello.</span><span class="sxs-lookup"><span data-stu-id="8c715-184">Currently there is no support for composing template "parts" together.</span></span> <span data-ttu-id="8c715-185">Tuttavia, stiamo esplorando le opzioni e ci auguriamo di condividere più presto.</span><span class="sxs-lookup"><span data-stu-id="8c715-185">But we are exploring options and hope to share more soon.</span></span> <span data-ttu-id="8c715-186">Tutti i pensieri sono benvenuti.</span><span class="sxs-lookup"><span data-stu-id="8c715-186">Any thoughts here welcome!</span></span>


## <a name="examples"></a><span data-ttu-id="8c715-187">Esempi</span><span class="sxs-lookup"><span data-stu-id="8c715-187">Examples</span></span>

<span data-ttu-id="8c715-188">Esplorare la [pagina Samples](https://adaptivecards.io/samples) aggiornata per esplorare tutti i tipi di nuove schede basate su modelli.</span><span class="sxs-lookup"><span data-stu-id="8c715-188">Browse the updated [Samples page](https://adaptivecards.io/samples) to explore all sorts of new templated cards.</span></span>
