---
title: Implementazione di un renderer
author: matthidinger
ms.author: mahiding
ms.date: 09/15/2017
ms.topic: article
ms.openlocfilehash: 607ce40e70e0e54e61a572853a521d2dd70a5c23
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454914"
---
# <a name="adaptive-card-renderer-specification"></a>Specifica relativa al renderer di schede adattive

La specifica seguente illustra come implementare un renderer di schede adattive in qualsiasi piattaforma di interfaccia utente.

> [!IMPORTANT]
> 
> Questo contenuto non è ancora definitivo. Torna a breve.

## <a name="sdk-versioning"></a>Controllo delle versioni dell'SDK

1. La versione principale e quella secondaria dell'SDK **DOVREBBERO** corrispondere alla versione di `schema`. 
1. La patch/build **DOVREBBE** essere usata per gli aggiornamenti del renderer che non prevedono modifiche relative allo schema.

## <a name="parsing-json"></a>Analisi del contenuto JSON

### <a name="error-conditions"></a>Condizioni di errore
1. Un parser **DEVE** verificare che si tratti di contenuto JSON valido
1. Un parser **DEVE** eseguire la convalida a fronte dello schema (proprietà obbligatorie e così via)
1. Gli errori sopra riportati **DEVONO** essere segnalati all'app host (eccezione o equivalente)

### <a name="unknown-types"></a>Tipi sconosciuti
1. Se vengono rilevati "tipi" sconosciuti, questi **DEVONO ESSERE ELIMINATI** dal risultato
1. Eventuali modifiche del payload (come nei casi sopra indicati) **DOVREBBERO** essere segnalate come avvisi all'app host

### <a name="unknown-properties"></a>Proprietà sconosciute
1. Un parser **DEVE** includere proprietà **aggiuntive** per gli elementi

### <a name="additional-considerations"></a>Altre considerazioni
1. La proprietà `speak` può contenere markup SSML e **DEVE** essere restituita all'app host come specificato

## <a name="parsing-host-config"></a>Analisi della configurazione host
1. TODO

## <a name="versioning"></a>Controllo versioni

1. Un renderer **DEVE** implementare una determinata versione dello schema. 
1. Il costruttore `AdaptiveCard`**DEVE** assegnare alla proprietà `version` un valore predefinito in base alla versione corrente dello schema. 
1. Se un renderer rileva una proprietà `version` nell'oggetto `AdaptiveCard` con un valore superiore alla versione supportata, **DEVE** invece restituire l'oggetto `fallbackText`.

## <a name="rendering"></a>Rendering

Un oggetto `AdaptiveCard` è costituito da un oggetto `body` e da `actions`. L'oggetto `body` è una raccolta di `CardElement` di cui un renderer eseguirà l'enumerazione e il rendering nell'ordine. 

1. Ogni elemento **DEVE** estendersi per la larghezza del relativo elemento padre (pensa a `display: block` in HTML).
1. Un renderer **DEVE** ignorare i tipi di elemento sconosciuti e continuare a eseguire il rendering del resto del payload.

### <a name="spacing-and-separators"></a>Spaziatura e separatori

1. La proprietà `spacing` di ogni elemento influisce sulla quantità di spazio tra l'elemento **CORRENTE** e quello **PRECEDENTE**.
1. La spaziatura **DEVE ESSERE APPLICATA SOLO** quando esiste effettivamente un elemento precedente. Ad esempio, non si applica al primo elemento di una matrice.
1. Un renderer **DEVE** cercare la quantità di spazio da usare dalla spaziatura di `hostConfig` per il valore di enumerazione applicato all'elemento corrente.
1. Se l'elemento ha un valore `separator` impostato su `true`, **DEVE** essere tracciata una linea visibile tra l'elemento corrente e quello che lo precede.
1. La linea di separazione **DEVE** essere tracciata con `container.style.default.foregroundColor`.
1. Un separatore **DEVE ESSERE TRACCIATO SOLO** se l'elemento **NON È** il primo della matrice.

