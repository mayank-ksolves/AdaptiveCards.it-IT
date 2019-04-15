---
title: Attività iniziali
author: matthidinger
ms.author: mahiding
ms.date: 11/9/2017
ms.topic: article
ms.openlocfilehash: 9d363da0c10b242e23d2594984292fcc1f31382f
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552683"
---
# <a name="getting-started"></a>Attività iniziali 

Una scheda adattiva è un modello a oggetti serializzati con JSON smart card.

## <a name="adaptive-card-structure"></a>Struttura della scheda adattiva

La struttura di base di una scheda è come segue:

* `AdaptiveCard` -L'oggetto radice descrive AdaptiveCard, tra cui la composizione di elemento, le azioni, come devono essere pronunciato e la versione dello schema necessario per eseguirne il rendering.
* `body` -Il corpo della scheda è costituito da blocchi predefiniti noto come `elements`. Gli elementi possono essere composte negli accordi quasi infinite per creare molti tipi di schede. 
* `actions` -Molte schede includono un set di azioni che un utente può eseguire su di esso. Questa proprietà descrive le azioni che in genere sottoposti a rendering in una barra"azione" nella parte inferiore.

### <a name="example-card"></a>Scheda di esempio

Questa scheda di esempio che include una singola riga di testo seguita da un'immagine.

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

Ogni elemento ha un `type` è la proprietà che identifica quale tipo di oggetto. Esaminando la scheda precedente, si possono individuare sono di due elementi, un `TextBlock` e un `Image`.

Tutti gli elementi di scheda adattiva **raggruppati verticalmente** e **espandere la larghezza del relativo elemento padre** (pensare `display: block` in formato HTML). Tuttavia, è possibile usare un `ColumnSet` creare colonne side-by-side di contenitori.

## <a name="adaptive-elements"></a>Elementi adattivi

Gli elementi più importanti sono:

* **TextBlock** -aggiunge un blocco di testo con le proprietà per controllare l'aspetto del testo
* **Immagine** -aggiunge un'immagine con le proprietà per controllare l'aspetto dell'immagine

## <a name="container-elements"></a>Elementi contenitore

Le schede possono avere anche i contenitori, disporre di una raccolta di elementi figlio.

* **Contenitore** -definisce una raccolta di elementi
* **/ Colonna ColumnSet** -definisce una raccolta di colonne, ogni colonna è un contenitore
* **FactSet** -contenitore di fact
* **ImageSet** -esperienza di raccolta per una raccolta di immagini di foto di immagini del contenitore in modo da tale interfaccia utente può visualizzare appropriato.

## <a name="input-elements"></a>Elementi di input

Gli elementi di input consentono di porre per interfaccia utente nativa compilare moduli semplici:

* **Input.Text** -ottenere contenuto di testo dall'utente
* **Input.Date** -ottenere una data dall'utente
* **Input.Time** -ottenere una volta dall'utente
* **Input.Number** -ottenere un numero da parte dell'utente
* **Input.ChoiceSet** : concedere all'utente un set di scelte e che siano selezionate
* **Input.Toggle** : concedere all'utente una scelta singola tra due elementi e che siano selezionate

## <a name="actions"></a>Azioni

Azioni aggiungere pulsanti alla scheda. Si può eseguire una serie di azioni, ad esempio l'apertura di un URL o l'invio di alcuni dati.

* **Action.OpenUrl** -pulsante consente di aprire un URL esterno per la visualizzazione
* **Action.ShowCard** -richiede una carta secondari da visualizzare all'utente.
* **Action.Submit** -porre per tutti gli elementi di input di raccogliere in un oggetto che viene quindi inviato all'utente tramite un metodo definito dall'applicazione host.

> **Esempio Action.Submit**: Con Skype, un Action.Submit invierà un bot di Bot Framework attività al bot con i **valore** proprietà che contiene un oggetto con tutti i dati di input su di esso.

## <a name="learn-more"></a>Altre informazioni

* [Individuare le schede di esempio](http://adaptivecards.io/samples/) per trovare l'ispirazione
* Usare la [Schema Explorer](http://adaptivecards.io/explorer) per esplorare gli elementi disponibili
* Creare una scheda usando il [Visualizzatore interattivo](http://adaptivecards.io/visualizer/)
* [Contattare il supporto](http://adaptivecards.io/connect) con eventuali commenti
