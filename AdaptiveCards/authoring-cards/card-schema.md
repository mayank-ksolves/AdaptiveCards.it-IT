---
title: Schema di smart card
author: paulcam206
ms.author: paulcam
ms.date: 09/18/2018
ms.topic: reference
ms.openlocfilehash: 76a21affcd26798acb52e2bcf1168121838ed00a
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553723"
---
# <a name="card-schema"></a>Schema di smart card

Schede
   * [`AdaptiveCard`](#schema-adaptivecard) -Elemento radice in una scheda adattiva.

Elementi di smart card
   * [`TextBlock`](#schema-textblock) -Consente di visualizzare il testo, che consente di controllare le dimensioni dei caratteri, spessore e colore.
   * [`Image`](#schema-image) -Consente di visualizzare un'immagine.
   * [`Media`](#schema-media) -Consente di visualizzare un lettore multimediale per contenuti audio o video.
   * [`MediaSource`](#schema-mediasource) -Definisce un'origine per un elemento multimediale

Contenitori
   * [`Container`](#schema-container) -Contenitori raggruppano gli elementi.
   * [`ColumnSet`](#schema-columnset) -ColumnSet divide un'area in colonne, consentendo di elementi per un periodo side-by-side.
   * [`Column`](#schema-column) -Definisce un contenitore che fa parte di un set di colonne.
   * [`FactSet`](#schema-factset) -L'elemento di FactSet Visualizza una serie di fact (vale a dire le coppie nome/valore) in un formato tabulare.
   * [`Fact`](#schema-fact) -Viene descritto un Fact in un FactSet come una coppia chiave/valore.
   * [`ImageSet`](#schema-imageset) -Il ImageSet Visualizza una raccolta di immagini simile a una raccolta.

Azioni
   * [`Action.OpenUrl`](#schema-action.openurl) -Quando viene richiamato, visualizzare l'url specificato mediante il relativo avvio in un browser esterno o con in-situ con browser web incorporato.
   * [`Action.Submit`](#schema-action.submit) -Consente di raccogliere i campi di input, vengono uniti con il campo dati facoltativi e un evento viene inviato al client. È compito al client di determinare la modalità di elaborazione dati. Ad esempio: Con BotFramework Bot, il client invia un'attività tramite il supporto di messaggistica al bot.
   * [`Action.ShowCard`](#schema-action.showcard) -Definisce un AdaptiveCard mostrata all'utente quando viene scelto il pulsante o collegamento.

Input
   * [`Input.Text`](#schema-input.text) -Consente un utente di immettere testo.
   * [`Input.Number`](#schema-input.number) -Consente all'utente di immettere un numero.
   * [`Input.Date`](#schema-input.date) -Consente a un utente sceglie una data.
   * [`Input.Time`](#schema-input.time) -Consente di selezionare un'ora.
   * [`Input.Toggle`](#schema-input.toggle) -Consente di scegliere tra due opzioni.
   * [`Input.ChoiceSet`](#schema-input.choiceset) -Consente a un utente di immettere una scelta.
   * [`Input.Choice`](#schema-input.choice) -Descrive una scelta per l'uso in un ChoiceSet.

# <a name="cards"></a>Schede

<a name="schema-adaptivecard"></a>
## <a name="adaptivecard"></a>AdaptiveCard

Elemento radice in una scheda adattiva.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**type**|`"AdaptiveCard"`|Yes|Deve essere `"AdaptiveCard"`.|1.0
|**actions**|`Action[]`| No|Le azioni da visualizzare nella barra delle azioni della scheda.|1.0
|**body**|`array[]`| No|Gli elementi della scheda da visualizzare nell'area primaria smart card.|1.0
|**selectAction**|`object`| No|Un'azione che verrà richiamata quando viene toccata o selezionata la scheda. `Action.ShowCard` non è supportato.|1.0
|**version**|`string`|Yes|Versione dello schema che richiede questa scheda. Se un client è **inferiori** di questa versione, il `fallbackText` verranno sottoposti a rendering.|1.0
|**fallbackText**|`string`| No|Testo visualizzato quando il client non supporta la versione specificata (può contenere markdown).|1.0
|**backgroundImage**|`string`| No|Un'immagine da utilizzare come sfondo della scheda.|1.0
|**speak**|`string`| No|Specifica che cosa deve essere pronunciata per questa scheda intera. Questo è testo semplice o un frammento SSML.|1.0
|**lang**|`string`| No|Il linguaggio di ISO-639-1 2 lettere utilizzato nella scheda. Consente di localizzare le funzioni di data/ora.|1.0


# <a name="card-elements"></a>Elementi di smart card

<a name="schema-textblock"></a>
## <a name="textblock"></a>TextBlock

Visualizza il testo, che consente di controllare le dimensioni dei caratteri, spessore e colore.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**color**|`string`| No|Controllare il colore dei `TextBlock` elementi.|1.0
|**horizontalAlignment**|`string`| No, predefinito: `"left"`|Controlla la modalità con cui gli elementi vengono posizionati in orizzontale all'interno del contenitore.|1.0
|**isSubtle**|`boolean`| No, predefinito: `false`|Se `true`, Visualizza il testo leggermente attenuato visualizzare meno evidente.|1.0
|**maxLines**|`number`| No|Specifica il numero massimo di righe da visualizzare.|1.0
|**size**|`string`| No|Controlla le dimensioni del testo.|1.0
|**text**|`string`|Yes|Testo da visualizzare.|1.0
|**type**|`"TextBlock"`|Yes|Deve essere `"TextBlock"`.|1.0
|**weight**|`string`| No|Controlla il peso di `TextBlock` elementi.|1.0
|**wrap**|`boolean`| No, predefinito: `false`|Se `true`, consentire a capo del testo. In caso contrario, il testo viene ritagliato.|1.0
|**id**|`string`| No|Identificatore univoco associato all'elemento.|1.0
|**spacing**|`string`| No|Controlla la quantità di spaziatura tra questo elemento e l'elemento precedente.|1.0
|**separator**|`boolean`| No, predefinito: `false`|Quando `true`, disegnare una linea di separazione nella parte superiore dell'elemento.|1.0


<a name="schema-image"></a>
## <a name="image"></a>Image

Visualizza un'immagine.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**altText**|`string`| No|Testo alternativo che descrivono l'immagine.|1.0
|**horizontalAlignment**|`string`| No, predefinito: `"left"`|Controlla la modalità con cui gli elementi vengono posizionati in orizzontale all'interno del contenitore.|1.0
|**selectAction**|`object`| No|Un'azione che verrà richiamato quando il `Image` è selezionato o toccato. `Action.ShowCard` non è supportato.|1.0
|**size**|`string`| No, predefinito: `"auto"`|Controlla le dimensioni approssimative dell'immagine. Le dimensioni fisiche possono variare per ogni host. Specificare `"auto"` per la dimensione di immagine true, o `"stretch"` per forzarlo a riempire il contenitore.|1.0
|**style**|`string`| No|Controlli come questo `Image` viene visualizzato.|1.0
|**type**|`"Image"`|Yes|Deve essere `"Image"`.|1.0
|**url**|`string`|Yes|L'URL all'immagine.|1.0
|**id**|`string`| No|Identificatore univoco associato all'elemento.|1.0
|**spacing**|`string`| No|Controlla la quantità di spaziatura tra questo elemento e l'elemento precedente.|1.0
|**separator**|`boolean`| No, predefinito: `false`|Quando `true`, disegnare una linea di separazione nella parte superiore dell'elemento.|1.0


<a name="schema-media"></a>
## <a name="media"></a>Media

Visualizza un lettore multimediale per contenuti audio o video.

#### <a name="introduced-in-version-11"></a>Introdotta nella versione 1.1

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**type**|`"Media"`|Yes|Deve essere `"Media"`.|1.1
|**sources**|`object` `[]`| No|Matrice di origini multimediali per tentare di riprodurre.|1.1
|**poster**|`string`| No|URL di un'immagine da visualizzare prima della visualizzazione.|1.1
|**altText**|`string`| No|Testo alternativo che descrive il file audio o video.|1.1
|**id**|`string`| No|Identificatore univoco associato all'elemento.|1.1
|**spacing**|`string`| No|Controlla la quantità di spaziatura tra questo elemento e l'elemento precedente.|1.1
|**separator**|`boolean`| No, predefinito: `false`|Quando `true`, disegnare una linea di separazione nella parte superiore dell'elemento.|1.1


<a name="schema-mediasource"></a>
## <a name="mediasource"></a>MediaSource

Definisce un'origine per un elemento multimediale

#### <a name="introduced-in-version-11"></a>Introdotta nella versione 1.1

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**mimeType**|`string`|Yes|Il tipo di file multimediali associati MIME (ad esempio `"video/mp4"`).|1.1
|**url**|`string`|Yes|URL di supporto.|1.1


# <a name="containers"></a>Contenitori

<a name="schema-container"></a>
## <a name="container"></a>Contenitore

I contenitori di raggruppano gli elementi.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**type**|`"Container"`|Yes|Deve essere `"Container"`.|1.0
|**items**|`array[]`|Yes|Gli elementi di smart card per il rendering all'interno di `Container`.|1.0
|**selectAction**|`object`| No|Un'azione che verrà richiamato quando il `Container` è selezionato o toccato. `Action.ShowCard` non è supportato.|1.0
|**style**|`string`| No|Hint di stile per `Container`.|1.0
|**verticalContentAlignment**|`string`| No, predefinito: `"top"`|Definisce come il contenuto deve essere allineato verticalmente all'interno del contenitore.|1.1
|**id**|`string`| No|Identificatore univoco associato all'elemento.|1.0
|**spacing**|`string`| No|Controlla la quantità di spaziatura tra questo elemento e l'elemento precedente.|1.0
|**separator**|`boolean`| No, predefinito: `false`|Quando `true`, disegnare una linea di separazione nella parte superiore dell'elemento.|1.0


<a name="schema-columnset"></a>
## <a name="columnset"></a>ColumnSet

ColumnSet divide un'area in colonne, consentendo di elementi per un periodo side-by-side.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**Colonne**|`Column[]`| No|Matrice di `Columns` per dividere la regione in.|1.0
|**selectAction**|`object`| No|Un'azione che verrà richiamato quando il `ColumnSet` è selezionato o toccato. `Action.ShowCard` non è supportato.|1.0
|**type**|`"ColumnSet"`|Yes|Deve essere `"ColumnSet"`.|1.0
|**id**|`string`| No|Identificatore univoco associato all'elemento.|1.0
|**spacing**|`string`| No|Controlla la quantità di spaziatura tra questo elemento e l'elemento precedente.|1.0
|**separator**|`boolean`| No, predefinito: `false`|Quando `true`, disegnare una linea di separazione nella parte superiore dell'elemento.|1.0


<a name="schema-column"></a>
## <a name="column"></a>Column

Definisce un contenitore che fa parte di un set di colonne.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**items**|`array[]`|Yes|Elementi da includere nella smart card di `Column`.|1.0
|**selectAction**|`object`| No|Un'azione che verrà richiamato quando il `Column` è selezionato o toccato. `Action.ShowCard` non è supportato.|1.0
|**style**|`string`| No|Hint di stile per `Column`.|1.0
|**width**|`string,number`| No|`"auto"`, `"stretch"`, o un numero che rappresenta la larghezza relativa della colonna nel gruppo di colonne.|1.0
|**type**|`"Column"`| No|Deve essere `"Column"`.|1.0
|**id**|`string`| No|Identificatore univoco associato all'elemento.|1.0
|**spacing**|`string`| No|Controlla la quantità di spaziatura tra questo elemento e l'elemento precedente.|1.0
|**separator**|`boolean`| No, predefinito: `false`|Quando `true`, disegnare una linea di separazione nella parte superiore dell'elemento.|1.0


<a name="schema-factset"></a>
## <a name="factset"></a>FactSet

L'elemento di FactSet Visualizza una serie di fact (vale a dire le coppie nome/valore) in un formato tabulare.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**facts**|`Fact[]`|Yes|Matrice di `Fact`s.|1.0
|**type**|`"FactSet"`|Yes|Deve essere `"FactSet"`.|1.0
|**id**|`string`| No|Identificatore univoco associato all'elemento.|1.0
|**spacing**|`string`| No|Controlla la quantità di spaziatura tra questo elemento e l'elemento precedente.|1.0
|**separator**|`boolean`| No, predefinito: `false`|Quando `true`, disegnare una linea di separazione nella parte superiore dell'elemento.|1.0


<a name="schema-fact"></a>
## <a name="fact"></a>Fatto

Descrive un Fact in un FactSet come una coppia chiave/valore.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**type**|`"Fact"`| No|&nbsp;|1.0
|**title**|`string`|Yes|Il titolo del fact.|1.0
|**value**|`string`|Yes|Il valore del fact.|1.0


<a name="schema-imageset"></a>
## <a name="imageset"></a>ImageSet

Il ImageSet Visualizza una raccolta di immagini simile a una raccolta.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**images**|`Image[]`|Yes|Matrice di `Image` elementi da visualizzare.|1.0
|**imageSize**|`string`| No, predefinito: `"auto"`|Controlla le dimensioni approssimative dell'immagine. Le dimensioni fisiche possono variare per ogni host. Specificare `"auto"` per la dimensione di immagine true, o `"stretch"` per forzarlo a riempire il contenitore.|1.0
|**type**|`"ImageSet"`|Yes|Deve essere `"ImageSet"`.|1.0
|**id**|`string`| No|Identificatore univoco associato all'elemento.|1.0
|**spacing**|`string`| No|Controlla la quantità di spaziatura tra questo elemento e l'elemento precedente.|1.0
|**separator**|`boolean`| No, predefinito: `false`|Quando `true`, disegnare una linea di separazione nella parte superiore dell'elemento.|1.0


# <a name="actions"></a>Azioni

<a name="schema-action.openurl"></a>
## <a name="actionopenurl"></a>Action.OpenUrl

Quando viene richiamato, visualizzare l'url specificato mediante il relativo avvio in un browser esterno o con in-situ con browser web incorporato.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**type**|`"Action.OpenUrl"`|Yes|Deve essere `"Action.OpenUrl"`.|1.0
|**title**|`string`|Yes|Etichetta pulsante o collegamento che rappresenta questa azione.|1.0
|**iconUrl**|`string`| No|Icona facoltativa da visualizzare sull'azione in combinazione con il titolo|1.1
|**url**|`string`|Yes|URL da aprire.|1.0


<a name="schema-action.submit"></a>
## <a name="actionsubmit"></a>Action.Submit

Raccoglie i campi di input, vengono uniti con il campo dati facoltativi e un evento viene inviato al client. È compito al client di determinare la modalità di elaborazione dati. Ad esempio: Con BotFramework Bot, il client invia un'attività tramite il supporto di messaggistica al bot.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**type**|`"Action.Submit"`|Yes|Deve essere `"Action.Submit"`.|1.0
|**title**|`string`|Yes|Etichetta pulsante o collegamento che rappresenta questa azione.|1.0
|**iconUrl**|`string`| No|Icona facoltativa da visualizzare sull'azione in combinazione con il titolo|1.1
|**data**|`string,object`| No|Dati iniziali che verranno combinati con i campi di input. Si tratta essenzialmente le proprietà 'hidden'.|1.0


<a name="schema-action.showcard"></a>
## <a name="actionshowcard"></a>Action.ShowCard

Definisce un AdaptiveCard mostrata all'utente quando viene scelto il pulsante o collegamento.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**type**|`"Action.ShowCard"`|Yes|Deve essere `"Action.ShowCard"`.|1.0
|**title**|`string`|Yes|Etichetta pulsante o collegamento che rappresenta questa azione.|1.0
|**iconUrl**|`string`| No|Icona facoltativa da visualizzare sull'azione in combinazione con il titolo|1.1
|**card**|`object`|Yes|Elemento radice in una scheda adattiva.|1.0


# <a name="inputs"></a>Input

<a name="schema-input.text"></a>
## <a name="inputtext"></a>Input.Text

Consente a un utente di immettere testo.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**id**|`string`|Yes|Identificatore univoco per il valore. Consente di identificare input raccolti quando viene eseguita l'azione di invio.|1.0
|**isMultiline**|`boolean`| No, predefinito: `false`|Se `true`, consente più righe di input.|1.0
|**maxLength**|`number`| No|Hint di caratteri di lunghezza massima da raccogliere (possono essere ignorati da alcuni client).|1.0
|**placeholder**|`string`| No|Descrizione dell'input desiderato. Quando non è stato alcun testo di input.|1.0
|**style**|`string`| No, predefinito: `"text"`|Hint di stile per `Input.Text`.|1.0
|**type**|`"Input.Text"`|Yes|Deve essere `"Input.Text"`.|1.0
|**value**|`string`| No|Il valore iniziale per questo campo.|1.0
|**spacing**|`string`| No|Controlla la quantità di spaziatura tra questo elemento e l'elemento precedente.|1.0
|**separator**|`boolean`| No, predefinito: `false`|Quando `true`, disegnare una linea di separazione nella parte superiore dell'elemento.|1.0


<a name="schema-input.number"></a>
## <a name="inputnumber"></a>Input.Number

Consente a un utente di immettere un numero.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**id**|`string`|Yes|Identificatore univoco per il valore. Consente di identificare input raccolti quando viene eseguita l'azione di invio.|1.0
|**max**|`number`| No|Hint del valore massimo (possono essere ignorati da alcuni client).|1.0
|**min**|`number`| No|Hint del valore minimo (possono essere ignorati da alcuni client).|1.0
|**placeholder**|`string`| No|Descrizione dell'input desiderato. Quando non è stata effettuata alcuna selezione.|1.0
|**type**|`"Input.Number"`|Yes|Deve essere `"Input.Number"`.|1.0
|**value**|`number`| No|Valore iniziale per questo campo.|1.0
|**spacing**|`string`| No|Controlla la quantità di spaziatura tra questo elemento e l'elemento precedente.|1.0
|**separator**|`boolean`| No, predefinito: `false`|Quando `true`, disegnare una linea di separazione nella parte superiore dell'elemento.|1.0


<a name="schema-input.date"></a>
## <a name="inputdate"></a>Input.Date

Consente a un utente di scegliere una data.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**id**|`string`|Yes|Identificatore univoco per il valore. Consente di identificare input raccolti quando viene eseguita l'azione di invio.|1.0
|**max**|`string`| No|Hint del valore massimo, espresso in formato ISO 8601 (possono essere ignorati da alcuni client).|1.0
|**min**|`string`| No|Hint del valore minimo espresso nel formato ISO 8601 (possono essere ignorati da alcuni client).|1.0
|**placeholder**|`string`| No|Descrizione dell'input desiderato. Quando non è stata effettuata alcuna selezione.|1.0
|**type**|`"Input.Date"`|Yes|Deve essere `"Input.Date"`.|1.0
|**value**|`string`| No|Il valore iniziale per questo campo viene espresso nel formato ISO-8601.|1.0
|**spacing**|`string`| No|Controlla la quantità di spaziatura tra questo elemento e l'elemento precedente.|1.0
|**separator**|`boolean`| No, predefinito: `false`|Quando `true`, disegnare una linea di separazione nella parte superiore dell'elemento.|1.0


<a name="schema-input.time"></a>
## <a name="inputtime"></a>Input.Time

Consente a un utente di selezionare un'ora.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**id**|`string`|Yes|Identificatore univoco per il valore. Consente di identificare input raccolti quando viene eseguita l'azione di invio.|1.0
|**max**|`string`| No|Hint del valore massimo (possono essere ignorati da alcuni client).|1.0
|**min**|`string`| No|Hint del valore minimo (possono essere ignorati da alcuni client).|1.0
|**placeholder**|`string`| No|Descrizione dell'input desiderato. Quando non è stato selezionato alcun tempo.|1.0
|**type**|`"Input.Time"`|Yes|Deve essere `"Input.Time"`.|1.0
|**value**|`string`| No|Il valore iniziale per questo campo viene espresso nel formato ISO-8601.|1.0
|**spacing**|`string`| No|Controlla la quantità di spaziatura tra questo elemento e l'elemento precedente.|1.0
|**separator**|`boolean`| No, predefinito: `false`|Quando `true`, disegnare una linea di separazione nella parte superiore dell'elemento.|1.0


<a name="schema-input.toggle"></a>
## <a name="inputtoggle"></a>Input.Toggle

Consente a un utente di scegliere tra due opzioni.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**id**|`string`|Yes|Identificatore univoco per il valore. Consente di identificare input raccolti quando viene eseguita l'azione di invio.|1.0
|**title**|`string`|Yes|Titolo per l'elemento toggle|1.0
|**type**|`"Input.Toggle"`|Yes|Input.Toggle|1.0
|**value**|`string`| No, predefinito: `"false"`|Il valore corrente selezionato. Se si seleziona l'elemento che verrà utilizzato "valueOn", "valueOff" in caso contrario,|1.0
|**valueOff**|`string`| No, predefinito: `"false"`|Il valore quando si attiva/disattiva è disattivato|1.0
|**valueOn**|`string`| No, predefinito: `"true"`|Il valore quando il controllo è attivato|1.0
|**spacing**|`string`| No|Controlla la quantità di spaziatura tra questo elemento e l'elemento precedente.|1.0
|**separator**|`boolean`| No, predefinito: `false`|Quando `true`, disegnare una linea di separazione nella parte superiore dell'elemento.|1.0


<a name="schema-input.choiceset"></a>
## <a name="inputchoiceset"></a>Input.ChoiceSet

Consente a un utente di immettere una scelta.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**choices**|`Input.Choice[]`|Yes|`Choice` Opzioni.|1.0
|**id**|`string`|Yes|Identificatore univoco per il valore. Consente di identificare input raccolti quando viene eseguita l'azione di invio.|1.0
|**isMultiSelect**|`boolean`| No, predefinito: `false`|Consente di scegliere tra diverse opzioni da selezionare.|1.0
|**style**|`string`| No, predefinito: `"compact"`|Hint di stile per `Input.ChoiceSet`.|1.0
|**type**|`"Input.ChoiceSet"`|Yes|Deve essere `"Input.ChoiceInput"`.|1.0
|**value**|`string`| No|La scelta iniziale (o il set di scelte) che deve essere selezionata. Per la selezione multipla, specificare una stringa di valori delimitati da virgole.|1.0
|**spacing**|`string`| No|Controlla la quantità di spaziatura tra questo elemento e l'elemento precedente.|1.0
|**separator**|`boolean`| No, predefinito: `false`|Quando `true`, disegnare una linea di separazione nella parte superiore dell'elemento.|1.0


<a name="schema-input.choice"></a>
## <a name="inputchoice"></a>Input.Choice

Descrive una scelta per l'uso in un ChoiceSet.

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**type**|`"Input.Choice"`| No|&nbsp;|1.0
|**title**|`string`|Yes|Testo da visualizzare.|1.0
|**value**|`string`|Yes|Il valore non elaborato per la scelta. **Nota:** non utilizzare un `,` nel valore, poiché un `ChoiceSet` con `isMultiSelect` impostato su `true` restituisce una stringa delimitata da virgole di valori di scelta.|1.0
