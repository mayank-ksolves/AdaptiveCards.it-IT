---
title: Convalida dell'input
author: rebeccaanne
ms.author: rebecch
ms.date: 07/24/2020
ms.topic: article
ms.openlocfilehash: 08fb2cb5b2b6fa1f227ec5a530f8063dc26b40e3
ms.sourcegitcommit: 19c08b1370305fb2965de0140c5e632356e78513
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2020
ms.locfileid: "87879135"
---
# <a name="input-validation"></a>Convalida dell'input

Nelle versioni 1.3 e successive dello schema, AdaptiveCards supporta la convalida dell'input lato client per i tipi di input.

### <a name="validation-properties"></a>Proprietà di convalida

Per la convalida in AdaptiveCards sono supportate le proprietà seguenti:

| Input | Proprietà |
| --- | --- | 
| `Input.ChoiceSet` | `isRequired` | 
| `Input.Date` | `isRequired` <br> `min`<br> `max` | 
| `Input.Number` | `isRequired` <br> `min`<br> `max` |
| `Input.Text` | `isRequired` <br> `regex` <br> `maxLength` |
| `Input.Time` | `isRequired` <br> `min`<br> `max` | 
| `Input.Toggle` | `isRequired` | 

Per tutti i tipi di input è disponibile una proprietà `errorMessage` per specificare l'errore che deve essere visualizzato se l'utente immette un valore non valido. 

> [!NOTE]
>
> In alcune piattaforme le proprietà min e max (inclusa maxLength) possono essere applicate direttamente dal controllo. È ad esempio possibile applicare una proprietà min per Input.Date impedendo agli utenti di selezionare una data prima del limite minimo in un controllo di selezione data. In tal caso, è possibile che il messaggio di errore non venga visualizzato.

## <a name="labels"></a>Etichette

Un'altra proprietà aggiunta nella versione dello schema 1.3 per tutti gli elementi di input è la proprietà di stringa `label`. L'uso della proprietà `label` è il metodo consigliato per contrassegnare gli input in una scheda adattiva, davanti alla proprietà `placeholder`. Si tratta di un metodo semplice e rapido per etichettare gli input per gli autori di schede e offre i vantaggi seguenti:
* Indicatori di convalida: come indicato in precedenza, gli input possono essere contrassegnati come obbligatori, quindi le etichette per gli input obbligatori avranno un indicatore visivo. Questo indicatore visivo è definito in `HostConfig` e, per impostazione predefinita, viene visualizzato come asterisco `*`.
* Accessibilità: con una connessione tra etichette e input, le librerie del renderer possono impostare le proprietà necessarie per consentire agli utenti di usare prodotti di assistive technology (utilità per la lettura dello schermo) per poter interagire correttamente con gli input delle schede adattive.
    * Etichette e segnaposto: come illustrato da Katie Sherwin nell'articolo [Placeholders in form fields are harmful](https://www.nngroup.com/articles/form-design-placeholders/) (I segnaposto nei campi di un modulo sono dannosi), l'uso dei segnaposto presenta molte conseguenze negative, ad esempio la limitazione della memoria a breve termine degli utenti, l'aumento della difficoltà per gli utenti di verificare i relativi input prima dell'invio, la difficoltà di lettura per gli utenti in quanto, in genere, il testo del segnaposto presenta un contrasto dei colori insufficiente rispetto allo sfondo oppure le utilità di lettura dello schermo non leggono il testo del segnaposto, per citarne solo alcuni.
    * TextBlock e RichTextBlock: sebbene l'uso di altri elementi della scheda come etichette possa sembrare una soluzione efficace, presenta il problema di non poter applicare la prossimità tra input ed etichette. D'altra parte, l'uso della proprietà `label` garantisce che entrambi gli elementi visivi vengano visualizzati uno accanto all'altro in modo da favorire gli utenti che necessitano dell'ingrandimento dello schermo.

## <a name="fields-to-be-validated-and-submitted"></a>Campi da convalidare e inviare

Gli input vengono convalidati quando l'utente fa clic su un'azione Action.Submit nella scheda. Gli input che vengono convalidati e inviati per una determinata azione Action.Submit sono i seguenti:

 - Input nella stessa scheda dell'azione Action.Submit
 - Input in una qualsiasi scheda padre della scheda contenente l'azione Action.Submit, nel caso di una scheda associata a un'azione Action.ShowCard

Se gli input superano la convalida, i valori nei rispettivi campi verranno restituiti al client. Se invece non superano la convalida, verranno visualizzati i messaggi di errore relativi agli input non validi e l'invio non verrà eseguito.

> [!NOTE]
>
> Gli input **non** vengono convalidati o inviati se si trovano in una scheda figlio o in una scheda di pari livello di quella contenente l'azione Action.Submit. Sono incluse le schede risultanti da Action.ShowCards in ActionSets nel corpo di tale scheda. Questo comportamento è diverso da quello delle versioni del renderer precedenti la 2.0 e si applica alle schede di tutte le versioni dello schema, indipendentemente dal fatto che vengano utilizzate le proprietà di convalida dell'input. 

## <a name="other-considerations-and-known-issues"></a>Altre considerazioni e problemi noti

 - Non è consigliabile creare input con proprietà di convalida che potrebbero non essere sempre visibili a causa dell'interazione con Action.ToggleVisibility. I messaggi di errore e le indicazioni visive per la segnalazione di input non valido non verranno visualizzati se l'input non è al momento visibile, il che può generare confusione riguardo al motivo per cui l'invio è bloccato.

 - Il comportamento della convalida dell'input per gli host che usano schede con visualizzazione popup tramite il valore `"actions":"showCard":"actionMode":"popup"` nella configurazione host non è ben definito. Le schede con visualizzazione popup potrebbero essere deprecate in una versione futura.