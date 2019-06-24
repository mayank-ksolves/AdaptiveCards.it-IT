---
title: Attività iniziali
author: matthidinger
ms.author: mahiding
ms.date: 11/9/2017
ms.topic: article
ms.openlocfilehash: 9d363da0c10b242e23d2594984292fcc1f31382f
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2019
ms.locfileid: "59552683"
---
# <a name="getting-started"></a>Attività iniziali 

Una scheda adattiva è un modello a oggetti per le schede con serializzazione JSON.

## <a name="adaptive-card-structure"></a>Struttura delle schede adattive

La struttura di base di una scheda è la seguente:

* `AdaptiveCard` - L'oggetto radice descrive la scheda adattiva stessa, tra cui la composizione degli elementi, le azioni, le modalità di pronuncia e la versione dello schema richiesta per il rendering.
* `body` - Il corpo della scheda è costituito da componenti denominati `elements`. Gli elementi possono essere composti in modi praticamente illimitati per creare diversi tipi di schede. 
* `actions` - Molte schede includono un set di azioni che un utente può eseguire su di esse. Questa proprietà descrive tali azioni, di cui in genere viene eseguito il rendering in una "barra delle azioni" nella parte inferiore.

### <a name="example-card"></a>Scheda di esempio

Questa scheda di esempio include una singola riga di testo seguita da un'immagine.

```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Here is a ninja cat"
        },
        {
            "type": "Image",
            "url": "http://adaptivecards.io/content/cats/1.png"
        }
    ]
}
```

## <a name="type-property"></a>Proprietà `Type`

Ogni elemento ha una proprietà `type` che identifica il tipo di oggetto. Esaminando la scheda precedente, puoi notare che sono presenti due elementi, `TextBlock` e `Image`.

Tutti gli elementi della scheda adattiva **sono raggruppati verticalmente** e **si espandono in base alla larghezza del relativo elemento padre** (in modo simile a `display: block` nel codice HTML). Tuttavia, puoi usare un `ColumnSet` per creare colonne affiancate di contenitori.

## <a name="adaptive-elements"></a>Elementi adattivi

Gli elementi più importanti sono:

* **TextBlock** - Aggiunge un blocco di testo con le proprietà per controllare l'aspetto del testo
* **Image** - Aggiunge un'immagine con le proprietà per controllare l'aspetto dell'immagine

## <a name="container-elements"></a>Elementi contenitore

Le schede possono anche includere contenitori, che organizzano una raccolta di elementi figlio.

* **Container** - Definisce una raccolta di elementi
* **ColumnSet/Column** - Definisce una raccolta di colonne, in cui ogni colonna è un contenitore
* **FactSet** - Contenitore di fatti
* **ImageSet** - Contenitore di immagini che consente all'interfaccia utente di visualizzare l'esperienza Raccolta foto appropriata per una raccolta di immagini.

## <a name="input-elements"></a>Elementi di input

Gli elementi di input consentono di richiedere all'interfaccia utente nativa di creare semplici moduli:

* **Input.Text** - Consente di ottenere contenuto di testo dall'utente
* **Input.Date** - Consente di ottenere una data dall'utente
* **Input.Time** - Consente di ottenere un'ora dall'utente
* **Input.Number** - Consente di ottenere un numero dall'utente
* **Input.ChoiceSet** - Consente di offrire all'utente un set di scelte da cui può effettuare una selezione
* **Input.Toggle** - Consente di offrire all'utente una singola scelta tra due elementi da cui può effettuare una selezione

## <a name="actions"></a>Azioni

Le azioni aggiungono pulsanti alla scheda. Questi pulsanti consentono di eseguire un'ampia varietà di azioni, come l'apertura di un URL o l'invio di dati.

* **Action.OpenUrl** - Il pulsante apre un URL esterno per la visualizzazione
* **Action.ShowCard** - Richiede la visualizzazione all'utente di una scheda secondaria.
* **Action.Submit** - Richiede la raccolta di tutti gli elementi di input in un oggetto che viene quindi inviato all'utente tramite un metodo definito dall'applicazione host.

> **Esempio di Action.Submit**: Con Skype, Action.Submit invierà al bot un'attività bot di Bot Framework con la proprietà **Value** che contiene un oggetto con tutti i dati di input.

## <a name="learn-more"></a>Altre informazioni

* [Esamina le schede di esempio](http://adaptivecards.io/samples/) per trovare l'ispirazione
* Usa [Schema Explorer](http://adaptivecards.io/explorer) per informazioni sugli elementi disponibili
* Crea una scheda usando il [visualizzatore interattivo](http://adaptivecards.io/visualizer/)
* [Contattaci](http://adaptivecards.io/connect) per eventuali commenti
