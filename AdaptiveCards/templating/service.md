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
# <a name="adaptive-cards-template-service"></a><span data-ttu-id="b2eb7-102">Servizio modello schede adattive</span><span class="sxs-lookup"><span data-stu-id="b2eb7-102">Adaptive Cards Template Service</span></span>

<span data-ttu-id="b2eb7-103">Il servizio modello schede adattive è un servizio di prova che consente a chiunque di trovare, contribuire e condividere un set di modelli noti.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-103">The Adaptive Cards Template Service is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

<span data-ttu-id="b2eb7-104">È utile se si desidera visualizzare alcuni dati, ma non si desidera preoccuparsi di scrivere una scheda adattiva personalizzata.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-104">It's useful if you want to display some data but don't want to bother writing a custom adaptive card for it.</span></span>

> <span data-ttu-id="b2eb7-105">Per una [Panoramica del modello di scheda adattivo](index.md) , vedere.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="b2eb7-106">*Termini e contratto*</span><span class="sxs-lookup"><span data-stu-id="b2eb7-106">*Terms and agreement*</span></span> 
> 
> <span data-ttu-id="b2eb7-107">Questo servizio a **livello di Alpha** viene fornito "così com'è", con tutti gli errori e non è supportato in alcun modo.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-107">This **alpha-level** service is provided "as-is", with all faults and is not supported in any way.</span></span> <span data-ttu-id="b2eb7-108">Qualsiasi raccolta di dati dal servizio è soggetta all' [informativa sulla privacy Microsoft](https://go.microsoft.com/fwlink/?LinkID=824704).</span><span class="sxs-lookup"><span data-stu-id="b2eb7-108">Any data collection from the service is subject to the [Microsoft privacy statement](https://go.microsoft.com/fwlink/?LinkID=824704).</span></span>
> 
> <span data-ttu-id="b2eb7-109">Queste funzionalità sono **in anteprima e sono soggette a modifiche**.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-109">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="b2eb7-110">Il feedback non è solo Benvenuto, ma è fondamentale per garantire la fornitura delle funzionalità necessarie.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-110">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

## <a name="how-does-the-service-help-me"></a><span data-ttu-id="b2eb7-111">In che modo il servizio può aiutarmi?</span><span class="sxs-lookup"><span data-stu-id="b2eb7-111">How does the service help me?</span></span>

<span data-ttu-id="b2eb7-112">Supponiamo di avere solo una porzione di dati, forse i dati finanziari, i dati Microsoft Graph, i dati schema.org o i dati personalizzati all'interno dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-112">Let's say I just got a piece of data, maybe it's financial data, Microsoft Graph data, schema.org data, or custom data from within my organization.</span></span> 

<span data-ttu-id="b2eb7-113">Ora voglio visualizzare i dati per un utente.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-113">Now I want to display the data to a user.</span></span> 

<span data-ttu-id="b2eb7-114">Tradizionalmente significa scrivere codice personalizzato dell'interfaccia utente in tutti gli stack front-end consegnati agli utenti finali.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-114">Traditionally that means writing custom UI code in all of the front-end stacks that I deliver to end-users.</span></span>

<span data-ttu-id="b2eb7-115">Tuttavia, se esistesse un mondo in cui l'app poteva "apprendere" nuovi modelli di interfaccia utente in base al tipo di dati?</span><span class="sxs-lookup"><span data-stu-id="b2eb7-115">But what if there were a world where my app could "learn" new UI templates based on the type of data?</span></span> <span data-ttu-id="b2eb7-116">Un mondo in cui chiunque potrebbe contribuire, migliorare e condividere modelli di interfaccia utente comuni, all'interno di progetti, all'interno di un'organizzazione o per l'intera rete Internet.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-116">A world where anyone could contribute, enhance, and share common UI templates, within their own projects, within an organization, or for the entire internet.</span></span>

## <a name="what-is-the-card-template-service"></a><span data-ttu-id="b2eb7-117">Che cos'è il servizio modello di scheda?</span><span class="sxs-lookup"><span data-stu-id="b2eb7-117">What is the card template service?</span></span>

