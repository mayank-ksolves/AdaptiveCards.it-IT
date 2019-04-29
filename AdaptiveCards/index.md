---
title: Panoramica delle schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 545d22a9dd2208d0a506f05943cd5ed9dd3de437
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552303"
---
# <a name="adaptive-cards-overview"></a><span data-ttu-id="78322-102">Panoramica delle schede adattive</span><span class="sxs-lookup"><span data-stu-id="78322-102">Adaptive Cards Overview</span></span> 

<span data-ttu-id="78322-103">Le schede adattive sono un formato aperto per lo scambio di schede che consente agli sviluppatori di scambiare contenuti dell'interfaccia utente in un modo coerente e comune.</span><span class="sxs-lookup"><span data-stu-id="78322-103">Adaptive Cards are an open card exchange format enabling developers to exchange UI content in a common and consistent way.</span></span>

<video controls width="100%" poster="./content/videoposter.png">
    <source src="https://adaptivecardsblob.blob.core.windows.net/assets/AdaptiveCardsOverviewVideo.mp4" type="video/mp4">
</video>

## <a name="how-they-work"></a><span data-ttu-id="78322-104">Come funzionano</span><span class="sxs-lookup"><span data-stu-id="78322-104">How they work</span></span>

<span data-ttu-id="78322-105">Gli [**autori di schede**](authoring-cards/getting-started.md) descrivono il contenuto come un semplice oggetto JSON.</span><span class="sxs-lookup"><span data-stu-id="78322-105">[**Card Authors**](authoring-cards/getting-started.md) describe their content as a simple JSON object.</span></span> <span data-ttu-id="78322-106">Tale contenuto verrà quindi sottoposto a rendering in modo nativo all'interno un'[**applicazione host**](rendering-cards/getting-started.md), adattandolo automaticamente all'aspetto dell'host.</span><span class="sxs-lookup"><span data-stu-id="78322-106">That content can then be rendered natively inside a [**Host Application**](rendering-cards/getting-started.md), automatically adapting to the look and feel of the Host.</span></span>

<span data-ttu-id="78322-107">Ad esempio, Contoso Bot può creare una scheda adattiva tramite Bot Framework. Quando viene recapitata a Skype, avrà l'aspetto di una scheda di Skype.</span><span class="sxs-lookup"><span data-stu-id="78322-107">For example, Contoso Bot can author an Adaptive Card through the Bot Framework, and when delivered to Skype, it will look and feel like a Skype card.</span></span> <span data-ttu-id="78322-108">Se lo stesso payload viene inviato a Microsoft Teams, avrà un aspetto coerente con Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="78322-108">When that same payload is sent to Microsoft Teams, it will look and feel like Microsoft Teams.</span></span> <span data-ttu-id="78322-109">Con la diffusione del supporto delle schede adattive da parte di più app host, lo stesso payload verrà attivato automaticamente all'interno di queste applicazioni, sempre con un aspetto nativo per l'app.</span><span class="sxs-lookup"><span data-stu-id="78322-109">As more host apps start to support Adaptive Cards, that same payload will automatically light up inside these applications, yet still feel entirely native to the app.</span></span>

<span data-ttu-id="78322-110">Per gli utenti il vantaggio è che questi elementi hanno un aspetto familiare.</span><span class="sxs-lookup"><span data-stu-id="78322-110">Users win because everything feels familiar.</span></span> <span data-ttu-id="78322-111">Il vantaggio per le app host è la possibilità di controllare l'esperienza utente.</span><span class="sxs-lookup"><span data-stu-id="78322-111">Host apps win because they control the user experience.</span></span> <span data-ttu-id="78322-112">Gli autori di schede hanno l'opportunità di ottenere una maggiore copertura per il contenuto senza lavoro aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="78322-112">And Card Authors win because their content gets broader reach without any additional work.</span></span>

## <a name="goals"></a><span data-ttu-id="78322-113">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="78322-113">Goals</span></span> 

