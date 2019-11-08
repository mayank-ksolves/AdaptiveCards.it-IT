---
title: Panoramica della creazione di modelli
author: matthidinger
ms.author: mahiding
ms.date: 07/29/2019
ms.topic: article
ms.openlocfilehash: 11ade4c2a41111f372873ea9a0677fe823c5b0ab
ms.sourcegitcommit: 16a274ce5596001a1c5ab252d9d2a3db6a5a9a0d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73750418"
---
# <a name="adaptive-cards-templating-preview"></a><span data-ttu-id="f0537-102">Creazione di modelli di Schede adattive (anteprima)</span><span class="sxs-lookup"><span data-stu-id="f0537-102">Adaptive Cards Templating (Preview)</span></span>

<span data-ttu-id="f0537-103">Siamo lieti di condividere un'anteprima dei nuovi strumenti che ti aiuteranno a **creare**, **,riutilizzare** e **condividere** Schede adattive.</span><span class="sxs-lookup"><span data-stu-id="f0537-103">We're excited to share a preview of new tools that will help you **create**, **reuse**, and **share** Adaptive Cards.</span></span> 

> [!IMPORTANT] 
> 
> <span data-ttu-id="f0537-104">Queste funzionalità sono disponibili **in anteprima e sono soggette a modifiche**.</span><span class="sxs-lookup"><span data-stu-id="f0537-104">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="f0537-105">Il tuo feedback non solo è apprezzato, ma è anche fondamentale per aiutarci a offrire le funzionalità di cui **tu** hai bisogno.</span><span class="sxs-lookup"><span data-stu-id="f0537-105">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

## <a name="how-can-templating-help-you"></a><span data-ttu-id="f0537-106">Quali sono i vantaggi della creazione di modelli?</span><span class="sxs-lookup"><span data-stu-id="f0537-106">How can templating help you?</span></span>

<span data-ttu-id="f0537-107">La creazione di modelli consente di separare i **dati** dal **layout** in una scheda adattiva.</span><span class="sxs-lookup"><span data-stu-id="f0537-107">Templating enables the separation of **data** from the **layout** in an Adaptive Card.</span></span> 

### <a name="it-helps-design-a-card-once-and-then-populate-it-with-real-data"></a><span data-ttu-id="f0537-108">Permette di progettare una scheda una sola volta e quindi di popolarla con dati reali</span><span class="sxs-lookup"><span data-stu-id="f0537-108">It helps design a card once, and then populate it with real data</span></span>