<span data-ttu-id="b2eb7-118">Il servizio modello di scheda è un semplice endpoint REST che consente di:</span><span class="sxs-lookup"><span data-stu-id="b2eb7-118">The card template service is a simple REST endpoint that helps:</span></span>

* <span data-ttu-id="b2eb7-119">**Trovare** un modello analizzando la struttura dei dati</span><span class="sxs-lookup"><span data-stu-id="b2eb7-119">**Find** a template by analyzing the structure of your data</span></span>
* <span data-ttu-id="b2eb7-120">**Ottenere** un modello in modo da poterlo associare direttamente al client, *senza inviare i dati al server o mai uscire dal dispositivo*</span><span class="sxs-lookup"><span data-stu-id="b2eb7-120">**Get** a template so you can bind it directly on the client, *without sending your data to the server or ever leaving the device*</span></span>
* <span data-ttu-id="b2eb7-121">**Popolare** un modello nel server, quando il data binding lato client non è appropriato o possibile</span><span class="sxs-lookup"><span data-stu-id="b2eb7-121">**Populate** a template on the server, when client-side data binding isn't appropriate or possible</span></span>

<span data-ttu-id="b2eb7-122">Dietro tutto, è:</span><span class="sxs-lookup"><span data-stu-id="b2eb7-122">Behind it all, is:</span></span>

* <span data-ttu-id="b2eb7-123">Un repository di modelli open source condiviso supportato da GitHub.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-123">A shared, open-source template repository backed by GitHub.</span></span> <span data-ttu-id="b2eb7-124">*(Il repository è attualmente privato, ma sarà reso pubblico non appena si riallacciano alcune estremità separate)*</span><span class="sxs-lookup"><span data-stu-id="b2eb7-124">*(The repo is currently private but will be made public as soon as we tie up some loose ends)*</span></span>
* <span data-ttu-id="b2eb7-125">Tutti i modelli sono file JSON flat nel repository, che semplificano la modifica, contribuiscono e condividono una parte naturale di un flusso di lavoro per sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-125">All the templates are flat JSON files in the repo, which makes editing, contributing, and sharing a natural part of a developer workflow.</span></span>
* <span data-ttu-id="b2eb7-126">Il codice per il servizio sarà reso disponibile, in modo che sia possibile ospitare ovunque sia più sensato.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-126">The code for the service will be made available so you can host wherever makes the most sense to you.</span></span> 

## <a name="using-the-service"></a><span data-ttu-id="b2eb7-127">Utilizzo del servizio</span><span class="sxs-lookup"><span data-stu-id="b2eb7-127">Using the service</span></span>

### <a name="get-all-templates"></a><span data-ttu-id="b2eb7-128">Ottenere tutti i modelli</span><span class="sxs-lookup"><span data-stu-id="b2eb7-128">Get all templates</span></span> 

<span data-ttu-id="b2eb7-129">Questo endpoint restituisce un elenco di tutti i modelli noti.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-129">This endpoint returns a list of all known templates.</span></span>

> `HTTP GET https://templates.adaptivecards.io/list`

<span data-ttu-id="b2eb7-130">**Estratto della risposta**</span><span class="sxs-lookup"><span data-stu-id="b2eb7-130">**Response excerpt**</span></span>

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

### <a name="find-a-template"></a><span data-ttu-id="b2eb7-131">Trovare un modello</span><span class="sxs-lookup"><span data-stu-id="b2eb7-131">Find a template</span></span>

<span data-ttu-id="b2eb7-132">Questo endpoint tenta di trovare un modello analizzando la struttura dei dati.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-132">This endpoint tries to find a template by analyzing the structure of your data.</span></span>

> `HTTP POST https://templates.adaptivecards.io/find`

#### <a name="example"></a><span data-ttu-id="b2eb7-133">Esempio</span><span class="sxs-lookup"><span data-stu-id="b2eb7-133">Example</span></span>