<span data-ttu-id="78322-114">Le schede adattive sono:</span><span class="sxs-lookup"><span data-stu-id="78322-114">The goals for adaptive cards are:</span></span>

* <span data-ttu-id="78322-115">**Portabili** - Per qualsiasi app, dispositivo e framework dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="78322-115">**Portable** - To any app, device, and UI framework</span></span>
* <span data-ttu-id="78322-116">**Aperte** - Librerie e schema sono open source e condivisi</span><span class="sxs-lookup"><span data-stu-id="78322-116">**Open** - Libraries and schema are open source and shared</span></span>
* <span data-ttu-id="78322-117">**Convenienti** - Facili da definire, facili da utilizzare</span><span class="sxs-lookup"><span data-stu-id="78322-117">**Low cost** - Easy to define, easy to consume</span></span>
* <span data-ttu-id="78322-118">**Espressive** - Destinate ai contenuti di ampio spettro che gli sviluppatori desiderano produrre</span><span class="sxs-lookup"><span data-stu-id="78322-118">**Expressive** - Targeted at the long tail of content that developers want to produce</span></span>
* <span data-ttu-id="78322-119">**Puramente dichiarative** - Non è necessario o consentito codice</span><span class="sxs-lookup"><span data-stu-id="78322-119">**Purely declarative** - No code is needed or allowed</span></span>
* <span data-ttu-id="78322-120">**Con stile automatico** - In base alle linee guida per marchio ed esperienza utente dell'applicazione host</span><span class="sxs-lookup"><span data-stu-id="78322-120">**Automatically styled** - To the Host application UX and brand guidelines</span></span>

## <a name="for-card-authors"></a><span data-ttu-id="78322-121">Per gli autori delle schede</span><span class="sxs-lookup"><span data-stu-id="78322-121">For Card Authors</span></span>
<span data-ttu-id="78322-122">Le schede adattive offrono agli autori i vantaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="78322-122">Adaptive Cards are great for card authors:</span></span>

* <span data-ttu-id="78322-123">**Un solo schema** - Un singolo formato che offre la possibilità di ridurre al minimo i costi per la creazione di una scheda, massimizzando il numero di posizioni in cui può essere usata.</span><span class="sxs-lookup"><span data-stu-id="78322-123">**One schema** - You get a single format, minimizing the cost of creating a card and maximizing the number of places it can be used.</span></span>
* <span data-ttu-id="78322-124">**Maggiore libertà di espressione** - Il contenuto può essere allineato al messaggio con maggiore precisione, perché si ha a disposizione una tavolozza più completa.</span><span class="sxs-lookup"><span data-stu-id="78322-124">**Richer expression** - Your content can more closely align with want you want to say because you have a richer palette to paint with.</span></span>
* <span data-ttu-id="78322-125">**Ampia copertura** - Il contenuto sarà supportato da una più vasta gamma di applicazioni senza dover apprendere nuovi schemi.</span><span class="sxs-lookup"><span data-stu-id="78322-125">**Broad reach** - Your content will work across a broader set of applications without you having to learn new schemas.</span></span>
* <span data-ttu-id="78322-126">**Controlli di input** - La scheda può includere controlli di input per raccogliere informazioni dall'utente che la sta visualizzando.</span><span class="sxs-lookup"><span data-stu-id="78322-126">**Input controls** - Your card can include input controls for gathering information from the user that is viewing the card.</span></span>
* <span data-ttu-id="78322-127">**Migliori strumenti** - Un ecosistema aperto significa strumenti migliori condivisi da tutti.</span><span class="sxs-lookup"><span data-stu-id="78322-127">**Better tooling** - An open card ecosystem means better tooling that is shared by everyone.</span></span>

## <a name="for-experience-owners"></a><span data-ttu-id="78322-128">Per i proprietari dell'esperienza</span><span class="sxs-lookup"><span data-stu-id="78322-128">For Experience Owners</span></span>
<span data-ttu-id="78322-129">Gli sviluppatori di app che vogliono attingere a un ecosistema di contenuti di terze parti apprezzeranno le schede adattive per i motivi seguenti:</span><span class="sxs-lookup"><span data-stu-id="78322-129">If you are an app developer who wants to tap into an ecosystem of third-party content you will love Adaptive Cards because:</span></span>

