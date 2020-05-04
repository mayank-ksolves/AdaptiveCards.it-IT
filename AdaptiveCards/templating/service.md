---
title: Servizio modelli di Schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: db211fc3bac27dc980ae87983a918a35730f8e5e
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2020
ms.locfileid: "82136187"
---
# <a name="adaptive-cards-template-service"></a><span data-ttu-id="6bc90-102">Servizio modelli di Schede adattive</span><span class="sxs-lookup"><span data-stu-id="6bc90-102">Adaptive Cards Template Service</span></span>

<span data-ttu-id="6bc90-103">Il servizio modelli di Schede adattive è un modello di verifica che consente a chiunque di trovare, contribuire e condividere un set di modelli ben noti.</span><span class="sxs-lookup"><span data-stu-id="6bc90-103">The Adaptive Cards Template Service is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

<span data-ttu-id="6bc90-104">È utile se vuoi visualizzare alcuni dati senza dover scrivere per questo una scheda adattiva personalizzata.</span><span class="sxs-lookup"><span data-stu-id="6bc90-104">It's useful if you want to display some data but don't want to bother writing a custom adaptive card for it.</span></span>

> <span data-ttu-id="6bc90-105">Per una [panoramica della creazione di modelli di schede adattive](index.md), leggi l'argomento specifico.</span><span class="sxs-lookup"><span data-stu-id="6bc90-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="6bc90-106">*Condizioni e contratto*</span><span class="sxs-lookup"><span data-stu-id="6bc90-106">*Terms and agreement*</span></span> 
> 
> <span data-ttu-id="6bc90-107">Questo servizio di **livello alfa** viene fornito "com'è", inclusi tutti gli errori, e non è supportato in alcun modo.</span><span class="sxs-lookup"><span data-stu-id="6bc90-107">This **alpha-level** service is provided "as-is", with all faults and is not supported in any way.</span></span> <span data-ttu-id="6bc90-108">I dati raccolti dal servizio sono soggetti alle disposizioni dell'[Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkID=824704).</span><span class="sxs-lookup"><span data-stu-id="6bc90-108">Any data collection from the service is subject to the [Microsoft privacy statement](https://go.microsoft.com/fwlink/?LinkID=824704).</span></span>
> 
> <span data-ttu-id="6bc90-109">Queste funzionalità sono disponibili **in anteprima e sono soggette a modifiche**.</span><span class="sxs-lookup"><span data-stu-id="6bc90-109">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="6bc90-110">Il tuo feedback non solo è apprezzato, ma è anche fondamentale per aiutarci a offrire le funzionalità di cui **tu** hai bisogno.</span><span class="sxs-lookup"><span data-stu-id="6bc90-110">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

## <a name="how-does-the-service-help-me"></a><span data-ttu-id="6bc90-111">In che modo può essere utile il servizio?</span><span class="sxs-lookup"><span data-stu-id="6bc90-111">How does the service help me?</span></span>

<span data-ttu-id="6bc90-112">Supponiamo di aver ricevuto dall'interno dell'organizzazione alcuni dati, ad esempio dati finanziari, di Microsoft Graph, di schema.org o personalizzati.</span><span class="sxs-lookup"><span data-stu-id="6bc90-112">Let's say I just got a piece of data, maybe it's financial data, Microsoft Graph data, schema.org data, or custom data from within my organization.</span></span> 

<span data-ttu-id="6bc90-113">Ora vogliamo visualizzare questi dati per un utente.</span><span class="sxs-lookup"><span data-stu-id="6bc90-113">Now I want to display the data to a user.</span></span> 

<span data-ttu-id="6bc90-114">Di norma è necessario scrivere codice di interfaccia utente personalizzato in tutti gli stack front-end che vengono recapitati agli utenti finali.</span><span class="sxs-lookup"><span data-stu-id="6bc90-114">Traditionally that means writing custom UI code in all of the front-end stacks that I deliver to end-users.</span></span>

<span data-ttu-id="6bc90-115">Supponiamo invece che esista un ambiente in cui la nostra app sia in grado di "apprendere" nuovi modelli di interfaccia utente in base al tipo di dati.</span><span class="sxs-lookup"><span data-stu-id="6bc90-115">But what if there were a world where my app could "learn" new UI templates based on the type of data?</span></span> <span data-ttu-id="6bc90-116">In questo ambiente ognuno può aggiungere contributi, migliorare e condividere modelli di interfaccia utente comuni, all'interno di progetti specifici, all'interno di un'organizzazione o per l'intera rete Internet.</span><span class="sxs-lookup"><span data-stu-id="6bc90-116">A world where anyone could contribute, enhance, and share common UI templates, within their own projects, within an organization, or for the entire internet.</span></span>