### <a name="columns"></a>Colonne

1. La proprietà `width` di un elemento `Column` **DEVE** essere interpretata da "auto", "stretch" o un rapporto ponderato.

### <a name="textblock"></a>TextBlock

1. Un oggetto TextBlock **DEVE** occupare un'unica riga, tranne quando la proprietà `wrap` è impostata su `true`. 
1. Il blocco di testo **DOVREBBE** tagliare l'eventuale testo in eccesso con i puntini di sospensione (...)

#### <a name="markdown"></a>Markdown

1. Le schede adattive consentono l'uso di un sottoinsieme del markdown e **DOVREBBE** essere fornito il supporto in `TextBlock`. 
1. Vedi i [requisiti di markdown](../authoring-cards/text-features.md) completi.

#### <a name="formatting-functions"></a>Funzioni di formattazione

1. `TextBlock` consente l'uso di [funzioni di formattazione DATE/TIME](../authoring-cards/text-features.md) che **DEVONO** essere supportate in ogni renderer.
1. **TUTTI GLI ERRORI DEVONO** visualizzare la stringa non elaborata nella scheda. Non vengono usati messaggi descrittivi perché l'obiettivo è quello di far comprendere immediatamente il problema allo sviluppatore.

1. TODO: includi regex.

### <a name="images"></a>Immagini

1. Un renderer **DOVREBBE** consentire alle app host di rilevare quando tutte le immagini HTTP sono state scaricate ed è stato "eseguito il rendering completo" della scheda
1. Un renderer **DEVE** controllare il parametro `maxImageSize` della configurazione host durante il download delle immagini HTTP
1. Un renderer **DEVE** supportare `.png` e `.jpeg`
1. Un renderer **DOVREBBE** supportare le immagini `.gif`

### <a name="host-config"></a>Configurazione dell'host

* TODO: quali dovrebbero essere le impostazioni predefinite? La condivisione dovrebbe essere totale? È necessario incorporare un file hostConfig.json comune nei dati binari?
* TODO: è necessario applicare il controllo delle versioni anche di HostConfig per l'analisi?

[`HostConfig`](host-config.md) è un oggetto di configurazione condivisa che specifica il modo in cui un renderer di schede adattive genera l'interfaccia utente.  

Ciò consente di condividere le proprietà indipendenti dalla piattaforma tra i renderer in piattaforme e dispositivi diversi. Consente inoltre di creare strumenti che danno un'idea dell'aspetto che avrebbe la scheda per un determinato ambiente.

1. I renderer **DEVONO** esporre un parametro di **configurazione host** alle app host
1. Tutti gli elementi **DEVONO** avere uno stile in base alle rispettive impostazioni di configurazione host

### <a name="native-platform-styling"></a>Applicazione di stili della piattaforma nativa

1. Ogni tipo di elemento **DOVREBBE** associare uno stile della piattaforma nativa all'elemento generato dell'interfaccia utente. Ad esempio, in HTML è stata aggiunta una classe CSS ai tipi di elemento e in XAML viene assegnato uno stile specifico.

## <a name="extensibility"></a>Estendibilità 

1. Un renderer **DEVE** consentire alle app host di eseguire l'override dei renderer di elementi predefiniti, ad esempio sostituire il rendering di `TextBlock` con la propria logica.
1. Un renderer **DEVE** consentire alle app host di registrare tipi di elementi personalizzati, ad esempio aggiungere il supporto per un elemento `Rating` personalizzato.
1. Un renderer **DEVE** consentire alle app host di rimuovere il supporto per un elemento predefinito, ad esempio rimuovere `Action.Submit` se non vogliono che sia supportato.

## <a name="actions"></a>Azioni