* <span data-ttu-id="78322-130">**Esperienza utente coerente** - Si può garantire un'esperienza coerente per gli utenti, perché si è proprietari dello stile della scheda sottoposta a rendering.</span><span class="sxs-lookup"><span data-stu-id="78322-130">**Consistent user experience** - You guarantee a consistent experience for your users, because you own the style of the rendered card.</span></span>
* <span data-ttu-id="78322-131">**Prestazioni native** - È possibile ottenere prestazioni native grazie all'utilizzo diretto del framework dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="78322-131">**Native performance** - You get native performance as it targets your UI framework directly.</span></span>
* <span data-ttu-id="78322-132">**Sicurezza** - Il contenuto viene distribuito in payload sicuri in modo da non dover aprire il framework dell'interfaccia utente a markup non elaborato e script.</span><span class="sxs-lookup"><span data-stu-id="78322-132">**Safe** - Content is delivered in safe payloads so you don't have to open up your UI framework to raw markup and scripting.</span></span>
* <span data-ttu-id="78322-133">**Facilità di implementazione** - Librerie pronte e facilmente integrabili in qualsiasi piattaforma supportata.</span><span class="sxs-lookup"><span data-stu-id="78322-133">**Easy to implement** - You get off the shelf libraries to easily integrate on any platform you support</span></span> 
* <span data-ttu-id="78322-134">**Documentazione gratuita** - Si risparmia tempo perché non è necessario inventare, implementare e documentare uno schema proprietario.</span><span class="sxs-lookup"><span data-stu-id="78322-134">**Free documentation** - You save time because you don't have invent, implement, and document a proprietary schema.</span></span>
* <span data-ttu-id="78322-135">**Strumenti condivisi** - Si risparmia tempo perché non è necessario creare strumenti personalizzati.</span><span class="sxs-lookup"><span data-stu-id="78322-135">**Shared tooling** - You save time because you don't have to create custom tooling.</span></span>

## <a name="core-design-principles"></a><span data-ttu-id="78322-136">Principi di progettazione di base</span><span class="sxs-lookup"><span data-stu-id="78322-136">Core Design Principles</span></span> 

<span data-ttu-id="78322-137">Le schede adattive sono basate su un set di [principi guida](resources/principles.md) che si sono rivelati utili per mantenere sotto controllo la progettazione.</span><span class="sxs-lookup"><span data-stu-id="78322-137">Adaptive Cards are driven by a set of [guiding principles](resources/principles.md) that have been useful for keeping the design on track.</span></span> 

### <a name="semantic-instead-of-pixel-perfect"></a><span data-ttu-id="78322-138">Semantica invece di perfezione al pixel</span><span class="sxs-lookup"><span data-stu-id="78322-138">Semantic instead of pixel-perfect</span></span>
<span data-ttu-id="78322-139">Si è cercato il più possibile di concentrarsi su valori semantici e concetti, piuttosto che sul puro layout perfetto al pixel.</span><span class="sxs-lookup"><span data-stu-id="78322-139">We have striven as much as possible for semantic values and concepts as opposed to pure pixel-perfect layout.</span></span> <span data-ttu-id="78322-140">Gli esempi di espressione semantica vengono visualizzati in vari colori e dimensioni e in elementi come FactSet e ImageSet.</span><span class="sxs-lookup"><span data-stu-id="78322-140">Examples of semantic expression show up in colors, sizes, and in elements like FactSet and ImageSet.</span></span> <span data-ttu-id="78322-141">Tutti questi elementi consentono all'applicazione host di prendere decisioni migliori sull'aspetto effettivo.</span><span class="sxs-lookup"><span data-stu-id="78322-141">These all allow the host application to make better decisions about the actual look and feel.</span></span>

