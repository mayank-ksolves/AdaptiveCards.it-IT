---
title: Implementazione di un Renderer
author: matthidinger
ms.author: mahiding
ms.date: 09/15/2017
ms.topic: article
ms.openlocfilehash: b39493f82f3378e5a554abc6df890d6821869671
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2019
ms.locfileid: "67138024"
---
# <a name="adaptive-card-renderer-specification"></a>Specifica del Renderer scheda adattiva

La specifica seguente viene descritto come implementare un renderer scheda adattiva in qualsiasi piattaforma dell'interfaccia utente.

> [!IMPORTANT]
> 
> Questo contenuto non è ancora stato completato. Ricontrollare a breve.

## <a name="sdk-versioning"></a>Controllo delle versioni SDK

1. La versione del SDK major e minor **SHOULD** corrispondere il `schema` versione. 
1. Patch/build **SHOULD** essere usato per gli aggiornamenti di renderer che non hanno le modifiche dello schema.

## <a name="parsing-json"></a>L'analisi JSON

### <a name="error-conditions"></a>Condizioni di errore
1. Un parser **necessario** che sia contenuto JSON valido
1. Un parser **necessario** convalidare a fronte dello schema (proprietà obbligatorie e così via)
1. Gli errori citati **necessario** segnalati per l'app host (un'eccezione o equivalente)

### <a name="unknown-types"></a>Tipi sconosciuti
1. Se vengono rilevati sconosciuti "tipi" essi **devono essere eliminati** dal risultato
1. Modifiche del payload (come sopra) **SHOULD** siano segnalati come avvisi per l'applicazione host

### <a name="unknown-properties"></a>Proprietà sconosciute
1. Un parser **devono** includono **aggiuntive** sulle proprietà degli elementi

### <a name="additional-considerations"></a>Considerazioni aggiuntive
1. Il `speak` proprietà contenga il markup SSML e **necessario** restituito all'app host come specificata

## <a name="parsing-host-config"></a>L'analisi di configurazione di Host
1. TODO

## <a name="versioning"></a>Controllo delle versioni

1. Un renderer **necessario** implementare una particolare versione dello schema. 
1. Il `AdaptiveCard` costruttore **necessario** assegnare il `version` proprietà valore predefinito è basato sulla versione corrente dello schema 
1. Se viene rilevato un renderer di un `version` proprietà nel `AdaptiveCard` che è superiore alla versione supportata, viene **deve** restituiscono il `fallbackText` invece.

## <a name="rendering"></a>Per il rendering

Un' `AdaptiveCard` è costituito da un `body` e `actions`. Il `body` è una raccolta di `CardElement`che un renderer enumererà ed eseguire il rendering in ordine. 

1. Ogni elemento **devono** stretch per la larghezza dell'elemento padre (pensare `display: block` in formato HTML).
1. Un renderer **necessario** ignorano i tipi di elemento sconosciuto e continuare il resto del payload di rendering.

### <a name="spacing-and-separators"></a>Spaziatura e separatori

1. Il `spacing` proprietà su ogni elemento influisce sulla quantità di spazio tra il **corrente** elemento e quello **BEFORE** è.
1. Spaziatura **devono solo** applicare se si è effettivamente un elemento che la precede. (Ad esempio, non verranno applicati al primo elemento in una matrice)
1. Un renderer **devono** cercare la quantità di spazio da utilizzare dal `hostConfig` spaziatura per il valore di enumerazione applicato all'elemento corrente.
1. Se l'elemento ha un `separator` pari a `true`, quindi una riga visibile **necessario** separazione tra l'elemento corrente e quella prima di esso.
1. La linea di separazione **devono** essere disegnata usando il `container.style.default.foregroundColor`.
1. Un separatore **devono solo** da disegnare se l'elemento **non è** il primo elemento nella matrice.

### <a name="columns"></a>Colonne

1. `Column` `width` **È necessario** essere interpretata dalle "auto", "stretch" o un rapporto ponderato.

### <a name="textblock"></a>TextBlock

1. Un elemento TextBlock **devono** occupano una singola riga, a meno che il `wrap` è di proprietà `true`. 
1. Il blocco di testo **SHOULD** tagliare il testo in eccesso con i puntini di sospensione (...)

#### <a name="markdown"></a>Markdown

1. Le schede adattive consentono un sottoinsieme di Markdown e **SHOULD** supportata in `TextBlock`. 
1. Vedere completi [requisiti markdown](../authoring-cards/text-features.md)

#### <a name="formatting-functions"></a>Le funzioni di formattazione

