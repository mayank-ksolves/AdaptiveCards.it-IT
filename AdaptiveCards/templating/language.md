---
title: Lingua del modello di schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 42a1f43fbcfe1416820637af750acc960b9effde
ms.sourcegitcommit: 16a274ce5596001a1c5ab252d9d2a3db6a5a9a0d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73750406"
---
# <a name="adaptive-cards-template-language"></a><span data-ttu-id="989e2-102">Lingua del modello di schede adattive</span><span class="sxs-lookup"><span data-stu-id="989e2-102">Adaptive Cards Template Language</span></span>

<span data-ttu-id="989e2-103">Il modello consente la separazione dei **dati** dal **layout** nella scheda adattiva.</span><span class="sxs-lookup"><span data-stu-id="989e2-103">Templating enables the separation of **data** from **layout** in your Adaptive Card.</span></span> <span data-ttu-id="989e2-104">Il modello Language è la sintassi utilizzata per creare un modello.</span><span class="sxs-lookup"><span data-stu-id="989e2-104">The template langauge is the syntax used to author a template.</span></span> 

> <span data-ttu-id="989e2-105">Per una [Panoramica del modello di scheda adattivo](index.md) , vedere.</span><span class="sxs-lookup"><span data-stu-id="989e2-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="989e2-106">Queste funzionalità sono disponibili **in anteprima e sono soggette a modifiche**.</span><span class="sxs-lookup"><span data-stu-id="989e2-106">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="989e2-107">Il tuo feedback non solo è apprezzato, ma è anche fondamentale per aiutarci a offrire le funzionalità di cui **tu** hai bisogno.</span><span class="sxs-lookup"><span data-stu-id="989e2-107">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