### <a name="card-authors-own-the-content-host-app-owns-the-look-and-feel"></a><span data-ttu-id="78322-142">Gli autori delle schede sono i proprietari del contenuto, l'app host è proprietaria dell'aspetto</span><span class="sxs-lookup"><span data-stu-id="78322-142">Card Authors own the content, Host App owns the look and feel</span></span>
<span data-ttu-id="78322-143">Gli autori delle schede decidono cosa vogliono dire, ma l'applicazione in cui vengono visualizzate le schede ne determina l'aspetto nel contesto.</span><span class="sxs-lookup"><span data-stu-id="78322-143">The card authors own what they want to say, but the application displaying it owns the look and feel of the card in the context of their application.</span></span>

### <a name="keep-it-simple-but-expressive"></a><span data-ttu-id="78322-144">Semplicità ed espressività</span><span class="sxs-lookup"><span data-stu-id="78322-144">Keep it simple, but expressive</span></span>
<span data-ttu-id="78322-145">Le schede adattive devono essere espressive e generiche, ma l'intenzione non è quella di creare un framework dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="78322-145">We want Adaptive Cards to be expressive and general purpose, but we don't want to build a UI framework.</span></span>  <span data-ttu-id="78322-146">L'obiettivo è realizzare un livello intermedio "sufficientemente espressivo" nello stesso modo in cui Markdown è sufficientemente espressivo per i documenti.</span><span class="sxs-lookup"><span data-stu-id="78322-146">The goal is to create an intermediate layer which is "expressive enough" in the same way Markdown is expressive enough for documents.</span></span>

<span data-ttu-id="78322-147">Focalizzando l'attenzione su semplicità ed espressività, con Markdown si è riusciti a creare una descrizione coerente e semplice del contenuto del documento.</span><span class="sxs-lookup"><span data-stu-id="78322-147">By focusing on keeping it simple and expressive, Markdown created an easy and consistent description of document content.</span></span>  <span data-ttu-id="78322-148">Nello stesso modo, Microsoft ritiene che le schede adattive possano diventare uno strumento semplice ed espressivo per descrivere il contenuto della scheda.</span><span class="sxs-lookup"><span data-stu-id="78322-148">In the same way, we believe that Adaptive Cards can create a simple, expressive means of describing card content.</span></span>

### <a name="when-in-doubt-keep-it-out"></a><span data-ttu-id="78322-149">In caso di dubbi, tralasciare</span><span class="sxs-lookup"><span data-stu-id="78322-149">When in doubt, keep it out</span></span>
<span data-ttu-id="78322-150">È più semplice aggiungere in un secondo momento che convivere con una scelta infelice.</span><span class="sxs-lookup"><span data-stu-id="78322-150">It is easier to add later then it is to live with a mistake.</span></span> <span data-ttu-id="78322-151">Se ci si ritrova a discutere se aggiungere o meno un elemento, è consigliabile decidere di ometterlo.  È sempre più semplice aggiungere una proprietà piuttosto che convivere con una proprietà legacy che sarebbe stato preferibile non dover supportare.</span><span class="sxs-lookup"><span data-stu-id="78322-151">If we found ourselves debating whether we should add something or not, we opted to leave it out.  It is always easier to add a property than to live with a legacy we wish we didn't have to support.</span></span>


## <a name="build-2018-session"></a><span data-ttu-id="78322-152">Sessione dell'evento Build 2018</span><span class="sxs-lookup"><span data-stu-id="78322-152">Build 2018 Session</span></span>

<span data-ttu-id="78322-153">La sessione seguente di Build 2018 presenta le schede adattive nei bot e in Cortana, Outlook e Windows.</span><span class="sxs-lookup"><span data-stu-id="78322-153">The following session at Build 2018 showcases Adaptive Cards in Bots, Cortana, Outlook, and Windows.</span></span> 

<iframe src="https://medius.studios.ms/Embed/Video/BRK2401?SFYT=true" width="960" height="540" allowFullScreen frameBorder="0"></iframe>