## <a name="what-is-the-card-template-service"></a><span data-ttu-id="6bc90-117">Che cos'è il servizio modelli di schede?</span><span class="sxs-lookup"><span data-stu-id="6bc90-117">What is the card template service?</span></span>

<span data-ttu-id="6bc90-118">Il servizio modelli di schede è un semplice endpoint REST che consente di:</span><span class="sxs-lookup"><span data-stu-id="6bc90-118">The card template service is a simple REST endpoint that helps:</span></span>

* <span data-ttu-id="6bc90-119">**Trovare** un modello analizzando la struttura dei dati</span><span class="sxs-lookup"><span data-stu-id="6bc90-119">**Find** a template by analyzing the structure of your data</span></span>
* <span data-ttu-id="6bc90-120">**Ottenere** un modello in modo da poterlo associare direttamente nel client, *senza inviare i dati al server o uscire dal dispositivo*</span><span class="sxs-lookup"><span data-stu-id="6bc90-120">**Get** a template so you can bind it directly on the client, *without sending your data to the server or ever leaving the device*</span></span>
* <span data-ttu-id="6bc90-121">**Popolare** un modello nel server, quando il binding dei dati sul lato client non è appropriato o possibile</span><span class="sxs-lookup"><span data-stu-id="6bc90-121">**Populate** a template on the server, when client-side data binding isn't appropriate or possible</span></span>

<span data-ttu-id="6bc90-122">Alla base di tutto:</span><span class="sxs-lookup"><span data-stu-id="6bc90-122">Behind it all, is:</span></span>

* <span data-ttu-id="6bc90-123">È presente un repository di modelli open source condiviso, supportato da GitHub.</span><span class="sxs-lookup"><span data-stu-id="6bc90-123">A shared, open-source template repository backed by GitHub.</span></span> <span data-ttu-id="6bc90-124">*Il repository è attualmente privato, ma sarà reso pubblico appena avremo risolto alcune questioni rimaste in sospeso.*</span><span class="sxs-lookup"><span data-stu-id="6bc90-124">*(The repo is currently private but will be made public as soon as we tie up some loose ends)*</span></span>
* <span data-ttu-id="6bc90-125">Tutti i modelli presenti nel repository sono file JSON flat, pertanto le modifiche, l'aggiunta di contributi e le condivisioni possono essere effettuate con naturalezza durante il flusso di lavoro di uno sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="6bc90-125">All the templates are flat JSON files in the repo, which makes editing, contributing, and sharing a natural part of a developer workflow.</span></span>
* <span data-ttu-id="6bc90-126">Il codice sarà reso disponibile in modo da poter ospitare il servizio ovunque ritieni che sia più appropriato.</span><span class="sxs-lookup"><span data-stu-id="6bc90-126">The code for the service will be made available so you can host wherever makes the most sense to you.</span></span> 

## <a name="using-the-service"></a><span data-ttu-id="6bc90-127">Uso del servizio</span><span class="sxs-lookup"><span data-stu-id="6bc90-127">Using the service</span></span>

### <a name="get-all-templates"></a><span data-ttu-id="6bc90-128">Ottenere tutti i modelli</span><span class="sxs-lookup"><span data-stu-id="6bc90-128">Get all templates</span></span> 

<span data-ttu-id="6bc90-129">Questo endpoint restituisce un elenco di tutti i modelli noti.</span><span class="sxs-lookup"><span data-stu-id="6bc90-129">This endpoint returns a list of all known templates.</span></span>

> `HTTP GET https://templates.adaptivecards.io/list`

<span data-ttu-id="6bc90-130">**Estratto della risposta**</span><span class="sxs-lookup"><span data-stu-id="6bc90-130">**Response excerpt**</span></span>

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

### <a name="find-a-template"></a><span data-ttu-id="6bc90-131">Trovare un modello</span><span class="sxs-lookup"><span data-stu-id="6bc90-131">Find a template</span></span>

<span data-ttu-id="6bc90-132">Questo endpoint cerca di trovare un modello analizzando la struttura dei dati.</span><span class="sxs-lookup"><span data-stu-id="6bc90-132">This endpoint tries to find a template by analyzing the structure of your data.</span></span>

> `HTTP POST https://templates.adaptivecards.io/find`

#### <a name="example"></a><span data-ttu-id="6bc90-133">Esempio</span><span class="sxs-lookup"><span data-stu-id="6bc90-133">Example</span></span>

<span data-ttu-id="6bc90-134">Supponiamo di aver eseguito l'accesso a un endpoint di [Microsoft Graph](https://graph.microsoft.com) per ottenere i dati dell'organizzazione che ci riguardano.</span><span class="sxs-lookup"><span data-stu-id="6bc90-134">Let's say I access a [Microsoft Graph](https://graph.microsoft.com) endpoint to get organizational data about me.</span></span>

