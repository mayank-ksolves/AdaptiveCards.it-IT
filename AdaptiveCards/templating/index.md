---
title: Panoramica della creazione di modelli
author: matthidinger
ms.author: mahiding
ms.date: 05/18/2020
ms.topic: article
ms.openlocfilehash: 41eb972603b1688a1f1857cec83208b9b55b02c3
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417622"
---
# <a name="adaptive-cards-templating"></a><span data-ttu-id="14c81-102">Creazione di modelli di Schede adattive</span><span class="sxs-lookup"><span data-stu-id="14c81-102">Adaptive Cards Templating</span></span>

<span data-ttu-id="14c81-103">Siamo lieti di condividere un'anteprima dei nuovi strumenti che ti aiuteranno a **creare**, **,riutilizzare** e **condividere** Schede adattive.</span><span class="sxs-lookup"><span data-stu-id="14c81-103">We're excited to share a preview of new tools that will help you **create**, **reuse**, and **share** Adaptive Cards.</span></span> 

> [!IMPORTANT] 
> 
> <span data-ttu-id="14c81-104">**Modifiche importanti** apportate alla **versione finale candidata di maggio 2020**</span><span class="sxs-lookup"><span data-stu-id="14c81-104">**Breaking changes** in the **May 2020 Release Candidate**</span></span>
>
> <span data-ttu-id="14c81-105">La versione finale candidata della creazione di modelli include alcune importanti modifiche che devi conoscere se stai usando i pacchetti meno recenti.</span><span class="sxs-lookup"><span data-stu-id="14c81-105">The templating release candidate includes some minor breaking changes that you should be aware of if you've been using the older packages.</span></span> <span data-ttu-id="14c81-106">Per informazioni dettagliate, vedi di seguito.</span><span class="sxs-lookup"><span data-stu-id="14c81-106">See below for details.</span></span>


## <a name="breaking-changes-as-of-may-2020"></a><span data-ttu-id="14c81-107">Modifiche importanti della versione di maggio 2020</span><span class="sxs-lookup"><span data-stu-id="14c81-107">Breaking changes as of May 2020</span></span>

1. <span data-ttu-id="14c81-108">La sintassi di binding è cambiata da `{...}` a `${...}`.</span><span class="sxs-lookup"><span data-stu-id="14c81-108">The binding syntax changed from `{...}` to `${...}`.</span></span> 
    * <span data-ttu-id="14c81-109">Ad esempio, `"text": "Hello {name}"` diventa `"text": "Hello ${name}"`</span><span class="sxs-lookup"><span data-stu-id="14c81-109">For Example: `"text": "Hello {name}"` becomes `"text": "Hello ${name}"`</span></span>
