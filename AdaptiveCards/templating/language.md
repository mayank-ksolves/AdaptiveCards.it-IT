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
# <a name="adaptive-cards-template-language"></a>Linguaggio del modello di Schede adattive

La creazione di modelli consente di separare i **dati** dal **layout** nella scheda adattiva. Il linguaggio del modello è la sintassi usata per creare un modello. 

> Per una [panoramica della creazione di modelli di schede adattive](index.md), leggi l'argomento specifico.

> [!IMPORTANT] 
> 
> **Modifiche importanti** apportate alla **versione finale candidata di maggio 2020**
>
> Abbiamo lavorato intensamente per il rilascio della creazione di modelli e abbiamo finalmente raggiunto l'obiettivo. Abbiamo dovuto apportare alcune piccole modifiche importanti, man mano che ci avvicinavamo alla data del rilascio.

## <a name="breaking-changes-as-of-may-2020"></a>Modifiche importanti della versione di maggio 2020

1. La sintassi di binding è cambiata da `{...}` a `${...}`.
    * Ad esempio, `"text": "Hello {name}"` diventa `"text": "Hello ${name}"`
    
## <a name="binding-to-data"></a>Binding ai dati

La scrittura di un modello è semplice quanto la sostituzione del contenuto "non statico" della scheda con "espressioni di binding".

### <a name="static-card-payload"></a>Payload scheda statica

```json
{
   "type": "TextBlock",
   "text": "Matt"
}
```

### <a name="template-payload"></a>Payload modello

```json
{
   "type": "TextBlock",
   "text": "${firstName}"
}
```

* Le espressioni di binding possono essere posizionate in qualsiasi punto in cui è presente contenuto statico
* La sintassi di binding inizia con `${` e termina con `}`, ad esempio `${myProperty}`
* Usa *Notazione Dot* per accedere agli oggetti secondari di una gerarchia di oggetti, ad esempio `${myParent.myChild}`
* Una gestione regolare dei valori null garantisce che non vengano generate eccezioni se accedi a una proprietà null in un oggetto grafico
* Usa la *sintassi dell'indicizzatore* per recuperare le proprietà in base alla chiave o agli elementi di una matrice, ad esempio `${myArray[0]}`

## <a name="providing-the-data"></a>Specificare i dati

Ora che disponi di un modello, devi specificare i dati che lo rendono completo. A questo scopo, sono disponibili due opzioni:

1. **Opzione A: inline all'interno del payload del modello**. Puoi specificare i dati inline all'interno del payload del modello `AdaptiveCard`. Per eseguire questa operazione, aggiungi semplicemente un attributo `$data` all'oggetto radice `AdaptiveCard`.
2. **Opzione B: come oggetto dati separato**. Con questa opzione, puoi specificare due oggetti separati nell'[SDK per la creazione di modelli](sdk.md) in fase di esecuzione: `template` e `data`. Si tratta dell'approccio più comune, dal momento che, in genere, si crea innanzitutto un modello e i dati dinamici vengono specificati in un secondo momento.

### <a name="option-a-inline-data"></a>Opzione A: Dati inline

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

### <a name="option-b-separating-the-template-from-the-data"></a>Opzione B: Separazione del modello dai dati

In alternativa (e con maggiore probabilità), creerai un modello di scheda riutilizzabile senza includere i dati. Questo modello può essere archiviato come file e aggiunto al controllo del codice sorgente.

**EmployeeCardTemplate.json**

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

Puoi quindi caricarlo e fornire i dati in fase di esecuzione tramite gli [SDK per la creazione di modelli](sdk.md).

**Esempio di JavaScript**

Uso del pacchetto [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating).

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

## <a name="designer-support"></a>Supporto per Designer

Adaptive Cards Designer è stato aggiornato per supportare la creazione di modelli. 

> Provala all'indirizzo: **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)** .

[![Immagine](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)

* **Sample Data Editor**: specifica qui i dati di esempio per visualizzare la scheda associata ai dati quando si trova in modalità di anteprima. Il piccolo pulsante presente in questo riquadro consente di popolare la struttura dati dai dati di esempio esistenti.
* **Preview Mode**: premi il pulsante della barra degli strumenti per passare dall'esperienza di modifica a quella di anteprima dei dati di esempio e viceversa.
* **Open Sample**: fai clic su questo pulsante per aprire vari payload di esempio.

## <a name="advanced-binding"></a>Binding avanzato

### <a name="binding-scopes"></a>Ambiti di binding

Esistono alcune parole chiave riservate per accedere a diversi ambiti di binding. 

```json
{
    "${<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating"
}
```

### <a name="assigning-a-data-context-to-elements"></a>Assegnazione di un contesto dati agli elementi

Per assegnare un contesto dati a qualsiasi elemento, aggiungi all'elemento un attributo `$data`.

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

## <a name="repeating-items-in-an-array"></a>Ripetizione di elementi in una matrice

* Se la proprietà `$data` di un elemento Adaptive Card è associata a una **matrice**, l'**elemento Adaptive Card verrà ripetuto per ciascun elemento della matrice**. 
* Tutte le espressioni di binding (`${myProperty}`) usate nei valori delle proprietà saranno limitate all'ambito del **singolo elemento** all'interno della matrice.
* Se è stato eseguito il binding a una matrice di stringhe, usa `${$data}` per accedere al singolo elemento stringa, ad esempio `"text": "${$data}"`

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
            "text": "${name}"
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

## <a name="built-in-functions"></a>Funzioni integrate

Nessun linguaggio per la creazione di modelli è completo senza una suite completa di funzioni helper. La creazione di modelli di schede adattive si basa sul [linguaggio di espressioni adattive](https://aka.ms/adaptive-expressions), uno standard aperto per la dichiarazione di espressioni che possono essere valutate su molte piattaforme diverse. Si tratta di un superset appropriato di "app per la logica", quindi puoi usare una sintassi simile a quella di Power Automate e così via.

**Ecco un piccolo campionamento delle funzioni predefinite.**

Vedi l'elenco completo delle [funzioni predefinite del linguaggio delle espressioni adattive](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-concept-adaptive-expressions?view=azure-bot-service-4.0).

### <a name="conditional-evaluation"></a>Valutazione condizionale

* if(*expression*, *trueValue*, *falseValue*)

**Esempio di `if`**

```json
{
    "type": "TextBlock",
    "color": "${if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="parsing-json"></a>Analisi del contenuto JSON

* json(*jsonString*) - Analizza una stringa JSON

**Esempio di `json`**

Si tratta di una risposta DevOps di Azure in cui la proprietà `message` è una stringa serializzata in JSON. Per accedere ai valori all'interno della stringa, dobbiamo usare la funzione `json` nel modello.

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
    "text": "${json(message).releaseName}"
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

Le funzioni personalizzate sono supportate tramite le API negli [SDK per la creazione di modelli](sdk.md). 

## <a name="conditional-layout-with-when"></a>Layout condizionale con `$when`

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

### <a name="composing-templates"></a>Composizione di modelli

Attualmente non è disponibile alcun supporto per la composizione di parti del modello. Tuttavia, stiamo esplorando varie opzioni e ci auguriamo di condividere presto altre informazioni. Si accetta qualsiasi suggerimento.

## <a name="examples"></a>Esempi

Accedi alla [pagina degli esempi](https://adaptivecards.io/samples) aggiornati per esplorare tutti i tipi di nuove schede basate su modelli.