> `HTTP GET https://graph.microsoft.com/v1.0/me/`

![Screenshot di Graph Explorer](content/2019-08-01-12-08-13.png)

<span data-ttu-id="6bc90-136">L'API restituisce **dati JSON**, ma in che modo possono essere **visualizzati** per gli utenti che usano Schede adattive?</span><span class="sxs-lookup"><span data-stu-id="6bc90-136">That API returned **JSON data**, but how do I **display it** to users using Adaptive Cards?</span></span> 

<span data-ttu-id="6bc90-137">Prima vediamo se è presente un modello per lo specifico tipo di dati. Inviamo pertanto una richiesta HTTP all'endpoint `/find` con i nostri dati in `POST body`.</span><span class="sxs-lookup"><span data-stu-id="6bc90-137">First I want to see if a template exists for this type of data, so I make an HTTP request to the `/find` endpoint with my data in the `POST body`.</span></span>

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

<span data-ttu-id="6bc90-138">**Risposta:**</span><span class="sxs-lookup"><span data-stu-id="6bc90-138">**Response:**</span></span>

```json
[
  {
    "templateUrl": "graph.microsoft.com/Profile.json",
    "confidence": 1
  }
]
```

<span data-ttu-id="6bc90-139">Il servizio restituisce un elenco di tutti i modelli corrispondenti, insieme a un valore `confidence` che indica il livello di corrispondenza.</span><span class="sxs-lookup"><span data-stu-id="6bc90-139">The service returns a list of any matching templates, along with a `confidence` indicating how close the match is.</span></span> <span data-ttu-id="6bc90-140">Ora possiamo usare l'URL del modello per **ottenere** il modello o **popolarlo** sul lato server.</span><span class="sxs-lookup"><span data-stu-id="6bc90-140">Now I can use that template URL to **get** the template, or **populate** it server-side.</span></span>

### <a name="get-a-template"></a><span data-ttu-id="6bc90-141">Ottenere un modello</span><span class="sxs-lookup"><span data-stu-id="6bc90-141">Get a template</span></span>

<span data-ttu-id="6bc90-142">Un modello recuperato da questo endpoint può essere popolato con i dati in fase di esecuzione [usando gli SDK di creazione modelli](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="6bc90-142">A template retrieved from this endpoint can be populated with data at runtime [using the templatng SDKs](sdk.md).</span></span>

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]`

<span data-ttu-id="6bc90-143">Nel modello puoi includere anche dati di esempio, in modo da rendere più intuitive le operazioni di modifica nella finestra di progettazione:</span><span class="sxs-lookup"><span data-stu-id="6bc90-143">You can also include "sample data" with the template, which makes editing in the designer more friendly:</span></span>

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]?sampleData=true`

#### <a name="example"></a><span data-ttu-id="6bc90-144">Esempio</span><span class="sxs-lookup"><span data-stu-id="6bc90-144">Example</span></span>

<span data-ttu-id="6bc90-145">Proviamo a ottenere il modello di profilo di Microsoft Graph restituito dall'operazione `/find` precedente.</span><span class="sxs-lookup"><span data-stu-id="6bc90-145">Let's get the Microsoft Graph profile template that was returned from `/find` above.</span></span>

`HTTP GET https://templates.adaptivecards.io/graph.microsoft.com/Profile.json`

<span data-ttu-id="6bc90-146">**Estratto della risposta**</span><span class="sxs-lookup"><span data-stu-id="6bc90-146">**Response excerpt**</span></span>

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

<span data-ttu-id="6bc90-147">Usa ora questo modello con gli [SDK per la creazione di modelli](sdk.md) per creare una scheda adattiva pronta per il rendering.</span><span class="sxs-lookup"><span data-stu-id="6bc90-147">Now use this template with the [templating SDKs](sdk.md) to create a ready-to-render Adaptive Card.</span></span>

### <a name="populate-a-template-server-side"></a><span data-ttu-id="6bc90-148">Popolare un modello sul lato server</span><span class="sxs-lookup"><span data-stu-id="6bc90-148">Populate a template server-side</span></span>

<span data-ttu-id="6bc90-149">In alcuni casi potrebbe non essere opportuno popolare un modello nel client.</span><span class="sxs-lookup"><span data-stu-id="6bc90-149">In some cases it may not make sense to populate a template on the client.</span></span>  <span data-ttu-id="6bc90-150">Per questi casi d'uso è possibile fare in modo che il servizio restituisca una scheda adattiva completamente popolata, pronta per essere passata a qualsiasi renderer di schede adattive.</span><span class="sxs-lookup"><span data-stu-id="6bc90-150">For these use cases, you can have the service return a fully-populated Adaptive Card, ready to be passed to any Adaptive Card Renderer.</span></span>