2. <span data-ttu-id="14c81-110">L'API JavaScript non contiene più un oggetto `EvaluationContext`.</span><span class="sxs-lookup"><span data-stu-id="14c81-110">The JavaScript API no longer contains an `EvaluationContext` object.</span></span> <span data-ttu-id="14c81-111">Passa semplicemente i dati alla funzione `expand`.</span><span class="sxs-lookup"><span data-stu-id="14c81-111">Simply pass your data to the `expand` function.</span></span> <span data-ttu-id="14c81-112">Per informazioni dettagliate, vedi la [pagina dell'SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="14c81-112">Please see the [SDK page](sdk.md) for full details.</span></span>
3. <span data-ttu-id="14c81-113">L'API .NET è stata riprogettata in modo da corrispondere più strettamente all'API JavaScript.</span><span class="sxs-lookup"><span data-stu-id="14c81-113">The .NET API was redesigned to more closely match the JavaScript API.</span></span> <span data-ttu-id="14c81-114">Per informazioni dettagliate, vedi la [pagina dell'SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="14c81-114">Please see the [SDK page](sdk.md) for full details.</span></span>

## <a name="how-can-templating-help-you"></a><span data-ttu-id="14c81-115">Vantaggi della creazione di modelli</span><span class="sxs-lookup"><span data-stu-id="14c81-115">How can templating help you</span></span>

<span data-ttu-id="14c81-116">La creazione di modelli consente di separare i **dati** dal **layout** in una scheda adattiva.</span><span class="sxs-lookup"><span data-stu-id="14c81-116">Templating enables the separation of **data** from the **layout** in an Adaptive Card.</span></span> 

### <a name="it-helps-design-a-card-once-and-then-populate-it-with-real-data"></a><span data-ttu-id="14c81-117">Permette di progettare una scheda una sola volta e quindi di popolarla con dati reali</span><span class="sxs-lookup"><span data-stu-id="14c81-117">It helps design a card once, and then populate it with real data</span></span>

<span data-ttu-id="14c81-118">Oggi non è possibile creare una scheda tramite [Designer di Schede adattive](https://adaptivecards.io/designer) e usare questo codice JSON per popolare il payload con **contenuto dinamico**.</span><span class="sxs-lookup"><span data-stu-id="14c81-118">Today it's impossible to create a card using the [Adaptive Card Designer](https://adaptivecards.io/designer) and use that JSON to populate the payload with **dynamic content**.</span></span> <span data-ttu-id="14c81-119">Per ottenere questo risultato, è necessario scrivere codice personalizzato per compilare una stringa JSON oppure usare gli SDK del modello a oggetti per creare un modello a oggetti che rappresenta la scheda, quindi serializzarlo in JSON.</span><span class="sxs-lookup"><span data-stu-id="14c81-119">In order to achieve this you must write custom code to build a JSON string, or use the Object Model SDKs to build an OM representing your card and serialize it to JSON.</span></span> <span data-ttu-id="14c81-120">In entrambi i casi, Designer offre un'operazione unidirezionale da eseguire una sola volta e non semplifica la modifica della progettazione della scheda in un secondo momento dopo la conversione in codice.</span><span class="sxs-lookup"><span data-stu-id="14c81-120">In either case the Designer is a one-time one-way operation and doesn't make it easy to tweak the card design later once you've converted it to code.</span></span>

### <a name="it-makes-transmissions-over-the-wire-smaller"></a><span data-ttu-id="14c81-121">Riduce le dimensioni delle trasmissioni in rete</span><span class="sxs-lookup"><span data-stu-id="14c81-121">It makes transmissions over the wire smaller</span></span>

<span data-ttu-id="14c81-122">Immagina un mondo in cui sia possibile combinare un modello e i dati **direttamente nel client**.</span><span class="sxs-lookup"><span data-stu-id="14c81-122">Imagine a world where a template and data can be combined **directly on the client**.</span></span> <span data-ttu-id="14c81-123">Significa che se usi lo stesso modello più volte, oppure vuoi aggiornarlo con nuovi dati, è sufficiente inviare i nuovi dati al dispositivo e quindi riutilizzare lo stesso modello più volte.</span><span class="sxs-lookup"><span data-stu-id="14c81-123">This means if you use the same template multiple times, or want to update it with new data, you just need to send new data to the device and it can re-use the same template over and over.</span></span>

### <a name="it-helps-you-create-a-great-looking-card-from-just-the-data-you-provide"></a><span data-ttu-id="14c81-124">Consente di creare una scheda dall'aspetto accattivante solo dai dati forniti</span><span class="sxs-lookup"><span data-stu-id="14c81-124">It helps you create a great looking card from just the data you provide</span></span>

<span data-ttu-id="14c81-125">Le schede adattive sono fantastiche, ma se fosse possibile evitare di scriverne una per ogni contenuto da visualizzare agli utenti?</span><span class="sxs-lookup"><span data-stu-id="14c81-125">We think Adaptive Cards are great, but what if you didn't have to write an Adaptive Card for everything you want to display to a user?</span></span> <span data-ttu-id="14c81-126">Con un servizio di modelli (descritto di seguito) possiamo creare un mondo in cui tutti possono contribuire, scoprire e condividere modelli per qualsiasi tipo di dati.</span><span class="sxs-lookup"><span data-stu-id="14c81-126">With a template service (described below) we can create a world where everyone can contribute, discover, and share templates over any type of data.</span></span> 

<span data-ttu-id="14c81-127">Condividi all'interno dei progetti, nell'organizzazione o con l'intera rete Internet.</span><span class="sxs-lookup"><span data-stu-id="14c81-127">Share within your own projects, your organization, or with the entire internet.</span></span>

### <a name="ai-and-other-services-could-improve-user-experiences"></a><span data-ttu-id="14c81-128">L'intelligenza artificiale e altri servizi potrebbero migliorare l'esperienza utente</span><span class="sxs-lookup"><span data-stu-id="14c81-128">AI and other services could improve user experiences</span></span>

<span data-ttu-id="14c81-129">Separando i dati dal contenuto, l'intelligenza artificiale e altri servizi possono "ragionare" sui dati nelle schede che vediamo e migliorare la produttività degli utenti o aiutarci a trovare quello che cerchiamo.</span><span class="sxs-lookup"><span data-stu-id="14c81-129">By separating data from content it opens a door for AI and other services to  "reason" over the data in the cards we see and enhance user productivity or help us find things.</span></span>

## <a name="what-is-adaptive-cards-templating"></a><span data-ttu-id="14c81-130">Cos'è la creazione di modelli di Schede adattive?</span><span class="sxs-lookup"><span data-stu-id="14c81-130">What is Adaptive Cards Templating?</span></span>

<span data-ttu-id="14c81-131">È costituita da tre componenti principali:</span><span class="sxs-lookup"><span data-stu-id="14c81-131">It's comprised of 3 major components:</span></span>

1. <span data-ttu-id="14c81-132">Il **[linguaggio del modello](language.md)** è la sintassi usata per la creazione di un modello.</span><span class="sxs-lookup"><span data-stu-id="14c81-132">The **[Template Language](language.md)** is the syntax used for authoring a template.</span></span> <span data-ttu-id="14c81-133">Designer consente anche di visualizzare in anteprima i modelli in fase di progettazione includendo "dati di esempio".</span><span class="sxs-lookup"><span data-stu-id="14c81-133">The Designer even lets you preview your templates at design time by including "sample data".</span></span>
2. <span data-ttu-id="14c81-134">Gli **[SDK di creazione modelli](sdk.md)** esistono in tutte le piattaforma di Schede adattive supportate.</span><span class="sxs-lookup"><span data-stu-id="14c81-134">The **[Templating SDK's](sdk.md)** will exist on all supported Adaptive Card platforms.</span></span> <span data-ttu-id="14c81-135">Questi SDK consentono di popolare un modello con dati reali, nel back-end o direttamente nel client.</span><span class="sxs-lookup"><span data-stu-id="14c81-135">These SDKs allow you to populate a template with real data, on the back-end or directly on the client.</span></span> 
3. <span data-ttu-id="14c81-136">Il **[servizio modelli](service.md)** è un modello di verifica che consente a chiunque di trovare, contribuire e condividere un set di modelli ben noti.</span><span class="sxs-lookup"><span data-stu-id="14c81-136">The **[Template Service](service.md)** is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

## <a name="template-language"></a><span data-ttu-id="14c81-137">Linguaggio del modello</span><span class="sxs-lookup"><span data-stu-id="14c81-137">Template Language</span></span>

<span data-ttu-id="14c81-138">Il linguaggio del modello è la sintassi usata per creare un modello di scheda adattiva.</span><span class="sxs-lookup"><span data-stu-id="14c81-138">The template language is the syntax used to author an Adaptive Card template.</span></span> 

> [!NOTE]
> 
> <span data-ttu-id="14c81-139">Segui l'esempio riportato di seguito aprendo una nuova scheda all'indirizzo</span><span class="sxs-lookup"><span data-stu-id="14c81-139">Follow along with the example below by opening up a new tab to</span></span>
>
> **https://adaptivecards.io/designer**
> 
> <span data-ttu-id="14c81-140">Fai clic sul pulsante **Preview Mode** (Modalità di anteprima) per alternare tra la modalità di progettazione e la modalità di anteprima.</span><span class="sxs-lookup"><span data-stu-id="14c81-140">Click the **Preview Mode** button to toggle between design-mode and preview-mode.</span></span>

![Screenshot di Designer](content/2019-08-01-13-58-27.png)

<span data-ttu-id="14c81-142">Il componente Designer appena aggiornato aggiunge il supporto per la creazione di modelli e fornisce **dati di esempio** per visualizzare l'anteprima della scheda in fase di progettazione.</span><span class="sxs-lookup"><span data-stu-id="14c81-142">The newly updated Designer adds support for authoring templates and providing **Sample Data** to preview the card at design-time.</span></span>

<span data-ttu-id="14c81-143">Incolla l'esempio seguente nel riquadro **Card Payload Editor** (Editor payload scheda):</span><span class="sxs-lookup"><span data-stu-id="14c81-143">Paste the example below into the **Card Payload Editor** pane:</span></span> 

<span data-ttu-id="14c81-144">**EmployeeCardTemplate.json**</span><span class="sxs-lookup"><span data-stu-id="14c81-144">**EmployeeCardTemplate.json**</span></span>

```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "ColumnSet",
            "style": "accent",
            "bleed": true,
            "columns": [
                {
                    "type": "Column",
                    "width": "auto",
                    "items": [
                        {
                            "type": "Image",
                            "url": "${photo}",
                            "altText": "Profile picture",
                            "size": "Small",
                            "style": "Person"
                        }
                    ]
                },
                {
                    "type": "Column",
                    "width": "stretch",
                    "items": [
                        {
                            "type": "TextBlock",
                            "text": "Hi ${name}!",
                            "size": "Medium"
                        },
                        {
                            "type": "TextBlock",
                            "text": "Here's a bit about your org...",
                            "spacing": "None"
                        }
                    ]
                }
            ]
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: **${manager.name}**"
        },
        {
            "type": "TextBlock",
            "text": "Your peers are:"
        },
        {
            "type": "FactSet",
            "facts": [
                {
                    "$data": "${peers}",
                    "title": "${name}",
                    "value": "${title}"
                }
            ]
        }
    ]
}
```

<span data-ttu-id="14c81-145">Quindi incolla i dati JSON seguenti in **Sample Data Editor** (Editor dati di esempio).</span><span class="sxs-lookup"><span data-stu-id="14c81-145">Then paste the JSON data below into the **Sample Data Editor**.</span></span> 

<span data-ttu-id="14c81-146">I **dati di esempio** ti consentono di vedere esattamente come verrà visualizzata la scheda in fase di esecuzione quando verranno passati i dati effettivi.</span><span class="sxs-lookup"><span data-stu-id="14c81-146">**Sample Data** helps you see exactly how your card will appear at runtime when passed actual data.</span></span>

<span data-ttu-id="14c81-147">**EmployeeData**</span><span class="sxs-lookup"><span data-stu-id="14c81-147">**EmployeeData**</span></span>

```json
{
    "name": "Matt",
    "photo": "https://pbs.twimg.com/profile_images/3647943215/d7f12830b3c17a5a9e4afcc370e3a37e_400x400.jpeg",
    "manager": {
        "name": "Thomas",
        "title": "PM Lead"
    },
    "peers": [
        {
            "name": "Lei",
            "title": "Sr Program Manager"
        },
        {
            "name": "Andrew",
            "title": "Program Manager II"
        },
        {
            "name": "Mary Anne",
            "title": "Program Manager"
        }
    ]
}
```

<span data-ttu-id="14c81-148">Fai clic sul pulsante **Preview Mode** (Modalità di anteprima).</span><span class="sxs-lookup"><span data-stu-id="14c81-148">Click the **Preview Mode** button.</span></span> <span data-ttu-id="14c81-149">Dovrebbe essere eseguito il rendering della scheda in base ai dati di esempio forniti prima.</span><span class="sxs-lookup"><span data-stu-id="14c81-149">You should see the card render according to the sample data provided above.</span></span> <span data-ttu-id="14c81-150">Apporta qualsiasi modifica ai dati di esempio. Come puoi vedere, la scheda viene aggiornata in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="14c81-150">Feel free to make tweaks to the sample data and watch the card update in realtime.</span></span>

<span data-ttu-id="14c81-151">**Congratulazioni**, hai appena creato il tuo primo modello di scheda adattiva.</span><span class="sxs-lookup"><span data-stu-id="14c81-151">**Congratulations**, you just authored your first Adaptive Card Template!</span></span> <span data-ttu-id="14c81-152">Vediamo ora come popolare il modello con dati reali.</span><span class="sxs-lookup"><span data-stu-id="14c81-152">Next let's learn how to populate the template with real data.</span></span>

> <span data-ttu-id="14c81-153">Scopri di più sul [linguaggio del modello](language.md)</span><span class="sxs-lookup"><span data-stu-id="14c81-153">Learn more about the [template language](language.md)</span></span>

## <a name="sdk-support"></a><span data-ttu-id="14c81-154">SDK supportati</span><span class="sxs-lookup"><span data-stu-id="14c81-154">SDK support</span></span>

<span data-ttu-id="14c81-155">Gli SDK di creazione modelli rendono possibile popolare un modello con dati reali.</span><span class="sxs-lookup"><span data-stu-id="14c81-155">The Templating SDKs make it possible to populate a template with real-data.</span></span>

> [!NOTE]
>
> <span data-ttu-id="14c81-156">Al momento, gli SDK per la creazione di modelli sono disponibili per .NET e NodeJS.</span><span class="sxs-lookup"><span data-stu-id="14c81-156">At this time templating SDKs are available for .NET and NodeJS.</span></span> <span data-ttu-id="14c81-157">Nel tempo gli SDK per la creazione di modelli verranno rilasciati per tutte le rimanenti piattaforme di Schede adattive, ad esempio iOS, Android, UWP e così via.</span><span class="sxs-lookup"><span data-stu-id="14c81-157">Over time we will release templating SDKs for all remaining Adaptive Cards platform, like iOS, Android, UWP, etc.</span></span>

<span data-ttu-id="14c81-158">Piattaforma</span><span class="sxs-lookup"><span data-stu-id="14c81-158">Platform</span></span> | <span data-ttu-id="14c81-159">Pacchetto</span><span class="sxs-lookup"><span data-stu-id="14c81-159">Package</span></span> | <span data-ttu-id="14c81-160">Installa</span><span class="sxs-lookup"><span data-stu-id="14c81-160">Install</span></span> | <span data-ttu-id="14c81-161">Documentazione</span><span class="sxs-lookup"><span data-stu-id="14c81-161">Documentation</span></span>
--- | --- | --- | ---
<span data-ttu-id="14c81-162">JavaScript</span><span class="sxs-lookup"><span data-stu-id="14c81-162">JavaScript</span></span> | <span data-ttu-id="14c81-163">[![Installazione di NPM](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)</span><span class="sxs-lookup"><span data-stu-id="14c81-163">[![npm install](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)</span></span> | `npm install adaptivecards-templating` | [<span data-ttu-id="14c81-164">Documentazione</span><span class="sxs-lookup"><span data-stu-id="14c81-164">Documentation</span></span>](https://www.npmjs.com/package/adaptivecards-templating)
<span data-ttu-id="14c81-165">.NET</span><span class="sxs-lookup"><span data-stu-id="14c81-165">.NET</span></span> | <span data-ttu-id="14c81-166">[![Installazione di Nuget](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)</span><span class="sxs-lookup"><span data-stu-id="14c81-166">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)</span></span> | `dotnet add package AdaptiveCards.Templating` | [<span data-ttu-id="14c81-167">Documentazione</span><span class="sxs-lookup"><span data-stu-id="14c81-167">Documentation</span></span>](https://docs.microsoft.com/adaptive-cards/templating/sdk#net)

### <a name="javascript-example"></a><span data-ttu-id="14c81-168">Esempio di JavaScript</span><span class="sxs-lookup"><span data-stu-id="14c81-168">JavaScript Example</span></span>

<span data-ttu-id="14c81-169">Il codice JavaScript seguente illustra il criterio generale che verrà usato per popolare un modello con dati.</span><span class="sxs-lookup"><span data-stu-id="14c81-169">The JavaScript below shows the general pattern that will be used to populate a template with data.</span></span>

```js
var template = new ACData.Template({ 
    // Card Template JSON
});

var card = template.expand({
    $root: {
        // Data Fields
    }
});

// Now you have an AdaptiveCard ready to render!
```

### <a name="c-example"></a><span data-ttu-id="14c81-170">Esempio di C#</span><span class="sxs-lookup"><span data-stu-id="14c81-170">C# Example</span></span>

<span data-ttu-id="14c81-171">Il codice C# seguente illustra il criterio generale che verrà usato per popolare un modello con dati.</span><span class="sxs-lookup"><span data-stu-id="14c81-171">The C# below shows the general pattern that will be used to populate a template with data.</span></span>

```csharp
var template = new AdaptiveCards.Templating.AdaptiveCardTemplate(cardJson);
   
var card = template.Expand(new {Key="Value"});

// Now you have an AdaptiveCard ready to render!
```

> <span data-ttu-id="14c81-172">Scopri di più sugli [SDK di creazione modelli](sdk.md)</span><span class="sxs-lookup"><span data-stu-id="14c81-172">Learn more about the [templating SDKs](sdk.md)</span></span>

## <a name="template-service"></a><span data-ttu-id="14c81-173">Servizio modelli</span><span class="sxs-lookup"><span data-stu-id="14c81-173">Template Service</span></span>

<span data-ttu-id="14c81-174">Il servizio modelli di Schede adattive è un modello di verifica che consente a chiunque di trovare, contribuire e condividere un set di modelli ben noti.</span><span class="sxs-lookup"><span data-stu-id="14c81-174">The Adaptive Cards Template Service is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

<span data-ttu-id="14c81-175">È utile se vuoi visualizzare alcuni dati, ma senza scrivere appositamente una scheda adattiva personalizzata.</span><span class="sxs-lookup"><span data-stu-id="14c81-175">It's useful if you want to display some data but don't want to bother writing a custom Adaptive Card for it.</span></span>

<span data-ttu-id="14c81-176">L'API per ottenere un modello è abbastanza semplice, ma il servizio in realtà offre molto di più, inclusa la possibilità di analizzare i dati e trovare un modello che potrebbe funzionare per specifiche esigenze.</span><span class="sxs-lookup"><span data-stu-id="14c81-176">The API to get a template is straight-forward enough, but the service actually offers much more, including the ability to analyze your data and find a template that might work for you.</span></span>

`HTTP GET https://templates.adaptivecards.io/graph.microsoft.com/Profile.json`

<span data-ttu-id="14c81-177">Tutti i modelli sono file JSON flat archiviati in un repository di GitHub in modo che chiunque possa contribuirvi come per qualsiasi altro codice open source.</span><span class="sxs-lookup"><span data-stu-id="14c81-177">All templates are flat JSON files stored in a GitHub repo so anyone can contribute to them like any other open source code.</span></span>

> <span data-ttu-id="14c81-178">Scopri di più sul [servizio modelli](service.md)</span><span class="sxs-lookup"><span data-stu-id="14c81-178">Learn more about the [card template Service](service.md)</span></span>

## <a name="whats-next-and-sending-feedback"></a><span data-ttu-id="14c81-179">Passaggi successivi e invio di feedback</span><span class="sxs-lookup"><span data-stu-id="14c81-179">What's next and sending feedback</span></span>

<span data-ttu-id="14c81-180">La creazione di modelli e la separazione della presentazione dai dati ci avvicinano di molto alla nostra mission: "un ecosistema standardizzato per lo scambio di contenuti tra app e servizi".</span><span class="sxs-lookup"><span data-stu-id="14c81-180">Templating and the separation of presentation from data takes us a whole lot closer toward our mission: "an ecosystem standardized content exchange between apps and services".</span></span> <span data-ttu-id="14c81-181">In quest'area sono disponibili molte informazioni, quindi continua a seguire la pagina e condividi con noi la tua esperienza con [GitHub](https://github.com/Microsoft/AdaptiveCards/issues).</span><span class="sxs-lookup"><span data-stu-id="14c81-181">We've got plenty to deliver in this area, so stay tuned and let us know how it's working for you on [GitHub](https://github.com/Microsoft/AdaptiveCards/issues)!</span></span>
