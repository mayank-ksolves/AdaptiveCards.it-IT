---
title: Servizio modelli di Schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 8ccccd3c3e67324acf123e03b947372e1517faab
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454984"
---
# <a name="adaptive-cards-template-service"></a>Servizio modelli di Schede adattive

Il servizio modelli di Schede adattive è un modello di verifica che consente a chiunque di trovare, contribuire e condividere un set di modelli ben noti.

È utile se vuoi visualizzare alcuni dati senza dover scrivere per questo una scheda adattiva personalizzata.

> Per una [panoramica della creazione di modelli di schede adattive](index.md), leggi l'argomento specifico.

> [!IMPORTANT] 
> 
> *Condizioni e contratto* 
> 
> Questo servizio di **livello alfa** viene fornito "com'è", inclusi tutti gli errori, e non è supportato in alcun modo. I dati raccolti dal servizio sono soggetti alle disposizioni dell'[Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkID=824704).
> 
> Queste funzionalità sono disponibili **in anteprima e sono soggette a modifiche**. Il tuo feedback non solo è apprezzato, ma è anche fondamentale per aiutarci a offrire le funzionalità di cui **tu** hai bisogno.

## <a name="how-does-the-service-help-me"></a>In che modo può essere utile il servizio?

Supponiamo di aver ricevuto dall'interno dell'organizzazione alcuni dati, ad esempio dati finanziari, di Microsoft Graph, di schema.org o personalizzati. 

Ora vogliamo visualizzare questi dati per un utente. 

Di norma è necessario scrivere codice di interfaccia utente personalizzato in tutti gli stack front-end che vengono recapitati agli utenti finali.

Supponiamo invece che esista un ambiente in cui la nostra app sia in grado di "apprendere" nuovi modelli di interfaccia utente in base al tipo di dati. In questo ambiente ognuno può aggiungere contributi, migliorare e condividere modelli di interfaccia utente comuni, all'interno di progetti specifici, all'interno di un'organizzazione o per l'intera rete Internet.

## <a name="what-is-the-card-template-service"></a>Che cos'è il servizio modelli di schede?

Il servizio modelli di schede è un semplice endpoint REST che consente di:

* **Trovare** un modello analizzando la struttura dei dati
* **Ottenere** un modello in modo da poterlo associare direttamente nel client, *senza inviare i dati al server o uscire dal dispositivo*
* **Popolare** un modello nel server, quando il binding dei dati sul lato client non è appropriato o possibile

Alla base di tutto:

* È presente un repository di modelli open source condiviso, supportato da GitHub. *Il repository è attualmente privato, ma sarà reso pubblico appena avremo risolto alcune questioni rimaste in sospeso.*
* Tutti i modelli presenti nel repository sono file JSON flat, pertanto le modifiche, l'aggiunta di contributi e le condivisioni possono essere effettuate con naturalezza durante il flusso di lavoro di uno sviluppatore.
* Il codice sarà reso disponibile in modo da poter ospitare il servizio ovunque ritieni che sia più appropriato. 

## <a name="using-the-service"></a>Uso del servizio

### <a name="get-all-templates"></a>Ottenere tutti i modelli 

Questo endpoint restituisce un elenco di tutti i modelli noti.

> `HTTP GET https://templates.adaptivecards.io/list`

**Estratto della risposta**

```json
{
  "graph.microsoft.com": {
    "templates": [
      {
        "file": "Files.json",
        "fullPath": "graph.microsoft.com/Files.json"
      },
      {
        "file": "Profile.json",
        "fullPath": "graph.microsoft.com/Profile.json"
      }
   ]
}
```

### <a name="find-a-template"></a>Trovare un modello

Questo endpoint cerca di trovare un modello analizzando la struttura dei dati.

> `HTTP POST https://templates.adaptivecards.io/find`

#### <a name="example"></a>Esempio

Supponiamo di aver appena eseguito l'accesso a un endpoint di [Microsoft Graph](https://graph.microsoft.com) per ottenere i dati dell'organizzazione che ci riguardano.

> `HTTP GET https://graph.microsoft.com/v1.0/me/`

![Screenshot di Graph Explorer](content/2019-08-01-12-08-13.png)

L'API restituisce **dati JSON**, ma in che modo possono essere **visualizzati** per gli utenti che usano Schede adattive? 

Prima vediamo se è presente un modello per lo specifico tipo di dati. Inviamo pertanto una richiesta HTTP all'endpoint `/find` con i nostri dati in `POST body`.