> `HTTP POST https://templates.adaptivecards.io/[TEMPLATE-PATH]`

#### <a name="example"></a><span data-ttu-id="6bc90-151">Esempio</span><span class="sxs-lookup"><span data-stu-id="6bc90-151">Example</span></span>

<span data-ttu-id="6bc90-152">Proviamo a popolare il modello di profilo di Microsoft Graph restituito dall'operazione `/find` usando i dati precedenti.</span><span class="sxs-lookup"><span data-stu-id="6bc90-152">Let's populate the Microsoft Graph profile template that was returned from `/find` using the data above.</span></span>

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

<span data-ttu-id="6bc90-153">**Estratto della risposta**</span><span class="sxs-lookup"><span data-stu-id="6bc90-153">**Response excerpt**</span></span>

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

<span data-ttu-id="6bc90-154">Si noti come la risposta ha sostituito il testo del primo `TextBlock` con `"Megan Bowen"` anziché `"{name}"` come nella richiesta `GET`.</span><span class="sxs-lookup"><span data-stu-id="6bc90-154">Notice how the response replaced the text of the first `TextBlock` with `"Megan Bowen"` instead of `"{name}"`, as in the `GET` request.</span></span> <span data-ttu-id="6bc90-155">È ora possibile passare questa scheda adattiva a qualsiasi renderer di schede adattive senza dover creare modelli sul lato client.</span><span class="sxs-lookup"><span data-stu-id="6bc90-155">This AdaptiveCard can now be passed to any Adaptive Card renderer without going through client-side templating.</span></span>

## <a name="contributing-templates"></a><span data-ttu-id="6bc90-156">Aggiunta di contributi ai modelli</span><span class="sxs-lookup"><span data-stu-id="6bc90-156">Contributing templates</span></span>

<span data-ttu-id="6bc90-157">I modelli sono ospitati in GitHub nel repository [adaptivecards-templates](https://github.com/microsoft/adaptivecards-templates).</span><span class="sxs-lookup"><span data-stu-id="6bc90-157">The templates are hosted on GitHub in the [adaptivecards-templates](https://github.com/microsoft/adaptivecards-templates) repo.</span></span>

<span data-ttu-id="6bc90-158">Usando GitHub come archivio di backup per i modelli, ci auguriamo di poter "democratizzare" il processo di creazione, miglioramento e condivisione dei modelli.</span><span class="sxs-lookup"><span data-stu-id="6bc90-158">Our hope is that by using GitHub as a backing store for the templates, we can "democratize" the process of authoring, enhancing, and sharing templates.</span></span> <span data-ttu-id="6bc90-159">Chiunque può inviare una richiesta pull con un modello completamente nuovo o apportare miglioramenti ai modelli esistenti, tutto all'interno dell'esperienza di GitHub adatta per gli sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="6bc90-159">Anyone can submit a Pull Request that includes an entirely new template, or make enhancements to existing ones... all within the developer-friendly experience of GitHub.</span></span>

## <a name="self-hosting-the-service"></a><span data-ttu-id="6bc90-160">Test interno del servizio</span><span class="sxs-lookup"><span data-stu-id="6bc90-160">Self-hosting the service</span></span>

<span data-ttu-id="6bc90-161">Non tutti i tipi di dati sono adatti per il servizio modelli "centrale" di Schede adattive ospitato all'indirizzo `https://templates.adaptivecards.io`.</span><span class="sxs-lookup"><span data-stu-id="6bc90-161">Not all types of data are appropriate for the "central" Adaptive Cards template service hosted at `https://templates.adaptivecards.io`.</span></span> 

<span data-ttu-id="6bc90-162">Vogliamo assicurarci che chiunque possa ospitare il servizio modelli all'interno di un'organizzazione. Il codice sorgente è quindi disponibile su GitHub e può essere distribuito con estrema facilità nella Funzione di Azure personale.</span><span class="sxs-lookup"><span data-stu-id="6bc90-162">We want to make sure anyone can host the template service within your organization, so the source code is available on GitHub and can be easily deployed to your own Azure Function.</span></span> 

<span data-ttu-id="6bc90-163">Per iniziare ➡ [adaptivecards-templates](https://github.com/microsoft/adaptivecards-templates)</span><span class="sxs-lookup"><span data-stu-id="6bc90-163">Get started here ➡ [adaptivecards-templates](https://github.com/microsoft/adaptivecards-templates)</span></span>