<span data-ttu-id="f0537-109">Oggi non è possibile creare una scheda tramite [Designer di Schede adattive](https://adaptivecards.io/designer) e usare questo codice JSON per popolare il payload con **contenuto dinamico**.</span><span class="sxs-lookup"><span data-stu-id="f0537-109">Today it's impossible to create a card using the [Adaptive Card Designer](https://adaptivecards.io/designer) and use that JSON to populate the payload with **dynamic content**.</span></span> <span data-ttu-id="f0537-110">Per ottenere questo risultato, è necessario scrivere codice personalizzato per compilare una stringa JSON oppure usare gli SDK del modello a oggetti per creare un modello a oggetti che rappresenta la scheda, quindi serializzarlo in JSON.</span><span class="sxs-lookup"><span data-stu-id="f0537-110">In order to achieve this you must write custom code to build a JSON string, or use the Object Model SDKs to build an OM representing your card and serialize it to JSON.</span></span> <span data-ttu-id="f0537-111">In entrambi i casi, Designer offre un'operazione unidirezionale da eseguire una sola volta e non semplifica la modifica della progettazione della scheda in un secondo momento dopo la conversione in codice.</span><span class="sxs-lookup"><span data-stu-id="f0537-111">In either case the Designer is a one-time one-way operation and doesn't make it easy to tweak the card design later once you've converted it to code.</span></span>

### <a name="it-makes-tranmissions-over-the-wire-smaller"></a><span data-ttu-id="f0537-112">Riduce le dimensioni delle trasmissioni in rete</span><span class="sxs-lookup"><span data-stu-id="f0537-112">It makes tranmissions over the wire smaller</span></span>

<span data-ttu-id="f0537-113">Immagina un mondo in cui sia possibile combinare un modello e i dati **direttamente nel client**.</span><span class="sxs-lookup"><span data-stu-id="f0537-113">Imagine a world where a template and data can be combined **directly on the client**.</span></span> <span data-ttu-id="f0537-114">Significa che se usi lo stesso modello più volte, oppure vuoi aggiornarlo con nuovi dati, è sufficiente inviare i nuovi dati al dispositivo e quindi riutilizzare lo stesso modello più volte.</span><span class="sxs-lookup"><span data-stu-id="f0537-114">This means if you use the same template multiple times, or want to update it with new data, you just need to send new data to the device and it can re-use the same template over and over.</span></span>

### <a name="it-helps-you-create-a-great-looking-card-from-just-the-data-you-provide"></a><span data-ttu-id="f0537-115">Consente di creare una scheda dall'aspetto accattivante solo dai dati forniti</span><span class="sxs-lookup"><span data-stu-id="f0537-115">It helps you create a great looking card from just the data you provide</span></span>

<span data-ttu-id="f0537-116">Le schede adattive sono fantastiche, ma se fosse possibile evitare di scriverne una per ogni contenuto da visualizzare agli utenti?</span><span class="sxs-lookup"><span data-stu-id="f0537-116">We think Adaptive Cards are great, but what if you didn't have to write an Adaptive Card for everything you want to display to a user?</span></span> <span data-ttu-id="f0537-117">Con un servizio di modelli (descritto di seguito) possiamo creare un mondo in cui tutti possono contribuire, scoprire e condividere modelli per qualsiasi tipo di dati.</span><span class="sxs-lookup"><span data-stu-id="f0537-117">With a template service (described below) we can create a world where everyone can contribute, discover, and share templates over any type of data.</span></span> 

<span data-ttu-id="f0537-118">Condividi all'interno dei progetti, nell'organizzazione o con l'intera rete Internet.</span><span class="sxs-lookup"><span data-stu-id="f0537-118">Share within your own projects, your organization, or with the entire internet.</span></span>

### <a name="ai-and-other-services-could-improve-user-experiences"></a><span data-ttu-id="f0537-119">L'intelligenza artificiale e altri servizi potrebbero migliorare l'esperienza utente</span><span class="sxs-lookup"><span data-stu-id="f0537-119">AI and other services could improve user experiences</span></span>

<span data-ttu-id="f0537-120">Separando i dati dal contenuto, l'intelligenza artificiale e altri servizi possono "ragionare" sui dati nelle schede che vediamo e migliorare la produttività degli utenti o aiutarci a trovare quello che cerchiamo.</span><span class="sxs-lookup"><span data-stu-id="f0537-120">By separating data from content it opens a door for AI and other services to  "reason" over the data in the cards we see and enhance user productivity or help us find things.</span></span>

## <a name="what-is-adaptive-cards-templating"></a><span data-ttu-id="f0537-121">Cos'è la creazione di modelli di Schede adattive?</span><span class="sxs-lookup"><span data-stu-id="f0537-121">What is Adaptive Cards Templating?</span></span>

<span data-ttu-id="f0537-122">È costituita da tre componenti principali:</span><span class="sxs-lookup"><span data-stu-id="f0537-122">It's comprised of 3 major components:</span></span>

1. <span data-ttu-id="f0537-123">Il **[linguaggio del modello](language.md)** è la sintassi usata per la creazione di un modello.</span><span class="sxs-lookup"><span data-stu-id="f0537-123">The **[Template Language](language.md)** is the syntax used for authoring a template.</span></span> <span data-ttu-id="f0537-124">Designer consente anche di visualizzare in anteprima i modelli in fase di progettazione includendo "dati di esempio".</span><span class="sxs-lookup"><span data-stu-id="f0537-124">The Designer even lets you preview your templates at design time by including "sample data".</span></span>
2. <span data-ttu-id="f0537-125">Gli **[SDK di creazione modelli](sdk.md)** esistono in tutte le piattaforma di Schede adattive supportate.</span><span class="sxs-lookup"><span data-stu-id="f0537-125">The **[Templating SDK's](sdk.md)** will exist on all supported Adaptive Card platforms.</span></span> <span data-ttu-id="f0537-126">Questi SDK consentono di popolare un modello con dati reali, nel back-end o direttamente nel client.</span><span class="sxs-lookup"><span data-stu-id="f0537-126">These SDKs allow you to populate a template with real data, on the back-end or directly on the client.</span></span> 
3. <span data-ttu-id="f0537-127">Il **[servizio modelli](service.md)** è un modello di verifica che consente a chiunque di trovare, contribuire e condividere un set di modelli ben noti.</span><span class="sxs-lookup"><span data-stu-id="f0537-127">The **[Template Service](service.md)** is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

## <a name="template-language"></a><span data-ttu-id="f0537-128">Linguaggio del modello</span><span class="sxs-lookup"><span data-stu-id="f0537-128">Template Language</span></span>

<span data-ttu-id="f0537-129">Il linguaggio del modello è la sintassi usata per creare un modello di scheda adattiva.</span><span class="sxs-lookup"><span data-stu-id="f0537-129">The template langauge is the syntax used to author an Adaptive Card template.</span></span> 

> [!NOTE]
> 
> <span data-ttu-id="f0537-130">Segui l'esempio riportato di seguito aprendo una nuova scheda all'indirizzo</span><span class="sxs-lookup"><span data-stu-id="f0537-130">Follow along with the example below by opening up a new tab to</span></span>
>
> **https://adaptivecards.io/designer**
> 
> <span data-ttu-id="f0537-131">Fai clic sul pulsante **Preview Mode** (Modalità di anteprima) per alternare tra la modalità di progettazione e la modalità di anteprima.</span><span class="sxs-lookup"><span data-stu-id="f0537-131">Click the **Preview Mode** button to toggle between design-mode and preview-mode.</span></span>

![Screenshot di Designer](content/2019-08-01-13-58-27.png)

<span data-ttu-id="f0537-133">Il componente Designer appena aggiornato aggiunge il supporto per la creazione di modelli e fornisce **dati di esempio** per visualizzare l'anteprima della scheda in fase di progettazione.</span><span class="sxs-lookup"><span data-stu-id="f0537-133">The newly updated Designer adds support for authoring templates and providing **Sample Data** to preview the card at design-time.</span></span>

<span data-ttu-id="f0537-134">Incolla l'esempio seguente nel riquadro **Card Payload Editor** (Editor payload scheda):</span><span class="sxs-lookup"><span data-stu-id="f0537-134">Paste the example below into the **Card Payload Editor** pane:</span></span> 

<span data-ttu-id="f0537-135">**EmployeeCardTemplate.json**</span><span class="sxs-lookup"><span data-stu-id="f0537-135">**EmployeeCardTemplate.json**</span></span>

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
                            "url": "{photo}",
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
                            "text": "Hi {name}!",
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
            "text": "Your manager is: **{manager.name}**"
        },
        {
            "type": "TextBlock",
            "text": "Your peers are:"
        },
        {
            "type": "FactSet",
            "facts": [
                {
                    "$data": "{peers}",
                    "title": "{name}",
                    "value": "{title}"
                }
            ]
        }
    ]
}
```

<span data-ttu-id="f0537-136">Quindi incolla i dati JSON seguenti in **Sample Data Editor** (Editor dati di esempio).</span><span class="sxs-lookup"><span data-stu-id="f0537-136">Then paste the JSON data below into the **Sample Data Editor**.</span></span> 

<span data-ttu-id="f0537-137">I **dati di esempio** ti consentono di vedere esattamente come verrà visualizzata la scheda in fase di esecuzione quando verranno passati i dati effettivi.</span><span class="sxs-lookup"><span data-stu-id="f0537-137">**Sample Data** helps you see exactly how your card will appear at runtime when passed actual data.</span></span>

<span data-ttu-id="f0537-138">**EmployeeData**</span><span class="sxs-lookup"><span data-stu-id="f0537-138">**EmployeeData**</span></span>

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

<span data-ttu-id="f0537-139">Fai clic sul pulsante **Preview Mode** (Modalità di anteprima).</span><span class="sxs-lookup"><span data-stu-id="f0537-139">Click the **Preview Mode** button.</span></span> <span data-ttu-id="f0537-140">Dovrebbe essere eseguito il rendering della scheda in base ai dati di esempio forniti prima.</span><span class="sxs-lookup"><span data-stu-id="f0537-140">You should see the card render according to the sample data provided above.</span></span> <span data-ttu-id="f0537-141">Apporta qualsiasi modifica ai dati di esempio. Come puoi vedere, la scheda viene aggiornata in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="f0537-141">Feel free to make tweaks to the sample data and watch the card update in realtime.</span></span>

<span data-ttu-id="f0537-142">**Congratulazioni**, hai appena creato il tuo primo modello di scheda adattiva.</span><span class="sxs-lookup"><span data-stu-id="f0537-142">**Congratulations**, you just authored your first Adaptive Card Template!</span></span> <span data-ttu-id="f0537-143">Vediamo ora come popolare il modello con dati reali.</span><span class="sxs-lookup"><span data-stu-id="f0537-143">Next let's learn how to populate the template with real data.</span></span>

> <span data-ttu-id="f0537-144">Scopri di più sul [linguaggio del modello](language.md)</span><span class="sxs-lookup"><span data-stu-id="f0537-144">Learn more about the [template language](language.md)</span></span>

## <a name="sdk-support"></a><span data-ttu-id="f0537-145">SDK supportati</span><span class="sxs-lookup"><span data-stu-id="f0537-145">SDK support</span></span>

<span data-ttu-id="f0537-146">Gli SDK di creazione modelli rendono possibile popolare un modello con dati reali.</span><span class="sxs-lookup"><span data-stu-id="f0537-146">The Templating SDKs make it possible to populate a template with real-data.</span></span>

> [!NOTE]
>
> <span data-ttu-id="f0537-147">Durante l'anteprima iniziale è disponibile solo un set limitato di SDK.</span><span class="sxs-lookup"><span data-stu-id="f0537-147">During the initial preview we only have a limited set of SDKs available.</span></span> <span data-ttu-id="f0537-148">Al momento del rilascio, ci saranno librerie di modelli per ogni piattaforma di Schede adattive supportate.</span><span class="sxs-lookup"><span data-stu-id="f0537-148">When we release there will be templating libraries for every supported Adaptive Cards platform.</span></span>

<span data-ttu-id="f0537-149">Piattaforma</span><span class="sxs-lookup"><span data-stu-id="f0537-149">Platform</span></span> | <span data-ttu-id="f0537-150">Installazione</span><span class="sxs-lookup"><span data-stu-id="f0537-150">Install</span></span> | <span data-ttu-id="f0537-151">Documentazione</span><span class="sxs-lookup"><span data-stu-id="f0537-151">Documentation</span></span>
--- | --- | ---
<span data-ttu-id="f0537-152">JavaScript</span><span class="sxs-lookup"><span data-stu-id="f0537-152">JavaScript</span></span> | `npm install adaptivecards-templating` | [<span data-ttu-id="f0537-153">Documentazione</span><span class="sxs-lookup"><span data-stu-id="f0537-153">Documentation</span></span>](https://www.npmjs.com/package/adaptivecards-templating)
<span data-ttu-id="f0537-154">.NET</span><span class="sxs-lookup"><span data-stu-id="f0537-154">.NET</span></span> | `nuget install AdaptiveCards.Templating` | [<span data-ttu-id="f0537-155">Documentazione</span><span class="sxs-lookup"><span data-stu-id="f0537-155">Documentation</span></span>](https://docs.microsoft.com/en-us/adaptive-cards/templating/sdk#net)

### <a name="javascript-example"></a><span data-ttu-id="f0537-156">Esempio di JavaScript</span><span class="sxs-lookup"><span data-stu-id="f0537-156">JavaScript Example</span></span>

<span data-ttu-id="f0537-157">Il codice JavaScript seguente illustra il criterio generale che verrà usato per popolare un modello con dati.</span><span class="sxs-lookup"><span data-stu-id="f0537-157">The JavaScript below shows the general pattern that will be used to populate a template with data.</span></span>

```js
var template = new ACData.Template({ 
    // EmployeeCardTemplate goes here
});