<span data-ttu-id="b2eb7-134">Supponiamo di avere appena raggiunto un endpoint [Microsoft Graph](https://graph.microsoft.com) per ottenere i dati dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-134">Let's say I just hit a [Microsoft Graph](https://graph.microsoft.com) endpoint to get organizational data about me.</span></span>

> `HTTP GET https://graph.microsoft.com/v1.0/me/`

![Screenshot di Graph Explorer](content/2019-08-01-12-08-13.png)

<span data-ttu-id="b2eb7-136">L'API ha restituito **i dati JSON**, ma come **è** possibile visualizzarli agli utenti usando schede adattive?</span><span class="sxs-lookup"><span data-stu-id="b2eb7-136">That API returned **JSON data**, but how do I **display it** to users using Adaptive Cards?</span></span> 

<span data-ttu-id="b2eb7-137">Per prima cosa, voglio verificare se esiste un modello per questo tipo di dati, quindi effettuo una richiesta HTTP all' `/find` endpoint con i miei dati `POST body`in.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-137">First I want to see if a template exists for this type of data, so I make an HTTP request to the `/find` endpoint with my data in the `POST body`.</span></span>

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

<span data-ttu-id="b2eb7-138">**Risposta**</span><span class="sxs-lookup"><span data-stu-id="b2eb7-138">**Response:**</span></span>

```json
[
  {
    "templateUrl": "graph.microsoft.com/Profile.json",
    "confidence": 1
  }
]
```

<span data-ttu-id="b2eb7-139">Il servizio restituisce un elenco di tutti i modelli corrispondenti, insieme a `confidence` un oggetto che indica la modalità di chiusura della corrispondenza.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-139">The service returns a list of any matching templates, along with a `confidence` indicating how close the match is.</span></span> <span data-ttu-id="b2eb7-140">Ora posso usare l'URL del modello per **ottenere** il modello o **popolarlo** sul lato server.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-140">Now I can use that template URL to **get** the template, or **populate** it server-side.</span></span>

### <a name="get-a-template"></a><span data-ttu-id="b2eb7-141">Ottenere un modello</span><span class="sxs-lookup"><span data-stu-id="b2eb7-141">Get a template</span></span>

<span data-ttu-id="b2eb7-142">Un modello recuperato da questo endpoint può essere popolato con i dati in fase di esecuzione [usando gli SDK di templatng](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="b2eb7-142">A template retrieved from this endpoint can be populated with data at runtime [using the templatng SDKs](sdk.md).</span></span>

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]`

<span data-ttu-id="b2eb7-143">È anche possibile includere "dati di esempio" con il modello, in modo da rendere più intuitiva la modifica nella finestra di progettazione:</span><span class="sxs-lookup"><span data-stu-id="b2eb7-143">You can also include "sample data" with the template, which makes editing in the designer more friendly:</span></span>

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]?sampleData=true`

#### <a name="example"></a><span data-ttu-id="b2eb7-144">Esempio</span><span class="sxs-lookup"><span data-stu-id="b2eb7-144">Example</span></span>

<span data-ttu-id="b2eb7-145">Si otterrà il modello di profilo Microsoft Graph restituito in `/find` precedenza.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-145">Let's get the Microsoft Graph profile template that was returned from `/find` above.</span></span>

`HTTP GET https://templates.adaptivecards.io/graph.microsoft.com/Profile.json`

<span data-ttu-id="b2eb7-146">**Estratto della risposta**</span><span class="sxs-lookup"><span data-stu-id="b2eb7-146">**Response excerpt**</span></span>

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

<span data-ttu-id="b2eb7-147">Usare ora questo modello con gli [SDK](sdk.md) per i modelli per creare una scheda Adaptive pronta per il rendering.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-147">Now use this template with the [templating SDKs](sdk.md) to create a ready-to-render Adaptive Card.</span></span>

### <a name="populate-a-template-server-side"></a><span data-ttu-id="b2eb7-148">Popolamento di un modello lato server</span><span class="sxs-lookup"><span data-stu-id="b2eb7-148">Populate a template server-side</span></span>

<span data-ttu-id="b2eb7-149">In alcuni casi potrebbe non essere opportuno popolare un modello nel client.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-149">In some cases it may not make sense to populate a template on the client.</span></span>  <span data-ttu-id="b2eb7-150">Per questi casi d'uso, è possibile fare in modo che il servizio restituisca una scheda adattiva completamente popolata, pronta per essere passata a qualsiasi renderer di schede adattivo.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-150">For these use cases, you can have the service return a fully-populated Adaptive Card, ready to be passed to any Adaptive Card Renderer.</span></span>

> `HTTP POST https://templates.adaptivecards.io/[TEMPLATE-PATH]`

#### <a name="example"></a><span data-ttu-id="b2eb7-151">Esempio</span><span class="sxs-lookup"><span data-stu-id="b2eb7-151">Example</span></span>

<span data-ttu-id="b2eb7-152">È ora popolare il modello di profilo di Microsoft Graph restituito dall' `/find` uso dei dati precedenti.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-152">Let's populate the Microsoft Graph profile template that was returned from `/find` using the data above.</span></span>

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

<span data-ttu-id="b2eb7-153">**Estratto della risposta**</span><span class="sxs-lookup"><span data-stu-id="b2eb7-153">**Response excerpt**</span></span>

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

<span data-ttu-id="b2eb7-154">Si noti come la risposta ha sostituito il testo del `TextBlock` primo `"Megan Bowen"` con anziché `"{name}"`, come nella `GET` richiesta.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-154">Notice how the response replaced the text of the first `TextBlock` with `"Megan Bowen"` instead of `"{name}"`, as in the `GET` request.</span></span> <span data-ttu-id="b2eb7-155">Questo AdaptiveCard può ora essere passato a qualsiasi renderer di schede adattive senza passare attraverso il modello sul lato client.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-155">This AdaptiveCard can now be passed to any Adaptive Card renderer without going through client-side templating.</span></span>

## <a name="contributing-templates"></a><span data-ttu-id="b2eb7-156">Aggiunta di contributi ai modelli</span><span class="sxs-lookup"><span data-stu-id="b2eb7-156">Contributing templates</span></span>

<span data-ttu-id="b2eb7-157">Il servizio modello è supportato da un repository GitHub, che attualmente è **privato**, ma in questo modo si aprirà l'origine una volta allegate alcune estremità.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-157">The template service is backed by a GitHub repo (which is currently **private**), but we will open source once we tie up some loose ends.</span></span>

<span data-ttu-id="b2eb7-158">Ci auguriamo che, usando GitHub come archivio di backup per i modelli, possiamo "democratizzare" il processo di creazione, miglioramento e condivisione dei modelli.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-158">Our hope is that by using GitHub as a backing store for the templates, we can "democratize" the process of authoring, enhancing, and sharing templates.</span></span> <span data-ttu-id="b2eb7-159">Chiunque può inviare una richiesta pull che include un modello completamente nuovo o apportare miglioramenti a quelli esistenti... tutto all'interno dell'esperienza intuitiva per gli sviluppatori di GitHub.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-159">Anyone can submit a Pull Request that includes an entirely new template, or make enhancements to existing ones... all within the developer-friendly experience of GitHub.</span></span>

## <a name="self-hosting-the-service"></a><span data-ttu-id="b2eb7-160">Self-hosting del servizio</span><span class="sxs-lookup"><span data-stu-id="b2eb7-160">Self-hosting the service</span></span>

<span data-ttu-id="b2eb7-161">Non tutti i tipi di dati sono appropriati per il servizio modello "centrale" di schede adattive `https://templates.adaptivecards.io`ospitato in.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-161">Not all types of data are appropriate for the "central" Adaptive Cards template service hosted at `https://templates.adaptivecards.io`.</span></span> 

<span data-ttu-id="b2eb7-162">Si vuole assicurarsi che chiunque possa ospitare il servizio del modello all'interno dell'organizzazione, in modo che il codice sorgente venga reso disponibile e la distribuzione in Azure o in un back-end è molto semplice.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-162">We want to make sure anyone can host the template service within your organization, so the source code will be made available and we'll make it very simple to deploy to Azure or your own back-end.</span></span>

<span data-ttu-id="b2eb7-163">Ulteriori informazioni su questa versione in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="b2eb7-163">More on this at a later date.</span></span>