1. `TextBlock` Consente [funzioni di formattazione di data/ora](../authoring-cards/text-features.md) che **necessario** siano supportate in ogni renderer.
1. **TUTTI gli errori devono** visualizzare la stringa non elaborata nella scheda. Nessun messaggio descrittivo tentato. (L'obiettivo a rendere lo sviluppatore consapevole immediatamente si è verificato un problema)

1. TODO: Includere espressioni regolari

### <a name="images"></a>Immagini

1. Un renderer **SHOULD** consentire l'hosting di App di sapere quando sono state scaricate tutte le immagini HTTP e la scheda è "completamente il rendering di"
1. Un renderer **devono** ispezionare la configurazione Host `maxImageSize` param durante il download delle immagini HTTP
1. Un renderer **devono** supportano `.png` e `.jpeg`
1. Un renderer **SHOULD** supportano `.gif` immagini

### <a name="host-config"></a>Configurazione dell'host

* TODO: Quale dovrebbero essere i valori predefiniti? Dovrebbe condividono tutti lo? Dovremmo si incorpora un file hostConfig.json comune nei file binari?
* TODO: Ritengo che HostConfig deve essere eseguito anche per l'analisi?

[`HostConfig`](host-config.md) è un oggetto di configurazione condivisa che specifica la modalità di generazione dell'interfaccia utente in un Renderer scheda adattiva.  

In questo modo le proprietà che sono indipendenti dalla piattaforma per la condivisione tra i renderer su diverse piattaforme e dispositivi. Consente inoltre gli strumenti da creare che ti offre un'idea dell'aspetto che scheda sarebbe necessario per un determinato ambiente.

1. I renderer **devono** esporre una **Host Config** parametro per ospitare App
1. Tutti gli elementi **necessario** applicare stili in base a delle rispettive impostazioni di configurazione di Host

### <a name="native-platform-styling"></a>Stile di piattaforma nativa

1. Ogni tipo di elemento **SHOULD** allegare uno stile di piattaforma nativa con l'elemento dell'interfaccia utente generato. Ad esempio, in formato HTML è stata aggiunta una classe CSS per i tipi di elemento e in XAML è assegnare uno stile specifico.

## <a name="extensibility"></a>Estendibilità 

1. Un renderer **necessario** consentire l'hosting delle App eseguire l'override di renderer di elemento predefinito. Ad esempio, sostituire `TextBlock` esegue il rendering con la propria logica.
1. Un renderer **necessario** consentire l'hosting delle App registrare i tipi di elemento personalizzati. Ad esempio, aggiungere il supporto per un oggetto personalizzato `Rating` elemento
1. Un renderer **necessario** consentire alle App host di rimuovere il supporto per un elemento predefinito. Ad esempio, rimuovere `Action.Submit` se si preferisce non supportata.

## <a name="actions"></a>Azioni

1. Se HostConfig `supportsInteractivity` viene `false`, un renderer **non deve** eseguire il rendering di eventuali azioni.
1. Il `actions` proprietà **necessario** sottoposta a rendering come pulsanti nello stesso tipo di barra delle azioni, in genere nella parte inferiore della scheda. 
1. Quando si tocca un pulsante viene **necessario** consentire all'app di host gestire l'evento. 
1. L'evento **necessario** pass lungo tutte le relative proprietà con l'azione
1. L'evento **devono** passano il `AdaptiveCard` quale è stato eseguito

Azione | Comportamento
--- | ---
**Action.OpenUrl** | Aprire un URL esterno per la visualizzazione
**Action.ShowCard** | Richiede una carta secondari da visualizzare all'utente.
**Action.Submit** | Porre per tutti gli elementi di input di raccogliere in un oggetto che viene quindi inviato all'utente tramite un metodo definito dall'applicazione host.

### <a name="actionopenurl"></a>Action.OpenUrl
1. `Action.OpenUrl` **DOVREBBE** aprire un URL usando il meccanismo di piattaforma nativa
1. Se questo non è possibile **necessario** generare un evento per l'applicazione host per gestire aprendo l'URL. Questo evento **necessario** consentire all'app di host eseguire l'override del comportamento predefinito. Ad esempio, consentendogli di aprire l'URL interno le proprie app.

### <a name="actionshowcard"></a>Action.ShowCard

1. `Action.ShowCard` **È necessario** supportato in qualche modo, in base all'impostazione hostConfig. Sono disponibili due modalità: inline e finestra popup. Le schede inline **SHOULD** attivare/disattivare la visibilità di smart card automaticamente. In modalità finestra popup, un evento **SHOULD** generato per l'app host venga visualizzata la scheda in qualche modo.

### <a name="actionsubmit"></a>Action.Submit

L'azione di invio si comporta come un invio di form HTML, ad eccezione del fatto che in cui in genere HTML attiva una richiesta post HTTP, le schede adattive lasciandolo fino a ogni app host di determinare quali "Invia" significa che a loro. 

1. Quando ciò **necessario** generare un evento a cui l'utente tocca l'azione richiamata.  
1. Il `data` proprietà **necessario** da includere nel payload del callback.
1. Per la `Action.Submit`, un renderer **necessario** raccogliere tutti gli input della scheda e recuperare i valori. 

### <a name="selectaction"></a>selectAction

1. Se Host Config `supportedInteractivity` viene `false` un' `selectAction` **non deve** sottoposti a rendering come una destinazione di tocco.
1. `Image`, `ColumnSet`, e `Column` offrono una `selectAction` proprietà, quali **SHOULD** da eseguire quando l'utente richiama, ad esempio, toccare l'elemento.

## <a name="inputs"></a>Input

1. Se HostConfig `supportsInteractivity` viene `false` un renderer **non deve** eseguire il rendering di alcun input.
2. Gli input **SHOULD** rendering con la massima fedeltà possibili. Ad esempio, un' `Input.Date` offrirebbe idealmente un controllo selezione data a un utente, ma se questo non è possibile lo stack di interfaccia utente, quindi il renderer **necessario** il fallback al rendering di una casella di testo standard.
3. Un renderer **SHOULD** visualizzare il `placeholderText` se possibile
4. Un renderer **non implica** disporre implementare la convalida dell'input. Gli utenti delle schede adattive devono pianificare convalidare tutti i dati ricevuti estremità.
5. Associazione del valore di input **necessario** utilizzare correttamente caratteri di escape

6. L'oggetto **necessario** da restituire per l'applicazione host come segue:

   È non apportare qualsiasi promesse di convalida dell'input nelle schede adattive, in modo che spetta alla parte ricevente per analizzare correttamente la risposta. Ad esempio, un Input.Number potrebbe restituire "hello" e devono essere preparati per che.


## <a name="events"></a>Events

1. Un renderer **SHOULD** generare un evento quando la visibilità di un elemento è stato modificato, consentendo all'app di host scorrere la scheda nella posizione desiderata.