```
HTTP POST https://templates.adaptivecards.io/find

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users/$entity",
    "businessPhones": [
        "+1 412 555 0109"
    ],
    "displayName": "Megan Bowen",
    "givenName": "Megan",
    "jobTitle": "Auditor",
    "mail": "MeganB@M365x214355.onmicrosoft.com",
    "mobilePhone": null,
    "officeLocation": "12/1110",
    "preferredLanguage": "en-US",
    "surname": "Bowen",
    "userPrincipalName": "MeganB@M365x214355.onmicrosoft.com",
    "id": "48d31887-5fad-4d73-a9f5-3c356e68a038"
}
```

**Risposta:**

```json
[
  {
    "templateUrl": "graph.microsoft.com/Profile.json",
    "confidence": 1
  }
]
```

Il servizio restituisce un elenco di tutti i modelli corrispondenti, insieme a un valore `confidence` che indica il livello di corrispondenza. Ora possiamo usare l'URL del modello per **ottenere** il modello o **popolarlo** sul lato server.

### <a name="get-a-template"></a>Ottenere un modello

Un modello recuperato da questo endpoint può essere popolato con i dati in fase di esecuzione [usando gli SDK di creazione modelli](sdk.md).

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]`

Nel modello puoi includere anche dati di esempio, in modo da rendere più intuitive le operazioni di modifica nella finestra di progettazione:

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]?sampleData=true`

#### <a name="example"></a>Esempio

Proviamo a ottenere il modello di profilo di Microsoft Graph restituito dall'operazione `/find` precedente.

`HTTP GET https://templates.adaptivecards.io/graph.microsoft.com/Profile.json`

**Estratto della risposta**

```json
{
  "type": "AdaptiveCard",
  "version": "1.0",
  "body": [
    {
      "type": "TextBlock",
      "size": "Medium",
      "weight": "Bolder",
      "text": "{name}"
    },
    {
        // ...snip
    }
  ]
}
```

Usa ora questo modello con gli [SDK per la creazione di modelli](sdk.md) per creare una scheda adattiva pronta per il rendering.

### <a name="populate-a-template-server-side"></a>Popolare un modello sul lato server

In alcuni casi potrebbe non essere opportuno popolare un modello nel client.  Per questi casi d'uso è possibile fare in modo che il servizio restituisca una scheda adattiva completamente popolata, pronta per essere passata a qualsiasi renderer di schede adattive.

> `HTTP POST https://templates.adaptivecards.io/[TEMPLATE-PATH]`

#### <a name="example"></a>Esempio

Proviamo a popolare il modello di profilo di Microsoft Graph restituito dall'operazione `/find` usando i dati precedenti.

```
HTTP POST https://templates.adaptivecards.io/graph.microsoft.com/Profile.json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users/$entity",
    "businessPhones": [
        "+1 412 555 0109"
    ],
    "displayName": "Megan Bowen",
    "givenName": "Megan",
    "jobTitle": "Auditor",
    "mail": "MeganB@M365x214355.onmicrosoft.com",
    "mobilePhone": null,
    "officeLocation": "12/1110",
    "preferredLanguage": "en-US",
    "surname": "Bowen",
    "userPrincipalName": "MeganB@M365x214355.onmicrosoft.com",
    "id": "48d31887-5fad-4d73-a9f5-3c356e68a038"
}
```

**Estratto della risposta**

```json
{
  "type": "AdaptiveCard",
  "version": "1.0",
  "body": [
    {
      "type": "TextBlock",
      "size": "Medium",
      "weight": "Bolder",
      "text": "Megan Bowen"
    },
    {
        // ...snip
    }
  ]
}
```

Si noti come la risposta ha sostituito il testo del primo `TextBlock` con `"Megan Bowen"` anziché `"{name}"` come nella richiesta `GET`. È ora possibile passare questa scheda adattiva a qualsiasi renderer di schede adattive senza dover creare modelli sul lato client.

## <a name="contributing-templates"></a>Aggiunta di contributi ai modelli

Il servizio modelli è supportato da un repository GitHub che attualmente è **privato**, ma che diventerà open source una volta risolte alcune questioni rimaste in sospeso.

Usando GitHub come archivio di backup per i modelli, ci auguriamo di poter "democratizzare" il processo di creazione, miglioramento e condivisione dei modelli. Chiunque può inviare una richiesta pull con un modello completamente nuovo o apportare miglioramenti ai modelli esistenti, tutto all'interno dell'esperienza di GitHub adatta per gli sviluppatori.

## <a name="self-hosting-the-service"></a>Test interno del servizio

Non tutti i tipi di dati sono adatti per il servizio modelli "centrale" di Schede adattive ospitato all'indirizzo `https://templates.adaptivecards.io`. 

Vogliamo assicurarci che chiunque possa ospitare il servizio modelli all'interno di un'organizzazione. Verrà pertanto reso disponibile il codice sorgente e faremo in modo che possa essere distribuito con estrema facilità in Azure o in un sistema back-end.

Saranno presto disponibili altre informazioni su questo argomento.