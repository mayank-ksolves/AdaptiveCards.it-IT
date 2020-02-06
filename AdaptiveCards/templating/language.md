---
title: Linguaggio del modello di Schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 2c583f774451e60f825cd8fd2c38f2ea34c2f8de
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145401"
---
# <a name="adaptive-cards-template-language"></a>Linguaggio del modello di Schede adattive

La creazione di modelli consente di separare i **dati** dal **layout** nella scheda adattiva. Il linguaggio del modello è la sintassi usata per creare un modello. 

> Per una [panoramica della creazione di modelli di schede adattive](index.md), leggi l'argomento specifico.

> [!IMPORTANT] 
> 
> Queste funzionalità sono disponibili **in anteprima e sono soggette a modifiche**. Il tuo feedback non solo è apprezzato, ma è anche fondamentale per aiutarci a offrire le funzionalità di cui **tu** hai bisogno.

Quando crei un modello, puoi specificare i dati inline con il payload di `AdaptiveCard` oppure in fase di esecuzione usando gli [SDK per la creazione di modelli](sdk.md).

## <a name="specify-data-within-the-card"></a>Specificare dati all'interno della scheda

Per fornire i dati direttamente all'interno del payload della scheda, aggiungi semplicemente un attributo `$data` ad `AdaptiveCard` (vedi più avanti).

## <a name="binding-to-the-data"></a>Binding ai dati

Puoi eseguire il binding ai dati all'interno di `body` o `actions` della scheda.

* La sintassi di binding inizia con `{` e termina con `}`, ad esempio `{myProperty}`
* Notazione Dot per accedere ai sotto-oggetti
* Sintassi dell'indicizzatore per recuperare le proprietà in base alla chiave o agli elementi di una matrice
* Gestione automatica dei valori null per le gerarchie profonde
* *Documentazione relativa alla sintassi di escape presto disponibile*

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

In alternativa (e con maggiore probabilità), creerai un modello di scheda riutilizzabile senza includere i dati. Questo modello può essere archiviato come file e aggiunto al controllo del codice sorgente.

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

Puoi quindi caricarlo e fornire i dati in fase di esecuzione tramite gli [SDK per la creazione di modelli](sdk.md).

**Esempio di JavaScript**

Uso del pacchetto [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating).

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

## <a name="designer-support"></a>Supporto per Designer

Adaptive Cards Designer è stato aggiornato per supportare la creazione di modelli. 

> Provala all'indirizzo: **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)** .

[![Immagine](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)

* **Sample Data Editor**: specifica qui i dati di esempio per visualizzare la scheda associata ai dati quando si trova in modalità di anteprima. Il piccolo pulsante presente in questo riquadro consente di popolare la struttura dati dai dati di esempio esistenti.
* **Data Structure**: è la struttura dei dati di esempio. I campi possono essere trascinati nell'area di progettazione per creare un binding. 
* **Preview Mode**: premi il pulsante della barra degli strumenti per passare dall'esperienza di modifica a quella di anteprima dei dati di esempio e viceversa.
* **Open Sample**: fai clic su questo pulsante per aprire vari payload di esempio.

## <a name="advanced-binding"></a>Binding avanzato

### <a name="binding-scopes"></a>Ambiti di binding

Esistono alcune parole chiave riservate per accedere a diversi ambiti di binding. 

*Nota:* non tutti sono implementati nella versione di anteprima.

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

Per assegnare un contesto dati a qualsiasi elemento, aggiungi all'elemento un attributo `$data`.

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

Questa parte presenta numerosi aspetti da chiarire. Ringraziamo in anticipo per il feedback che vorrete fornirci.

* Se la proprietà `$data` di un elemento Adaptive Card è associata a una **matrice**, l'**elemento Adaptive Card verrà ripetuto per ciascun elemento della matrice**. 
* Tutte le espressioni di binding (`{myProperty}`) usate nei valori delle proprietà saranno limitate all'ambito del **singolo elemento** all'interno della matrice.
* Se è stato eseguito il binding a una matrice di stringhe, usa `{$data}` per accedere al singolo elemento stringa, ad esempio `"text": "{$data}"`

Ad esempio, l'elemento `TextBlock` seguente sarà ripetuto tre volte poiché il relativo `$data` è una matrice. Si noti che la proprietà `text` è associata alla proprietà `name` di un singolo oggetto all'interno della matrice. 

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

Nessun linguaggio per la creazione di modelli è completo senza alcune funzioni helper. Forniremo un set di funzioni standard utili per ogni SDK. 

La sintassi non è stata ancora definita, pertanto ricontrolla a breve. Ecco uno schema preliminare delle funzioni pianificate:

### <a name="string-functions"></a>Funzioni stringa

* substr
* indexOf *(non ancora funzionante)*
* toUpper *(non ancora funzionante)*
* toLower *(non ancora funzionante)*

### <a name="number-functions"></a>Funzioni numero

* Formattazione (valuta, decimale e così via) *(non ancora funzionante)*

### <a name="date-functions"></a>Funzioni data

* Analisi dei formati di stringa di data noti *(non ancora funzionante)*
* Formattazione delle rappresentazioni di data/ora note *(non ancora funzionante)*

### <a name="conditional-functions"></a>Funzioni condizionali

* if(*expression*, *trueValue*, *falseValue*)

**Esempio di `if`**

```json
{
    "type": "TextBlock",
    "color": "{if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="data-manipulation"></a>Manipolazione dei dati

* JSON.parse: capacità di analizzare una stringa JSON 

**Esempio di `JSON.parse`**

Si tratta di una risposta DevOps di Azure in cui la proprietà `message` è una stringa serializzata in JSON. Per accedere ai valori all'interno della stringa, dobbiamo usare la funzione `JSON.parse` nel modello.

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

Vogliamo assicurarci che gli host possano aggiungere funzioni personalizzate e dobbiamo quindi prevedere un supporto efficace per il fallback nel caso in cui una funzione non sia supportata. Questo aspetto è ancora in fase di valutazione.

## <a name="conditional-layout"></a>Layout condizionale

Per eliminare un intero elemento nel caso in cui venga soddisfatta una condizione, usa la proprietà `$when`. Se il valore di `$when` risulta essere `false`, l'elemento non verrà visualizzato per l'utente.

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

Attualmente non è disponibile alcun supporto per la composizione di parti del modello. Tuttavia, stiamo esplorando varie opzioni e ci auguriamo di condividere presto altre informazioni. Si accetta qualsiasi suggerimento.


## <a name="examples"></a>Esempi

Accedi alla [pagina degli esempi](https://adaptivecards.io/samples) aggiornati per esplorare tutti i tipi di nuove schede basate su modelli.