var dataContext = new ACData.EvaluationContext();
dataContext.$root = {
    // Data goes here
};

var card = template.expand(dataContext);
// Now you have an AdaptiveCard ready to render!
```

> <span data-ttu-id="f0537-158">Scopri di più sugli [SDK di creazione modelli](sdk.md)</span><span class="sxs-lookup"><span data-stu-id="f0537-158">Learn more about the [templating SDKs](sdk.md)</span></span>

## <a name="template-service"></a><span data-ttu-id="f0537-159">Servizio modelli</span><span class="sxs-lookup"><span data-stu-id="f0537-159">Template Service</span></span>

<span data-ttu-id="f0537-160">Il servizio modelli di Schede adattive è un modello di verifica che consente a chiunque di trovare, contribuire e condividere un set di modelli ben noti.</span><span class="sxs-lookup"><span data-stu-id="f0537-160">The Adaptive Cards Template Service is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

<span data-ttu-id="f0537-161">È utile se vuoi visualizzare alcuni dati, ma senza scrivere appositamente una scheda adattiva personalizzata.</span><span class="sxs-lookup"><span data-stu-id="f0537-161">It's useful if you want to display some data but don't want to bother writing a custom Adaptive Card for it.</span></span>

<span data-ttu-id="f0537-162">L'API per ottenere un modello è abbastanza semplice, ma il servizio in realtà offre molto di più, inclusa la possibilità di analizzare i dati e trovare un modello che potrebbe funzionare per specifiche esigenze.</span><span class="sxs-lookup"><span data-stu-id="f0537-162">The API to get a template is straight-forward enough, but the service actually offers much more, including the ability to analyze your data and find a template that might work for you.</span></span>

`HTTP GET https://templates.adaptivecards.io/graph.microsoft.com/Profile.json`