<span data-ttu-id="989e2-108">Quando si crea un modello, è possibile specificare i dati inline con il payload del `AdaptiveCard` o in fase di esecuzione usando gli SDK per i [modelli](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="989e2-108">When authoring a template you can specify the data inline with the `AdaptiveCard` payload, or at runtime using the [Templating SDKs](sdk.md).</span></span>

## <a name="specify-data-within-the-card"></a><span data-ttu-id="989e2-109">Specificare i dati all'interno della scheda</span><span class="sxs-lookup"><span data-stu-id="989e2-109">Specify data within the card</span></span>

<span data-ttu-id="989e2-110">Per fornire i dati direttamente all'interno del payload della scheda, è sufficiente aggiungere un `$data` attributo al `AdaptiveCard` (illustrato di seguito).</span><span class="sxs-lookup"><span data-stu-id="989e2-110">To provide data directly within the card payload, simply add a `$data` attribute to your `AdaptiveCard` (seen below).</span></span>

## <a name="binding-to-the-data"></a><span data-ttu-id="989e2-111">Associazione ai dati</span><span class="sxs-lookup"><span data-stu-id="989e2-111">Binding to the data</span></span>

<span data-ttu-id="989e2-112">È possibile associare i dati all'interno del `body` o `actions` della scheda.</span><span class="sxs-lookup"><span data-stu-id="989e2-112">You can bind to the data within the `body` or `actions` of the card.</span></span>

* <span data-ttu-id="989e2-113">La sintassi di associazione inizia con `{` e termina con `}`.</span><span class="sxs-lookup"><span data-stu-id="989e2-113">Binding syntax starts with `{` and ends with `}`.</span></span> <span data-ttu-id="989e2-114">Ad esempio, `{myProperty}`</span><span class="sxs-lookup"><span data-stu-id="989e2-114">E.g., `{myProperty}`</span></span>
* <span data-ttu-id="989e2-115">Notazione del punto per accedere agli oggetti secondari</span><span class="sxs-lookup"><span data-stu-id="989e2-115">Dot-notation to access sub-objects</span></span>
* <span data-ttu-id="989e2-116">Sintassi dell'indicizzatore per recuperare le proprietà in base alla chiave o agli elementi di una matrice</span><span class="sxs-lookup"><span data-stu-id="989e2-116">Indexer syntax to retrieve properties by key or items in an array</span></span>
* <span data-ttu-id="989e2-117">Gestione dei valori null normale per le gerarchie complete</span><span class="sxs-lookup"><span data-stu-id="989e2-117">Graceful null handling for deep hierarchies</span></span>
* <span data-ttu-id="989e2-118">*La documentazione della sintassi di escape sarà presto disponibile*</span><span class="sxs-lookup"><span data-stu-id="989e2-118">*Escape syntax documentation to come soon*</span></span>

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

## <a name="separating-the-template-from-the-data"></a><span data-ttu-id="989e2-119">Separazione del modello dai dati</span><span class="sxs-lookup"><span data-stu-id="989e2-119">Separating the template from the data</span></span>

<span data-ttu-id="989e2-120">In alternativa, è possibile creare una scheda riutilizzabile "template" senza includere i dati.</span><span class="sxs-lookup"><span data-stu-id="989e2-120">Alternatively (and more likely), you will create a re-usable card "template" without including the data.</span></span> <span data-ttu-id="989e2-121">Questo modello può essere archiviato come file e aggiunto al controllo del codice sorgente.</span><span class="sxs-lookup"><span data-stu-id="989e2-121">This template could be stored as a file and added to source control.</span></span>

<span data-ttu-id="989e2-122">**EmployeeCardTemplate.json**</span><span class="sxs-lookup"><span data-stu-id="989e2-122">**EmployeeCardTemplate.json**</span></span>

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

<span data-ttu-id="989e2-123">Quindi caricarlo e fornire i dati in fase di esecuzione usando gli SDK per i [modelli](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="989e2-123">Then load it up and provide the data at runtime using the [Templating SDKs](sdk.md).</span></span>

<span data-ttu-id="989e2-124">**Esempio JavaScript**</span><span class="sxs-lookup"><span data-stu-id="989e2-124">**JavaScript example**</span></span>

<span data-ttu-id="989e2-125">Uso del pacchetto [adaptivecards-template](https://npmjs.com/package/adaptivecards-templating) .</span><span class="sxs-lookup"><span data-stu-id="989e2-125">Using the [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating) package.</span></span>

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

## <a name="designer-support"></a><span data-ttu-id="989e2-126">Supporto della finestra di progettazione</span><span class="sxs-lookup"><span data-stu-id="989e2-126">Designer Support</span></span>

<span data-ttu-id="989e2-127">La finestra di progettazione della scheda Adaptive è stata aggiornata per supportare i modelli.</span><span class="sxs-lookup"><span data-stu-id="989e2-127">The Adaptive Card Designer has been updated to support templating.</span></span> 

> <span data-ttu-id="989e2-128">Per provarlo, vedere:  **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**</span><span class="sxs-lookup"><span data-stu-id="989e2-128">Try it out at: **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**</span></span>

<span data-ttu-id="989e2-129">[immagine di ![](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="989e2-129">[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span></span>

* <span data-ttu-id="989e2-130">**Editor dati di esempio** : specificare qui i dati di esempio per visualizzare la scheda con associazione a dati in "modalità di anteprima".</span><span class="sxs-lookup"><span data-stu-id="989e2-130">**Sample Data Editor** - Specify sample data here to view the data-bound card when in "Preview Mode."</span></span> <span data-ttu-id="989e2-131">In questo riquadro è disponibile un piccolo pulsante per popolare la struttura dei dati dai dati di esempio esistenti.</span><span class="sxs-lookup"><span data-stu-id="989e2-131">There is a small button in this pane to populate the Data Structure from the existing sample data.</span></span>
* <span data-ttu-id="989e2-132">**Struttura dei dati** : questa è la struttura dei dati di esempio.</span><span class="sxs-lookup"><span data-stu-id="989e2-132">**Data Structure** - This is the structure of your sample data.</span></span> <span data-ttu-id="989e2-133">I campi possono essere trascinati nell'area di progettazione per creare un'associazione</span><span class="sxs-lookup"><span data-stu-id="989e2-133">Fields can be dragged onto the design surface to create a binding to them</span></span> 
* <span data-ttu-id="989e2-134">**Modalità di anteprima** : premere il pulsante della barra degli strumenti per passare dall'esperienza di modifica all'esperienza e dall'anteprima dei dati di esempio</span><span class="sxs-lookup"><span data-stu-id="989e2-134">**Preview Mode** - Press the toolbar button to toggle between the edit-experience and the sample-data-preview experience</span></span>
* <span data-ttu-id="989e2-135">**Apri esempio** : fare clic su questo pulsante per aprire diversi payload di esempio</span><span class="sxs-lookup"><span data-stu-id="989e2-135">**Open Sample** - click this button to open various sample payloads</span></span>

## <a name="advanced-binding"></a><span data-ttu-id="989e2-136">Associazione avanzata</span><span class="sxs-lookup"><span data-stu-id="989e2-136">Advanced binding</span></span>

### <a name="binding-scopes"></a><span data-ttu-id="989e2-137">Ambiti di associazione</span><span class="sxs-lookup"><span data-stu-id="989e2-137">Binding scopes</span></span>

<span data-ttu-id="989e2-138">Sono disponibili alcune parole chiave riservate per accedere a diversi ambiti di associazione.</span><span class="sxs-lookup"><span data-stu-id="989e2-138">There are a few reserved keywords to access various binding scopes.</span></span> 

<span data-ttu-id="989e2-139">*Nota:* non tutti questi sono implementati nell'anteprima.</span><span class="sxs-lookup"><span data-stu-id="989e2-139">*Note:* not all of these are implemented in the preview.</span></span>

```json
{
    "{<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating",
    "$host": "Access properties of the host *(not working yet)*"
}
```

### <a name="assigning-a-data-context-to-elements"></a><span data-ttu-id="989e2-140">Assegnazione di un contesto dati agli elementi</span><span class="sxs-lookup"><span data-stu-id="989e2-140">Assigning a data context to elements</span></span>

<span data-ttu-id="989e2-141">Per assegnare un "contesto dati" a qualsiasi elemento, aggiungere un attributo `$data` all'elemento.</span><span class="sxs-lookup"><span data-stu-id="989e2-141">To assign a "data context" to any element add a `$data` attribute to the element.</span></span>

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

## <a name="repeating-items-in-an-array"></a><span data-ttu-id="989e2-142">Ripetizione di elementi in una matrice</span><span class="sxs-lookup"><span data-stu-id="989e2-142">Repeating items in an array</span></span>

<span data-ttu-id="989e2-143">Questa parte è un po' di "magia scura".</span><span class="sxs-lookup"><span data-stu-id="989e2-143">This part is a bit of "dark magic".</span></span> <span data-ttu-id="989e2-144">Commenti e suggerimenti introduttivi.</span><span class="sxs-lookup"><span data-stu-id="989e2-144">Feedback welcome.</span></span>

* <span data-ttu-id="989e2-145">Se la proprietà `$data` degli oggetti è impostata su una **matrice**, l' **oggetto stesso verrà ripetuto per ogni elemento nella matrice.**</span><span class="sxs-lookup"><span data-stu-id="989e2-145">If the objects' `$data` property is set to an **array**, then the **object itself will be repeated for each item in the array.**</span></span> 
* <span data-ttu-id="989e2-146">Quando viene ripetuto, `$data` usato nei binding di proprietà è limitato al **singolo elemento** all'interno della matrice.</span><span class="sxs-lookup"><span data-stu-id="989e2-146">As it is being repeated, `$data` used in property bindings are scoped to the **individual item** within the array.</span></span>

<span data-ttu-id="989e2-147">Ad esempio, la `TextBlock` seguente verrà ripetuta 3 volte poiché è `$data` è una matrice.</span><span class="sxs-lookup"><span data-stu-id="989e2-147">For example, the `TextBlock` below will be repeated 3 times since it's `$data` is an array.</span></span> <span data-ttu-id="989e2-148">Si noti che la proprietà `text` è associata alla proprietà `name` di un singolo oggetto all'interno della matrice.</span><span class="sxs-lookup"><span data-stu-id="989e2-148">Notice how the `text` property is bound to the `name` property of an individual object within the array.</span></span> 

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

<span data-ttu-id="989e2-149">**Risultato:**</span><span class="sxs-lookup"><span data-stu-id="989e2-149">**Resulting in:**</span></span>

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

## <a name="functions"></a><span data-ttu-id="989e2-150">Funzioni</span><span class="sxs-lookup"><span data-stu-id="989e2-150">Functions</span></span>

<span data-ttu-id="989e2-151">Nessun linguaggio del modello è completo senza alcune funzioni helper.</span><span class="sxs-lookup"><span data-stu-id="989e2-151">No templating language is complete without some helper functions.</span></span> <span data-ttu-id="989e2-152">Si fornirà un set standard di funzioni che funzionano in ogni SDK.</span><span class="sxs-lookup"><span data-stu-id="989e2-152">We will provide a standard set of functions that work on every SDK.</span></span> 

<span data-ttu-id="989e2-153">La sintassi qui è ancora in aria, quindi riprovare a breve, ma ecco un inizio di ciò che stiamo pianificando:</span><span class="sxs-lookup"><span data-stu-id="989e2-153">The syntax here is still up in the air so please check back soon, but here's a start of what we're planning:</span></span>

### <a name="string-functions"></a><span data-ttu-id="989e2-154">Funzioni stringa</span><span class="sxs-lookup"><span data-stu-id="989e2-154">String functions</span></span>

* <span data-ttu-id="989e2-155">substr</span><span class="sxs-lookup"><span data-stu-id="989e2-155">substr</span></span>
* <span data-ttu-id="989e2-156">indexOf *(non funzionante)*</span><span class="sxs-lookup"><span data-stu-id="989e2-156">indexOf *(not working yet)*</span></span>
* <span data-ttu-id="989e2-157">ToUpper *(non funzionante)*</span><span class="sxs-lookup"><span data-stu-id="989e2-157">toUpper *(not working yet)*</span></span>
* <span data-ttu-id="989e2-158">ToLower *(non funzionante)*</span><span class="sxs-lookup"><span data-stu-id="989e2-158">toLower *(not working yet)*</span></span>

### <a name="number-functions"></a><span data-ttu-id="989e2-159">Funzioni numeriche</span><span class="sxs-lookup"><span data-stu-id="989e2-159">Number functions</span></span>

* <span data-ttu-id="989e2-160">Formattazione (valuta, decimale e così via) *(non ancora funzionante)*</span><span class="sxs-lookup"><span data-stu-id="989e2-160">Formatting (currency, decimal, etc) *(not working yet)*</span></span>

### <a name="date-functions"></a><span data-ttu-id="989e2-161">Funzioni di data</span><span class="sxs-lookup"><span data-stu-id="989e2-161">Date functions</span></span>

* <span data-ttu-id="989e2-162">Analisi di formati di stringa di data noti *(non ancora funzionante)*</span><span class="sxs-lookup"><span data-stu-id="989e2-162">Parsing well-known date string formats *(not working yet)*</span></span>
* <span data-ttu-id="989e2-163">Formattazione delle rappresentazioni di data/ora note *(non ancora in esecuzione)*</span><span class="sxs-lookup"><span data-stu-id="989e2-163">Formatting for well-known date/time representations *(not working yet)*</span></span>

### <a name="conditional-functions"></a><span data-ttu-id="989e2-164">Funzioni condizionali</span><span class="sxs-lookup"><span data-stu-id="989e2-164">Conditional functions</span></span>

* <span data-ttu-id="989e2-165">if (*Expression*, *TrueValue*, *FalseValue*)</span><span class="sxs-lookup"><span data-stu-id="989e2-165">if(*expression*, *trueValue*, *falseValue*)</span></span>

<span data-ttu-id="989e2-166">**esempio di`if`**</span><span class="sxs-lookup"><span data-stu-id="989e2-166">**`if` example**</span></span>

```json
{
    "type": "TextBlock",
    "color": "{if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="data-manipulation"></a><span data-ttu-id="989e2-167">Manipolazione dei dati</span><span class="sxs-lookup"><span data-stu-id="989e2-167">Data manipulation</span></span>

* <span data-ttu-id="989e2-168">JSON. Parse-possibilità di analizzare una stringa JSON</span><span class="sxs-lookup"><span data-stu-id="989e2-168">JSON.parse - ability to parse a JSON string</span></span> 

<span data-ttu-id="989e2-169">**esempio di`JSON.parse`**</span><span class="sxs-lookup"><span data-stu-id="989e2-169">**`JSON.parse` example**</span></span>

<span data-ttu-id="989e2-170">Si tratta di una risposta DevOps di Azure in cui la proprietà `message` è una stringa serializzata in JSON.</span><span class="sxs-lookup"><span data-stu-id="989e2-170">This is an Azure DevOps response where the `message` property is a JSON-serialized string.</span></span> <span data-ttu-id="989e2-171">Per accedere ai valori all'interno della stringa, è necessario usare la funzione `JSON.parse` nel modello.</span><span class="sxs-lookup"><span data-stu-id="989e2-171">In order to access values within the string, we need to use the `JSON.parse` function in our template.</span></span>

<span data-ttu-id="989e2-172">**Dati**</span><span class="sxs-lookup"><span data-stu-id="989e2-172">**Data**</span></span> 

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

<span data-ttu-id="989e2-173">**Utilizzo**</span><span class="sxs-lookup"><span data-stu-id="989e2-173">**Usage**</span></span>

```json
{
    "type": "TextBlock",
    "text": "{JSON.parse(message).releaseName}"
}
```

<span data-ttu-id="989e2-174">**Risultato**</span><span class="sxs-lookup"><span data-stu-id="989e2-174">**Resulting In**</span></span>

```json
{
    "type": "TextBlock",
    "text": "Release-104"
}
```

### <a name="custom-functions"></a><span data-ttu-id="989e2-175">Funzioni personalizzate</span><span class="sxs-lookup"><span data-stu-id="989e2-175">Custom functions</span></span>

<span data-ttu-id="989e2-176">È necessario assicurarsi che gli host possano aggiungere funzioni personalizzate, il che significa che è necessario un supporto efficace per il supporto di fallback se una funzione non è supportata.</span><span class="sxs-lookup"><span data-stu-id="989e2-176">We want to make sure Hosts can add custom functions, which means we need robust support for fallback support if a function isn't supported.</span></span> <span data-ttu-id="989e2-177">Stiamo ancora valutando questo problema.</span><span class="sxs-lookup"><span data-stu-id="989e2-177">We are still evaluating this.</span></span>

## <a name="conditional-layout"></a><span data-ttu-id="989e2-178">Layout condizionale</span><span class="sxs-lookup"><span data-stu-id="989e2-178">Conditional layout</span></span>

<span data-ttu-id="989e2-179">Per eliminare un intero elemento se viene soddisfatta una condizione, utilizzare la proprietà `$when`.</span><span class="sxs-lookup"><span data-stu-id="989e2-179">To drop an entire element if a condition is met, use the `$when` property.</span></span> <span data-ttu-id="989e2-180">Se `$when` restituisce `false` l'elemento non verrà visualizzato all'utente.</span><span class="sxs-lookup"><span data-stu-id="989e2-180">If `$when` evaluates to `false` the element will not appear to the user.</span></span>

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

### <a name="composing-templates"></a><span data-ttu-id="989e2-181">Composizione di modelli</span><span class="sxs-lookup"><span data-stu-id="989e2-181">Composing templates</span></span>

<span data-ttu-id="989e2-182">Attualmente non è disponibile alcun supporto per la composizione di "parti" del modello.</span><span class="sxs-lookup"><span data-stu-id="989e2-182">Currently there is no support for composing template "parts" together.</span></span> <span data-ttu-id="989e2-183">Tuttavia, stiamo esplorando le opzioni e ci auguriamo di condividere più presto.</span><span class="sxs-lookup"><span data-stu-id="989e2-183">But we are exploring options and hope to share more soon.</span></span> <span data-ttu-id="989e2-184">Tutti i pensieri sono benvenuti.</span><span class="sxs-lookup"><span data-stu-id="989e2-184">Any thoughts here welcome!</span></span>


## <a name="examples"></a><span data-ttu-id="989e2-185">Esempi</span><span class="sxs-lookup"><span data-stu-id="989e2-185">Examples</span></span>

<span data-ttu-id="989e2-186">Esplorare la [pagina Samples](https://adaptivecards.io/samples) aggiornata per esplorare tutti i tipi di nuove schede basate su modelli.</span><span class="sxs-lookup"><span data-stu-id="989e2-186">Browse the updated [Samples page](https://adaptivecards.io/samples) to explore all sorts of new templated cards.</span></span>
