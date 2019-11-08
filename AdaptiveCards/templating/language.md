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
# <a name="adaptive-cards-template-language"></a>Lingua del modello di schede adattive

Il modello consente la separazione dei **dati** dal **layout** nella scheda adattiva. Il modello Language è la sintassi utilizzata per creare un modello. 

> Per una [Panoramica del modello di scheda adattivo](index.md) , vedere.

> [!IMPORTANT] 
> 
> Queste funzionalità sono disponibili **in anteprima e sono soggette a modifiche**. Il tuo feedback non solo è apprezzato, ma è anche fondamentale per aiutarci a offrire le funzionalità di cui **tu** hai bisogno.

Quando si crea un modello, è possibile specificare i dati inline con il payload del `AdaptiveCard` o in fase di esecuzione usando gli SDK per i [modelli](sdk.md).

## <a name="specify-data-within-the-card"></a>Specificare i dati all'interno della scheda

Per fornire i dati direttamente all'interno del payload della scheda, è sufficiente aggiungere un `$data` attributo al `AdaptiveCard` (illustrato di seguito).

## <a name="binding-to-the-data"></a>Associazione ai dati

È possibile associare i dati all'interno del `body` o `actions` della scheda.

* La sintassi di associazione inizia con `{` e termina con `}`. Ad esempio, `{myProperty}`
* Notazione del punto per accedere agli oggetti secondari
* Sintassi dell'indicizzatore per recuperare le proprietà in base alla chiave o agli elementi di una matrice
* Gestione dei valori null normale per le gerarchie complete
* *La documentazione della sintassi di escape sarà presto disponibile*

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

## <a name="separating-the-template-from-the-data"></a>Separazione del modello dai dati

In alternativa, è possibile creare una scheda riutilizzabile "template" senza includere i dati. Questo modello può essere archiviato come file e aggiunto al controllo del codice sorgente.

**EmployeeCardTemplate.json**

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

Quindi caricarlo e fornire i dati in fase di esecuzione usando gli SDK per i [modelli](sdk.md).

**Esempio JavaScript**

Uso del pacchetto [adaptivecards-template](https://npmjs.com/package/adaptivecards-templating) .

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

## <a name="designer-support"></a>Supporto della finestra di progettazione

La finestra di progettazione della scheda Adaptive è stata aggiornata per supportare i modelli. 

> Per provarlo, vedere:  **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**

[immagine di ![](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)

* **Editor dati di esempio** : specificare qui i dati di esempio per visualizzare la scheda con associazione a dati in "modalità di anteprima". In questo riquadro è disponibile un piccolo pulsante per popolare la struttura dei dati dai dati di esempio esistenti.
* **Struttura dei dati** : questa è la struttura dei dati di esempio. I campi possono essere trascinati nell'area di progettazione per creare un'associazione 
* **Modalità di anteprima** : premere il pulsante della barra degli strumenti per passare dall'esperienza di modifica all'esperienza e dall'anteprima dei dati di esempio
* **Apri esempio** : fare clic su questo pulsante per aprire diversi payload di esempio

## <a name="advanced-binding"></a>Associazione avanzata

### <a name="binding-scopes"></a>Ambiti di associazione

Sono disponibili alcune parole chiave riservate per accedere a diversi ambiti di associazione. 

*Nota:* non tutti questi sono implementati nell'anteprima.

```json
{
    "{<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating",
    "$host": "Access properties of the host *(not working yet)*"
}
```

### <a name="assigning-a-data-context-to-elements"></a>Assegnazione di un contesto dati agli elementi

Per assegnare un "contesto dati" a qualsiasi elemento, aggiungere un attributo `$data` all'elemento.

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

## <a name="repeating-items-in-an-array"></a>Ripetizione di elementi in una matrice

Questa parte è un po' di "magia scura". Commenti e suggerimenti introduttivi.

* Se la proprietà `$data` degli oggetti è impostata su una **matrice**, l' **oggetto stesso verrà ripetuto per ogni elemento nella matrice.** 
* Quando viene ripetuto, `$data` usato nei binding di proprietà è limitato al **singolo elemento** all'interno della matrice.

Ad esempio, la `TextBlock` seguente verrà ripetuta 3 volte poiché è `$data` è una matrice. Si noti che la proprietà `text` è associata alla proprietà `name` di un singolo oggetto all'interno della matrice. 

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

**Risultato:**

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

## <a name="functions"></a>Funzioni

Nessun linguaggio del modello è completo senza alcune funzioni helper. Si fornirà un set standard di funzioni che funzionano in ogni SDK. 

La sintassi qui è ancora in aria, quindi riprovare a breve, ma ecco un inizio di ciò che stiamo pianificando:

### <a name="string-functions"></a>Funzioni stringa

* substr
* indexOf *(non funzionante)*
* ToUpper *(non funzionante)*
* ToLower *(non funzionante)*

### <a name="number-functions"></a>Funzioni numeriche

* Formattazione (valuta, decimale e così via) *(non ancora funzionante)*

### <a name="date-functions"></a>Funzioni di data

* Analisi di formati di stringa di data noti *(non ancora funzionante)*
* Formattazione delle rappresentazioni di data/ora note *(non ancora in esecuzione)*

### <a name="conditional-functions"></a>Funzioni condizionali

* if (*Expression*, *TrueValue*, *FalseValue*)

**esempio di`if`**

```json
{
    "type": "TextBlock",
    "color": "{if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="data-manipulation"></a>Manipolazione dei dati

* JSON. Parse-possibilità di analizzare una stringa JSON 

**esempio di`JSON.parse`**

Si tratta di una risposta DevOps di Azure in cui la proprietà `message` è una stringa serializzata in JSON. Per accedere ai valori all'interno della stringa, è necessario usare la funzione `JSON.parse` nel modello.

**Dati** 

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

**Utilizzo**

```json
{
    "type": "TextBlock",
    "text": "{JSON.parse(message).releaseName}"
}
```

**Risultato**

```json
{
    "type": "TextBlock",
    "text": "Release-104"
}
```

### <a name="custom-functions"></a>Funzioni personalizzate

È necessario assicurarsi che gli host possano aggiungere funzioni personalizzate, il che significa che è necessario un supporto efficace per il supporto di fallback se una funzione non è supportata. Stiamo ancora valutando questo problema.

## <a name="conditional-layout"></a>Layout condizionale

Per eliminare un intero elemento se viene soddisfatta una condizione, utilizzare la proprietà `$when`. Se `$when` restituisce `false` l'elemento non verrà visualizzato all'utente.

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

### <a name="composing-templates"></a>Composizione di modelli

Attualmente non è disponibile alcun supporto per la composizione di "parti" del modello. Tuttavia, stiamo esplorando le opzioni e ci auguriamo di condividere più presto. Tutti i pensieri sono benvenuti.


## <a name="examples"></a>Esempi

Esplorare la [pagina Samples](https://adaptivecards.io/samples) aggiornata per esplorare tutti i tipi di nuove schede basate su modelli.