<span data-ttu-id="f0537-163">Tutti i modelli sono file JSON flat archiviati in un repository di GitHub in modo che chiunque possa contribuirvi come per qualsiasi altro codice open source.</span><span class="sxs-lookup"><span data-stu-id="f0537-163">All templates are flat JSON files stored in a GitHub repo so anyone can contribute to them like any other open source code.</span></span>

> <span data-ttu-id="f0537-164">Scopri di più sul [servizio modelli](service.md)</span><span class="sxs-lookup"><span data-stu-id="f0537-164">Learn more about the [card template Service](service.md)</span></span>

## <a name="whats-next-and-sending-feedback"></a><span data-ttu-id="f0537-165">Passaggi successivi e invio di feedback</span><span class="sxs-lookup"><span data-stu-id="f0537-165">What's next and sending feedback</span></span>

<span data-ttu-id="f0537-166">La creazione di modelli e la separazione della presentazione dai dati ci avvicinano di molto alla nostra mission: "un ecosistema per lo scambio di contenuti di schede in modo comune e coerente".</span><span class="sxs-lookup"><span data-stu-id="f0537-166">Templating and the separation of presentation from data takes us a whole lot closer toward our mission: "an ecosystem for exchanging card content in a common and consistent way".</span></span>

<span data-ttu-id="f0537-167">Condivideremo altre informazioni non appena possibile.</span><span class="sxs-lookup"><span data-stu-id="f0537-167">We're eager to share more as soon as we can.</span></span> <span data-ttu-id="f0537-168">Nel frattempo, invia il tuo feedback qui, [GitHub](https://github.com/microsoft/AdaptiveCards) o Twitter **[@MattHidinger](https://twitter.com/matthidinger)** / **#AdaptiveCards**.</span><span class="sxs-lookup"><span data-stu-id="f0537-168">In the meantime please give feedback here, [GitHub](https://github.com/microsoft/AdaptiveCards), or Twitter **[@MattHidinger](https://twitter.com/matthidinger)**/**#AdaptiveCards**.</span></span> 
