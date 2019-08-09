---
title: Servizio modello schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 81d1e598b6157b6ba1fedbf458a7c624705afcd5
ms.sourcegitcommit: a16f53ba10a8607deacde5c8cc78927cac58657c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68878888"
---
# <a name="adaptive-cards-template-service"></a>Servizio modello schede adattive

Il servizio modello schede adattive è un servizio di prova che consente a chiunque di trovare, contribuire e condividere un set di modelli noti.

È utile se si desidera visualizzare alcuni dati, ma non si desidera preoccuparsi di scrivere una scheda adattiva personalizzata.

> Per una [Panoramica del modello di scheda adattivo](index.md) , vedere.

> [!IMPORTANT] 
> 
> *Termini e contratto* 
> 
> Questo servizio a **livello di Alpha** viene fornito "così com'è", con tutti gli errori e non è supportato in alcun modo. Qualsiasi raccolta di dati dal servizio è soggetta all' [informativa sulla privacy Microsoft](https://go.microsoft.com/fwlink/?LinkID=824704).
> 
> Queste funzionalità sono **in anteprima e sono soggette a modifiche**. Il feedback non è solo Benvenuto, ma è fondamentale per garantire la fornitura delle funzionalità necessarie.

## <a name="how-does-the-service-help-me"></a>In che modo il servizio può aiutarmi?

Supponiamo di avere solo una porzione di dati, forse i dati finanziari, i dati Microsoft Graph, i dati schema.org o i dati personalizzati all'interno dell'organizzazione. 

Ora voglio visualizzare i dati per un utente. 

Tradizionalmente significa scrivere codice personalizzato dell'interfaccia utente in tutti gli stack front-end consegnati agli utenti finali.

Tuttavia, se esistesse un mondo in cui l'app poteva "apprendere" nuovi modelli di interfaccia utente in base al tipo di dati? Un mondo in cui chiunque potrebbe contribuire, migliorare e condividere modelli di interfaccia utente comuni, all'interno di progetti, all'interno di un'organizzazione o per l'intera rete Internet.

## <a name="what-is-the-card-template-service"></a>Che cos'è il servizio modello di scheda?

Il servizio modello di scheda è un semplice endpoint REST che consente di:

* **Trovare** un modello analizzando la struttura dei dati
* **Ottenere** un modello in modo da poterlo associare direttamente al client, *senza inviare i dati al server o mai uscire dal dispositivo*
* **Popolare** un modello nel server, quando il data binding lato client non è appropriato o possibile

Dietro tutto, è:

* Un repository di modelli open source condiviso supportato da GitHub. *(Il repository è attualmente privato, ma sarà reso pubblico non appena si riallacciano alcune estremità separate)*
* Tutti i modelli sono file JSON flat nel repository, che semplificano la modifica, contribuiscono e condividono una parte naturale di un flusso di lavoro per sviluppatori.
* Il codice per il servizio sarà reso disponibile, in modo che sia possibile ospitare ovunque sia più sensato. 

## <a name="using-the-service"></a>Utilizzo del servizio

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

Questo endpoint tenta di trovare un modello analizzando la struttura dei dati.

> `HTTP POST https://templates.adaptivecards.io/find`

#### <a name="example"></a>Esempio

Supponiamo di avere appena raggiunto un endpoint [Microsoft Graph](https://graph.microsoft.com) per ottenere i dati dell'organizzazione.

> `HTTP GET https://graph.microsoft.com/v1.0/me/`

![Screenshot di Graph Explorer](content/2019-08-01-12-08-13.png)

L'API ha restituito **i dati JSON**, ma come **è** possibile visualizzarli agli utenti usando schede adattive? 

Per prima cosa, voglio verificare se esiste un modello per questo tipo di dati, quindi effettuo una richiesta HTTP all' `/find` endpoint con i miei dati `POST body`in.

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

**Risposta**

```json
[
  {
    "templateUrl": "graph.microsoft.com/Profile.json",
    "confidence": 1
  }
]
```

Il servizio restituisce un elenco di tutti i modelli corrispondenti, insieme a `confidence` un oggetto che indica la modalità di chiusura della corrispondenza. Ora posso usare l'URL del modello per **ottenere** il modello o **popolarlo** sul lato server.

### <a name="get-a-template"></a>Ottenere un modello

Un modello recuperato da questo endpoint può essere popolato con i dati in fase di esecuzione [usando gli SDK di templatng](sdk.md).

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]`

È anche possibile includere "dati di esempio" con il modello, in modo da rendere più intuitiva la modifica nella finestra di progettazione:

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]?sampleData=true`

#### <a name="example"></a>Esempio

Si otterrà il modello di profilo Microsoft Graph restituito in `/find` precedenza.

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

Usare ora questo modello con gli [SDK](sdk.md) per i modelli per creare una scheda Adaptive pronta per il rendering.

### <a name="populate-a-template-server-side"></a>Popolamento di un modello lato server

In alcuni casi potrebbe non essere opportuno popolare un modello nel client.  Per questi casi d'uso, è possibile fare in modo che il servizio restituisca una scheda adattiva completamente popolata, pronta per essere passata a qualsiasi renderer di schede adattivo.

> `HTTP POST https://templates.adaptivecards.io/[TEMPLATE-PATH]`

#### <a name="example"></a>Esempio

È ora popolare il modello di profilo di Microsoft Graph restituito dall' `/find` uso dei dati precedenti.

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

Si noti come la risposta ha sostituito il testo del `TextBlock` primo `"Megan Bowen"` con anziché `"{name}"`, come nella `GET` richiesta. Questo AdaptiveCard può ora essere passato a qualsiasi renderer di schede adattive senza passare attraverso il modello sul lato client.

## <a name="contributing-templates"></a>Aggiunta di contributi ai modelli

Il servizio modello è supportato da un repository GitHub, che attualmente è **privato**, ma in questo modo si aprirà l'origine una volta allegate alcune estremità.

Ci auguriamo che, usando GitHub come archivio di backup per i modelli, possiamo "democratizzare" il processo di creazione, miglioramento e condivisione dei modelli. Chiunque può inviare una richiesta pull che include un modello completamente nuovo o apportare miglioramenti a quelli esistenti... tutto all'interno dell'esperienza intuitiva per gli sviluppatori di GitHub.

## <a name="self-hosting-the-service"></a>Self-hosting del servizio

Non tutti i tipi di dati sono appropriati per il servizio modello "centrale" di schede adattive `https://templates.adaptivecards.io`ospitato in. 

Si vuole assicurarsi che chiunque possa ospitare il servizio del modello all'interno dell'organizzazione, in modo che il codice sorgente venga reso disponibile e la distribuzione in Azure o in un back-end è molto semplice.

Ulteriori informazioni su questa versione in un secondo momento.