1. Se la proprietà `supportsInteractivity` di HostConfig è `false`, un renderer **NON DEVE** eseguire il rendering di alcuna azione.
1. La proprietà `actions`**DEVE** essere sottoposta a rendering come pulsanti in una specie di barra delle azioni, in genere nella parte inferiore della scheda. 
1. Quando un pulsante viene toccato, **DEVE** consentire all'app host di gestire l'evento. 
1. L'evento **DEVE** passare tutte le proprietà associate con l'azione.
1. L'evento **DEVE** passare l'oggetto `AdaptiveCard` che è stato eseguito.

Azione | Comportamento
--- | ---
**Action.OpenUrl** | Apre un URL esterno per la visualizzazione
**Action.ShowCard** | Richiede che una scheda secondaria venga visualizzata all'utente.
**Action.Submit** | Richiede la raccolta di tutti gli elementi di input in un oggetto che ti viene quindi inviato tramite un metodo definito dall'applicazione host.

### <a name="actionopenurl"></a>Action.OpenUrl
1. `Action.OpenUrl` **DOVREBBE** aprire un URL usando il meccanismo della piattaforma nativa.
1. Se questo non è possibile, **DEVE** generare un evento nell'app host per gestire l'apertura dell'URL. Questo evento **DEVE** consentire all'app host di eseguire l'override del comportamento predefinito, ad esempio consentire l'apertura dell'URL all'interno della rispettiva app.

### <a name="actionshowcard"></a>Action.ShowCard

1. L'azione `Action.ShowCard` **DEVE** essere supportata in qualche modo, in base all'impostazione di hostConfig. Sono disponibili due modalità: inline e popup. Le schede inline **DOVREBBERO** attivare/disattivare la visibilità della scheda automaticamente. In modalità popup **DOVREBBE** essere generato un evento nell'app host per mostrare la scheda in qualche modo.

### <a name="actionsubmit"></a>Action.Submit

L'azione di invio si comporta come l'invio di un modulo HTML, ad eccezione del fatto che, quando il codice HTML in genere attiva un post HTTP, le schede adattive lasciano a ogni app host la possibilità di determinare il significato di "inviare". 

1. Quando **DEVE** essere generato un evento, l'utente tocca l'azione richiamata.  
1. La proprietà `data`**DEVE** essere inclusa nel payload di callback.
1. Per `Action.Submit`, un renderer **DEVE** raccogliere tutti gli input nella scheda e recuperare i relativi valori. 

### <a name="selectaction"></a>selectAction

1. Se la proprietà `supportedInteractivity` di Host Config è `false`, `selectAction` **NON DEVE** soggetta a rendering come destinazione del tocco.
1. `Image`, `ColumnSet` e `Column` offrono una proprietà `selectAction` che **DOVREBBE** essere eseguita quando l'utente la richiama, ad esempio toccando l'elemento.

## <a name="inputs"></a>Input

1. Se la proprietà `supportsInteractivity` di HostConfig è `false`, un renderer **NON DEVE** eseguire il rendering di alcun input.
2. Gli input **DOVREBBERO** essere sottoposti a rendering con la massima fedeltà possibile. Ad esempio, un oggetto `Input.Date` idealmente offre una selezione data a un utente, ma se questo non è possibile nello stack dell'interfaccia utente, il renderer **DEVE** eseguire il fallback al rendering di una casella di testo standard.
3. Un renderer **DOVREBBE** visualizzare l'oggetto `placeholderText`, se possibile.
4. **NON** è necessario che un renderer implementi la convalida dell'input. Gli utenti di schede adattive devono pianificare la convalida dei dati ricevuti sul loro lato.
5. L'associazione del valore di input **DEVE** essere preceduta adeguatamente da caratteri di escape.

6. L'oggetto **DEVE** essere restituito all'app host come segue:

   Non viene eseguita alcuna promessa di convalida dell'input nelle schede adattive, pertanto spetta alla parte ricevente analizzare correttamente la risposta. Ad esempio, Input.Number potrebbe restituire "hello" ed è necessario essere preparati in tal senso.


## <a name="events"></a>Eventi

1. Un renderer **DOVREBBE** generare un evento quando la visibilità di un elemento è cambiata, consentendo all'app host di scorrere la scheda in posizione.
