---
title: Implementazione di un renderer
author: matthidinger
ms.author: mahiding
ms.date: 09/15/2017
ms.topic: article
ms.openlocfilehash: 607ce40e70e0e54e61a572853a521d2dd70a5c23
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2020
ms.locfileid: "77454914"
---
# <a name="adaptive-card-renderer-specification"></a><span data-ttu-id="d3e32-102">Specifica relativa al renderer di schede adattive</span><span class="sxs-lookup"><span data-stu-id="d3e32-102">Adaptive Card Renderer Specification</span></span>

<span data-ttu-id="d3e32-103">La specifica seguente illustra come implementare un renderer di schede adattive in qualsiasi piattaforma di interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="d3e32-103">The following specification describes how implement an Adaptive Card renderer on any UI platform.</span></span>

> [!IMPORTANT]
> 
> <span data-ttu-id="d3e32-104">Questo contenuto non è ancora definitivo.</span><span class="sxs-lookup"><span data-stu-id="d3e32-104">This content is not finished yet.</span></span> <span data-ttu-id="d3e32-105">Torna a breve.</span><span class="sxs-lookup"><span data-stu-id="d3e32-105">Check back shortly.</span></span>

## <a name="sdk-versioning"></a><span data-ttu-id="d3e32-106">Controllo delle versioni dell'SDK</span><span class="sxs-lookup"><span data-stu-id="d3e32-106">SDK Versioning</span></span>

1. <span data-ttu-id="d3e32-107">La versione principale e quella secondaria dell'SDK **DOVREBBERO** corrispondere alla versione di `schema`.</span><span class="sxs-lookup"><span data-stu-id="d3e32-107">The SDK major and minor version **SHOULD** match the `schema` version.</span></span> 
1. <span data-ttu-id="d3e32-108">La patch/build **DOVREBBE** essere usata per gli aggiornamenti del renderer che non prevedono modifiche relative allo schema.</span><span class="sxs-lookup"><span data-stu-id="d3e32-108">Patch/build **SHOULD** be used for renderer updates that don't have schema changes.</span></span>

## <a name="parsing-json"></a><span data-ttu-id="d3e32-109">Analisi del contenuto JSON</span><span class="sxs-lookup"><span data-stu-id="d3e32-109">Parsing JSON</span></span>

### <a name="error-conditions"></a><span data-ttu-id="d3e32-110">Condizioni di errore</span><span class="sxs-lookup"><span data-stu-id="d3e32-110">Error conditions</span></span>
1. <span data-ttu-id="d3e32-111">Un parser **DEVE** verificare che si tratti di contenuto JSON valido</span><span class="sxs-lookup"><span data-stu-id="d3e32-111">A parser **MUST** check that it's valid JSON content</span></span>
1. <span data-ttu-id="d3e32-112">Un parser **DEVE** eseguire la convalida a fronte dello schema (proprietà obbligatorie e così via)</span><span class="sxs-lookup"><span data-stu-id="d3e32-112">A parser **MUST** validate against the schema (required properties, etc)</span></span>
1. <span data-ttu-id="d3e32-113">Gli errori sopra riportati **DEVONO** essere segnalati all'app host (eccezione o equivalente)</span><span class="sxs-lookup"><span data-stu-id="d3e32-113">The above errors **MUST** be reported to the host app (exception or equivalent)</span></span>

### <a name="unknown-types"></a><span data-ttu-id="d3e32-114">Tipi sconosciuti</span><span class="sxs-lookup"><span data-stu-id="d3e32-114">Unknown types</span></span>
1. <span data-ttu-id="d3e32-115">Se vengono rilevati "tipi" sconosciuti, questi **DEVONO ESSERE ELIMINATI** dal risultato</span><span class="sxs-lookup"><span data-stu-id="d3e32-115">If unknown "types" are encountered they **MUST BE DROPPED** from the result</span></span>
1. <span data-ttu-id="d3e32-116">Eventuali modifiche del payload (come nei casi sopra indicati) **DOVREBBERO** essere segnalate come avvisi all'app host</span><span class="sxs-lookup"><span data-stu-id="d3e32-116">Any alterations of the payload (like above) **SHOULD** be reported as warnings to the host app</span></span>

### <a name="unknown-properties"></a><span data-ttu-id="d3e32-117">Proprietà sconosciute</span><span class="sxs-lookup"><span data-stu-id="d3e32-117">Unknown properties</span></span>
1. <span data-ttu-id="d3e32-118">Un parser **DEVE** includere proprietà **aggiuntive** per gli elementi</span><span class="sxs-lookup"><span data-stu-id="d3e32-118">A parser **MUST** include **additional** properties on elements</span></span>

### <a name="additional-considerations"></a><span data-ttu-id="d3e32-119">Altre considerazioni</span><span class="sxs-lookup"><span data-stu-id="d3e32-119">Additional considerations</span></span>
1. <span data-ttu-id="d3e32-120">La proprietà `speak` può contenere markup SSML e **DEVE** essere restituita all'app host come specificato</span><span class="sxs-lookup"><span data-stu-id="d3e32-120">The `speak` property may contain SSML markup and **MUST** be returned to the host app as-specified</span></span>

## <a name="parsing-host-config"></a><span data-ttu-id="d3e32-121">Analisi della configurazione host</span><span class="sxs-lookup"><span data-stu-id="d3e32-121">Parsing Host Config</span></span>
1. <span data-ttu-id="d3e32-122">TODO</span><span class="sxs-lookup"><span data-stu-id="d3e32-122">TODO</span></span>

## <a name="versioning"></a><span data-ttu-id="d3e32-123">Controllo versioni</span><span class="sxs-lookup"><span data-stu-id="d3e32-123">Versioning</span></span>

1. <span data-ttu-id="d3e32-124">Un renderer **DEVE** implementare una determinata versione dello schema.</span><span class="sxs-lookup"><span data-stu-id="d3e32-124">A renderer **MUST** implement a particular version of the schema.</span></span> 
1. <span data-ttu-id="d3e32-125">Il costruttore `AdaptiveCard`**DEVE** assegnare alla proprietà `version` un valore predefinito in base alla versione corrente dello schema.</span><span class="sxs-lookup"><span data-stu-id="d3e32-125">The `AdaptiveCard` constructor **MUST** give the `version` property a default value based on the current schema version</span></span> 
1. <span data-ttu-id="d3e32-126">Se un renderer rileva una proprietà `version` nell'oggetto `AdaptiveCard` con un valore superiore alla versione supportata, **DEVE** invece restituire l'oggetto `fallbackText`.</span><span class="sxs-lookup"><span data-stu-id="d3e32-126">If a renderer encounters a `version` property in the `AdaptiveCard` that is higher than the supported version, it **MUST** return the `fallbackText` instead.</span></span>

## <a name="rendering"></a><span data-ttu-id="d3e32-127">Rendering</span><span class="sxs-lookup"><span data-stu-id="d3e32-127">Rendering</span></span>

<span data-ttu-id="d3e32-128">Un oggetto `AdaptiveCard` è costituito da un oggetto `body` e da `actions`.</span><span class="sxs-lookup"><span data-stu-id="d3e32-128">An `AdaptiveCard` consists of a `body` and `actions`.</span></span> <span data-ttu-id="d3e32-129">L'oggetto `body` è una raccolta di `CardElement` di cui un renderer eseguirà l'enumerazione e il rendering nell'ordine.</span><span class="sxs-lookup"><span data-stu-id="d3e32-129">The `body` is a collection of `CardElement`s that a renderer will enumerate and render in order.</span></span> 

1. <span data-ttu-id="d3e32-130">Ogni elemento **DEVE** estendersi per la larghezza del relativo elemento padre (pensa a `display: block` in HTML).</span><span class="sxs-lookup"><span data-stu-id="d3e32-130">Each Element **MUST** stretch to the width of its parent (think `display: block` in HTML).</span></span>
1. <span data-ttu-id="d3e32-131">Un renderer **DEVE** ignorare i tipi di elemento sconosciuti e continuare a eseguire il rendering del resto del payload.</span><span class="sxs-lookup"><span data-stu-id="d3e32-131">A renderer **MUST** ignore unknown element types, and continue rendering the rest of the payload.</span></span>

### <a name="spacing-and-separators"></a><span data-ttu-id="d3e32-132">Spaziatura e separatori</span><span class="sxs-lookup"><span data-stu-id="d3e32-132">Spacing and Separators</span></span>

1. <span data-ttu-id="d3e32-133">La proprietà `spacing` di ogni elemento influisce sulla quantità di spazio tra l'elemento **CORRENTE** e quello **PRECEDENTE**.</span><span class="sxs-lookup"><span data-stu-id="d3e32-133">The `spacing` property on every element influences the amount of space between the **CURRENT** element and the one **BEFORE** it.</span></span>
1. <span data-ttu-id="d3e32-134">La spaziatura **DEVE ESSERE APPLICATA SOLO** quando esiste effettivamente un elemento precedente.</span><span class="sxs-lookup"><span data-stu-id="d3e32-134">Spacing **MUST ONLY** apply when there actually is an element preceding it.</span></span> <span data-ttu-id="d3e32-135">Ad esempio, non si applica al primo elemento di una matrice.</span><span class="sxs-lookup"><span data-stu-id="d3e32-135">(E.g., won't apply to the first item in an array)</span></span>
1. <span data-ttu-id="d3e32-136">Un renderer **DEVE** cercare la quantità di spazio da usare dalla spaziatura di `hostConfig` per il valore di enumerazione applicato all'elemento corrente.</span><span class="sxs-lookup"><span data-stu-id="d3e32-136">A renderer **MUST** look up the amount of space to use from the `hostConfig` spacing for the enum value applied to the current element.</span></span>
1. <span data-ttu-id="d3e32-137">Se l'elemento ha un valore `separator` impostato su `true`, **DEVE** essere tracciata una linea visibile tra l'elemento corrente e quello che lo precede.</span><span class="sxs-lookup"><span data-stu-id="d3e32-137">If the element has a `separator` value of `true`, then a visible line **MUST** be drawn between the current element and the one before it.</span></span>
1. <span data-ttu-id="d3e32-138">La linea di separazione **DEVE** essere tracciata con `container.style.default.foregroundColor`.</span><span class="sxs-lookup"><span data-stu-id="d3e32-138">The separator line **MUST** be drawn using the `container.style.default.foregroundColor`.</span></span>
1. <span data-ttu-id="d3e32-139">Un separatore **DEVE ESSERE TRACCIATO SOLO** se l'elemento **NON È** il primo della matrice.</span><span class="sxs-lookup"><span data-stu-id="d3e32-139">A separator **MUST ONLY** be drawn if the item **IS NOT** the first in the array.</span></span>

### <a name="columns"></a><span data-ttu-id="d3e32-140">Colonne</span><span class="sxs-lookup"><span data-stu-id="d3e32-140">Columns</span></span>

1. <span data-ttu-id="d3e32-141">La proprietà `width` di un elemento `Column` **DEVE** essere interpretata da "auto", "stretch" o un rapporto ponderato.</span><span class="sxs-lookup"><span data-stu-id="d3e32-141">`Column` `width` **MUST** be interpreted by "auto", "stretch" or a weighted ratio.</span></span>

### <a name="textblock"></a><span data-ttu-id="d3e32-142">TextBlock</span><span class="sxs-lookup"><span data-stu-id="d3e32-142">TextBlock</span></span>

1. <span data-ttu-id="d3e32-143">Un oggetto TextBlock **DEVE** occupare un'unica riga, tranne quando la proprietà `wrap` è impostata su `true`.</span><span class="sxs-lookup"><span data-stu-id="d3e32-143">A TextBlock **MUST** take up a single line unless the `wrap` property is `true`.</span></span> 
1. <span data-ttu-id="d3e32-144">Il blocco di testo **DOVREBBE** tagliare l'eventuale testo in eccesso con i puntini di sospensione (...)</span><span class="sxs-lookup"><span data-stu-id="d3e32-144">The text block **SHOULD** trim any excess text with an ellipsis (...)</span></span>

#### <a name="markdown"></a><span data-ttu-id="d3e32-145">Markdown</span><span class="sxs-lookup"><span data-stu-id="d3e32-145">Markdown</span></span>

1. <span data-ttu-id="d3e32-146">Le schede adattive consentono l'uso di un sottoinsieme del markdown e **DOVREBBE** essere fornito il supporto in `TextBlock`.</span><span class="sxs-lookup"><span data-stu-id="d3e32-146">Adaptive Cards allow for a subset of Markdown and **SHOULD** be supported in `TextBlock`.</span></span> 
1. <span data-ttu-id="d3e32-147">Vedi i [requisiti di markdown](../authoring-cards/text-features.md) completi.</span><span class="sxs-lookup"><span data-stu-id="d3e32-147">See full [markdown requirements](../authoring-cards/text-features.md)</span></span>

#### <a name="formatting-functions"></a><span data-ttu-id="d3e32-148">Funzioni di formattazione</span><span class="sxs-lookup"><span data-stu-id="d3e32-148">Formatting functions</span></span>

1. <span data-ttu-id="d3e32-149">`TextBlock` consente l'uso di [funzioni di formattazione DATE/TIME](../authoring-cards/text-features.md) che **DEVONO** essere supportate in ogni renderer.</span><span class="sxs-lookup"><span data-stu-id="d3e32-149">`TextBlock` allows [DATE/TIME formatting functions](../authoring-cards/text-features.md) that **MUST** be supported on every renderer.</span></span>
1. <span data-ttu-id="d3e32-150">**TUTTI GLI ERRORI DEVONO** visualizzare la stringa non elaborata nella scheda.</span><span class="sxs-lookup"><span data-stu-id="d3e32-150">**ALL FAILURES MUST** display the raw string in the card.</span></span> <span data-ttu-id="d3e32-151">Non vengono usati messaggi descrittivi</span><span class="sxs-lookup"><span data-stu-id="d3e32-151">No friendly message attempted.</span></span> <span data-ttu-id="d3e32-152">perché l'obiettivo è quello di far comprendere immediatamente il problema allo sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="d3e32-152">(The goal being to make the developer immediately aware there is a problem)</span></span>

1. <span data-ttu-id="d3e32-153">TODO: includi regex.</span><span class="sxs-lookup"><span data-stu-id="d3e32-153">TODO: Include regex</span></span>

### <a name="images"></a><span data-ttu-id="d3e32-154">Immagini</span><span class="sxs-lookup"><span data-stu-id="d3e32-154">Images</span></span>

1. <span data-ttu-id="d3e32-155">Un renderer **DOVREBBE** consentire alle app host di rilevare quando tutte le immagini HTTP sono state scaricate ed è stato "eseguito il rendering completo" della scheda</span><span class="sxs-lookup"><span data-stu-id="d3e32-155">A renderer **SHOULD** allow host apps to know when all HTTP images have been downloaded and the card is "fully rendered"</span></span>
1. <span data-ttu-id="d3e32-156">Un renderer **DEVE** controllare il parametro `maxImageSize` della configurazione host durante il download delle immagini HTTP</span><span class="sxs-lookup"><span data-stu-id="d3e32-156">A renderer **MUST** inspect the Host Config `maxImageSize` param when downloading HTTP images</span></span>
1. <span data-ttu-id="d3e32-157">Un renderer **DEVE** supportare `.png` e `.jpeg`</span><span class="sxs-lookup"><span data-stu-id="d3e32-157">A renderer **MUST** support `.png` and `.jpeg`</span></span>
1. <span data-ttu-id="d3e32-158">Un renderer **DOVREBBE** supportare le immagini `.gif`</span><span class="sxs-lookup"><span data-stu-id="d3e32-158">A renderer **SHOULD** support `.gif` images</span></span>

### <a name="host-config"></a><span data-ttu-id="d3e32-159">Configurazione dell'host</span><span class="sxs-lookup"><span data-stu-id="d3e32-159">Host Config</span></span>

* <span data-ttu-id="d3e32-160">TODO: quali dovrebbero essere le impostazioni predefinite?</span><span class="sxs-lookup"><span data-stu-id="d3e32-160">TODO: What should the defaults be?</span></span> <span data-ttu-id="d3e32-161">La condivisione dovrebbe essere totale?</span><span class="sxs-lookup"><span data-stu-id="d3e32-161">Should they all share it?</span></span> <span data-ttu-id="d3e32-162">È necessario incorporare un file hostConfig.json comune nei dati binari?</span><span class="sxs-lookup"><span data-stu-id="d3e32-162">Should we embed a common hostConfig.json file in the binaries?</span></span>
* <span data-ttu-id="d3e32-163">TODO: è necessario applicare il controllo delle versioni anche di HostConfig per l'analisi?</span><span class="sxs-lookup"><span data-stu-id="d3e32-163">TODO: I think HostConfig needs to be versioned as well for parsing?</span></span>

<span data-ttu-id="d3e32-164">[`HostConfig`](host-config.md) è un oggetto di configurazione condivisa che specifica il modo in cui un renderer di schede adattive genera l'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="d3e32-164">[`HostConfig`](host-config.md) is a shared configuration object that specifies how an Adaptive Card Renderer generates UI.</span></span>  

<span data-ttu-id="d3e32-165">Ciò consente di condividere le proprietà indipendenti dalla piattaforma tra i renderer in piattaforme e dispositivi diversi.</span><span class="sxs-lookup"><span data-stu-id="d3e32-165">This allows properties which are platform agnostic to be shared among renderers on different platforms and devices.</span></span> <span data-ttu-id="d3e32-166">Consente inoltre di creare strumenti che danno un'idea dell'aspetto che avrebbe la scheda per un determinato ambiente.</span><span class="sxs-lookup"><span data-stu-id="d3e32-166">It also allows tooling to be created which gives you an idea of the look and feel that card would have for a given environment.</span></span>

1. <span data-ttu-id="d3e32-167">I renderer **DEVONO** esporre un parametro di **configurazione host** alle app host</span><span class="sxs-lookup"><span data-stu-id="d3e32-167">Renderers **MUST** expose a **Host Config** parameter to host apps</span></span>
1. <span data-ttu-id="d3e32-168">Tutti gli elementi **DEVONO** avere uno stile in base alle rispettive impostazioni di configurazione host</span><span class="sxs-lookup"><span data-stu-id="d3e32-168">All elements **MUST** be styled according to their respective Host Config settings</span></span>

### <a name="native-platform-styling"></a><span data-ttu-id="d3e32-169">Applicazione di stili della piattaforma nativa</span><span class="sxs-lookup"><span data-stu-id="d3e32-169">Native platform styling</span></span>

1. <span data-ttu-id="d3e32-170">Ogni tipo di elemento **DOVREBBE** associare uno stile della piattaforma nativa all'elemento generato dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="d3e32-170">Each element type **SHOULD** attach a native platform style with the generated UI element.</span></span> <span data-ttu-id="d3e32-171">Ad esempio, in HTML è stata aggiunta una classe CSS ai tipi di elemento e in XAML viene assegnato uno stile specifico.</span><span class="sxs-lookup"><span data-stu-id="d3e32-171">E.g., in HTML we added a CSS class to the element types, and in XAML we assign a specific Style.</span></span>

## <a name="extensibility"></a><span data-ttu-id="d3e32-172">Estendibilità</span><span class="sxs-lookup"><span data-stu-id="d3e32-172">Extensibility</span></span> 

1. <span data-ttu-id="d3e32-173">Un renderer **DEVE** consentire alle app host di eseguire l'override dei renderer di elementi predefiniti,</span><span class="sxs-lookup"><span data-stu-id="d3e32-173">A renderer **MUST** allow host apps to override default element renderers.</span></span> <span data-ttu-id="d3e32-174">ad esempio sostituire il rendering di `TextBlock` con la propria logica.</span><span class="sxs-lookup"><span data-stu-id="d3e32-174">E.g., replace `TextBlock` rendering with their own logic.</span></span>
1. <span data-ttu-id="d3e32-175">Un renderer **DEVE** consentire alle app host di registrare tipi di elementi personalizzati,</span><span class="sxs-lookup"><span data-stu-id="d3e32-175">A renderer **MUST** allow host apps to register custom element types.</span></span> <span data-ttu-id="d3e32-176">ad esempio aggiungere il supporto per un elemento `Rating` personalizzato.</span><span class="sxs-lookup"><span data-stu-id="d3e32-176">E.g., add support for a custom `Rating` element</span></span>
1. <span data-ttu-id="d3e32-177">Un renderer **DEVE** consentire alle app host di rimuovere il supporto per un elemento predefinito,</span><span class="sxs-lookup"><span data-stu-id="d3e32-177">A renderer **MUST** allow host apps to remove support for a default element.</span></span> <span data-ttu-id="d3e32-178">ad esempio rimuovere `Action.Submit` se non vogliono che sia supportato.</span><span class="sxs-lookup"><span data-stu-id="d3e32-178">E.g., remove `Action.Submit` if they don't want it supported.</span></span>

## <a name="actions"></a><span data-ttu-id="d3e32-179">Azioni</span><span class="sxs-lookup"><span data-stu-id="d3e32-179">Actions</span></span>

1. <span data-ttu-id="d3e32-180">Se la proprietà `supportsInteractivity` di HostConfig è `false`, un renderer **NON DEVE** eseguire il rendering di alcuna azione.</span><span class="sxs-lookup"><span data-stu-id="d3e32-180">If HostConfig `supportsInteractivity` is `false`, a renderer **MUST NOT** render any actions.</span></span>
1. <span data-ttu-id="d3e32-181">La proprietà `actions`**DEVE** essere sottoposta a rendering come pulsanti in una specie di barra delle azioni, in genere nella parte inferiore della scheda.</span><span class="sxs-lookup"><span data-stu-id="d3e32-181">The `actions` property **MUST** be rendered as buttons in some kind of action bar, usually at the bottom of the card.</span></span> 
1. <span data-ttu-id="d3e32-182">Quando un pulsante viene toccato, **DEVE** consentire all'app host di gestire l'evento.</span><span class="sxs-lookup"><span data-stu-id="d3e32-182">When a button is tapped it **MUST** allow the host app to handle the event.</span></span> 
1. <span data-ttu-id="d3e32-183">L'evento **DEVE** passare tutte le proprietà associate con l'azione.</span><span class="sxs-lookup"><span data-stu-id="d3e32-183">The event **MUST** pass along all associated properties with the action</span></span>
1. <span data-ttu-id="d3e32-184">L'evento **DEVE** passare l'oggetto `AdaptiveCard` che è stato eseguito.</span><span class="sxs-lookup"><span data-stu-id="d3e32-184">The event **MUST** pass along the `AdaptiveCard` which was executed</span></span>

<span data-ttu-id="d3e32-185">Azione</span><span class="sxs-lookup"><span data-stu-id="d3e32-185">Action</span></span> | <span data-ttu-id="d3e32-186">Comportamento</span><span class="sxs-lookup"><span data-stu-id="d3e32-186">Behavior</span></span>
--- | ---
<span data-ttu-id="d3e32-187">**Action.OpenUrl**</span><span class="sxs-lookup"><span data-stu-id="d3e32-187">**Action.OpenUrl**</span></span> | <span data-ttu-id="d3e32-188">Apre un URL esterno per la visualizzazione</span><span class="sxs-lookup"><span data-stu-id="d3e32-188">Open an external URL for viewing</span></span>
<span data-ttu-id="d3e32-189">**Action.ShowCard**</span><span class="sxs-lookup"><span data-stu-id="d3e32-189">**Action.ShowCard**</span></span> | <span data-ttu-id="d3e32-190">Richiede che una scheda secondaria venga visualizzata all'utente.</span><span class="sxs-lookup"><span data-stu-id="d3e32-190">Requests a sub-card to be shown to the user.</span></span>
<span data-ttu-id="d3e32-191">**Action.Submit**</span><span class="sxs-lookup"><span data-stu-id="d3e32-191">**Action.Submit**</span></span> | <span data-ttu-id="d3e32-192">Richiede la raccolta di tutti gli elementi di input in un oggetto che ti viene quindi inviato tramite un metodo definito dall'applicazione host.</span><span class="sxs-lookup"><span data-stu-id="d3e32-192">Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

### <a name="actionopenurl"></a><span data-ttu-id="d3e32-193">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="d3e32-193">Action.OpenUrl</span></span>
1. <span data-ttu-id="d3e32-194">`Action.OpenUrl` **DOVREBBE** aprire un URL usando il meccanismo della piattaforma nativa.</span><span class="sxs-lookup"><span data-stu-id="d3e32-194">`Action.OpenUrl` **SHOULD** open a URL using the native platform mechanism</span></span>
1. <span data-ttu-id="d3e32-195">Se questo non è possibile, **DEVE** generare un evento nell'app host per gestire l'apertura dell'URL.</span><span class="sxs-lookup"><span data-stu-id="d3e32-195">If this is not possible it **MUST** raise an event to the host app to handle opening the URL.</span></span> <span data-ttu-id="d3e32-196">Questo evento **DEVE** consentire all'app host di eseguire l'override del comportamento predefinito,</span><span class="sxs-lookup"><span data-stu-id="d3e32-196">This event **MUST** allow the host app to override the default behavior.</span></span> <span data-ttu-id="d3e32-197">ad esempio consentire l'apertura dell'URL all'interno della rispettiva app.</span><span class="sxs-lookup"><span data-stu-id="d3e32-197">E.g., let them open the URL within their own app.</span></span>

### <a name="actionshowcard"></a><span data-ttu-id="d3e32-198">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="d3e32-198">Action.ShowCard</span></span>

1. <span data-ttu-id="d3e32-199">L'azione `Action.ShowCard` **DEVE** essere supportata in qualche modo, in base all'impostazione di hostConfig.</span><span class="sxs-lookup"><span data-stu-id="d3e32-199">`Action.ShowCard` **MUST** be supported in some way, based on the hostConfig setting.</span></span> <span data-ttu-id="d3e32-200">Sono disponibili due modalità: inline e popup.</span><span class="sxs-lookup"><span data-stu-id="d3e32-200">There are two modes: inline, and popup.</span></span> <span data-ttu-id="d3e32-201">Le schede inline **DOVREBBERO** attivare/disattivare la visibilità della scheda automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d3e32-201">Inline cards **SHOULD** toggle the card visibility automatically.</span></span> <span data-ttu-id="d3e32-202">In modalità popup **DOVREBBE** essere generato un evento nell'app host per mostrare la scheda in qualche modo.</span><span class="sxs-lookup"><span data-stu-id="d3e32-202">In popup mode, an event **SHOULD** be fired to the host app to show the card in some way.</span></span>

### <a name="actionsubmit"></a><span data-ttu-id="d3e32-203">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="d3e32-203">Action.Submit</span></span>

<span data-ttu-id="d3e32-204">L'azione di invio si comporta come l'invio di un modulo HTML, ad eccezione del fatto che, quando il codice HTML in genere attiva un post HTTP, le schede adattive lasciano a ogni app host la possibilità di determinare il significato di "inviare".</span><span class="sxs-lookup"><span data-stu-id="d3e32-204">The Submit Action behaves like an HTML form submit, except that where HTML typically triggers an HTTP post, Adaptive Cards leaves it up to each host app to determine what "submit" means to them.</span></span> 

1. <span data-ttu-id="d3e32-205">Quando **DEVE** essere generato un evento, l'utente tocca l'azione richiamata.</span><span class="sxs-lookup"><span data-stu-id="d3e32-205">When this **MUST** raise an event the user taps the action invoked.</span></span>  
1. <span data-ttu-id="d3e32-206">La proprietà `data`**DEVE** essere inclusa nel payload di callback.</span><span class="sxs-lookup"><span data-stu-id="d3e32-206">The `data` property **MUST** be included in the callback payload.</span></span>
1. <span data-ttu-id="d3e32-207">Per `Action.Submit`, un renderer **DEVE** raccogliere tutti gli input nella scheda e recuperare i relativi valori.</span><span class="sxs-lookup"><span data-stu-id="d3e32-207">For `Action.Submit`, a renderer **MUST** gather all inputs on the card and retrieve their values.</span></span> 

### <a name="selectaction"></a><span data-ttu-id="d3e32-208">selectAction</span><span class="sxs-lookup"><span data-stu-id="d3e32-208">selectAction</span></span>

1. <span data-ttu-id="d3e32-209">Se la proprietà `supportedInteractivity` di Host Config è `false`, `selectAction` **NON DEVE** soggetta a rendering come destinazione del tocco.</span><span class="sxs-lookup"><span data-stu-id="d3e32-209">If Host Config `supportedInteractivity` is `false` then a `selectAction` **MUST NOT** render as a touch target.</span></span>
1. <span data-ttu-id="d3e32-210">`Image`, `ColumnSet` e `Column` offrono una proprietà `selectAction` che **DOVREBBE** essere eseguita quando l'utente la richiama, ad esempio toccando l'elemento.</span><span class="sxs-lookup"><span data-stu-id="d3e32-210">`Image`, `ColumnSet`, and `Column` offer a `selectAction` property, which **SHOULD** be executed when the user invokes it, e.g., by tapping the element.</span></span>

## <a name="inputs"></a><span data-ttu-id="d3e32-211">Input</span><span class="sxs-lookup"><span data-stu-id="d3e32-211">Inputs</span></span>

1. <span data-ttu-id="d3e32-212">Se la proprietà `supportsInteractivity` di HostConfig è `false`, un renderer **NON DEVE** eseguire il rendering di alcun input.</span><span class="sxs-lookup"><span data-stu-id="d3e32-212">If HostConfig `supportsInteractivity` is `false` a renderer **MUST NOT** render any inputs.</span></span>
2. <span data-ttu-id="d3e32-213">Gli input **DOVREBBERO** essere sottoposti a rendering con la massima fedeltà possibile.</span><span class="sxs-lookup"><span data-stu-id="d3e32-213">Inputs **SHOULD** render with the highest fidelity possible.</span></span> <span data-ttu-id="d3e32-214">Ad esempio, un oggetto `Input.Date` idealmente offre una selezione data a un utente, ma se questo non è possibile nello stack dell'interfaccia utente, il renderer **DEVE** eseguire il fallback al rendering di una casella di testo standard.</span><span class="sxs-lookup"><span data-stu-id="d3e32-214">For example, an `Input.Date` would ideally offer a date picker to a user, but if this isn't possible on your UI stack, then the renderer **MUST** fall back to rendering a standard text box.</span></span>
3. <span data-ttu-id="d3e32-215">Un renderer **DOVREBBE** visualizzare l'oggetto `placeholderText`, se possibile.</span><span class="sxs-lookup"><span data-stu-id="d3e32-215">A renderer **SHOULD** display the `placeholderText` if possible</span></span>
4. <span data-ttu-id="d3e32-216">**NON** è necessario che un renderer implementi la convalida dell'input.</span><span class="sxs-lookup"><span data-stu-id="d3e32-216">A renderer **DOES NOT** have to implement validation of the input.</span></span> <span data-ttu-id="d3e32-217">Gli utenti di schede adattive devono pianificare la convalida dei dati ricevuti sul loro lato.</span><span class="sxs-lookup"><span data-stu-id="d3e32-217">Users of Adaptive Cards must plan to validate any received data on their end.</span></span>
5. <span data-ttu-id="d3e32-218">L'associazione del valore di input **DEVE** essere preceduta adeguatamente da caratteri di escape.</span><span class="sxs-lookup"><span data-stu-id="d3e32-218">Input value binding **MUST** be properly escaped</span></span>

6. <span data-ttu-id="d3e32-219">L'oggetto **DEVE** essere restituito all'app host come segue:</span><span class="sxs-lookup"><span data-stu-id="d3e32-219">The object **MUST** be returned to the host app as follows:</span></span>

   <span data-ttu-id="d3e32-220">Non viene eseguita alcuna promessa di convalida dell'input nelle schede adattive, pertanto spetta alla parte ricevente analizzare correttamente la risposta.</span><span class="sxs-lookup"><span data-stu-id="d3e32-220">We do not make any promises of input validation in adaptive cards, so it's up to the receiving party to properly parse the response.</span></span> <span data-ttu-id="d3e32-221">Ad esempio, Input.Number potrebbe restituire "hello" ed è necessario essere preparati in tal senso.</span><span class="sxs-lookup"><span data-stu-id="d3e32-221">E.g., a Input.Number could return "hello" and they need to be prepared for that.</span></span>


## <a name="events"></a><span data-ttu-id="d3e32-222">Eventi</span><span class="sxs-lookup"><span data-stu-id="d3e32-222">Events</span></span>

1. <span data-ttu-id="d3e32-223">Un renderer **DOVREBBE** generare un evento quando la visibilità di un elemento è cambiata, consentendo all'app host di scorrere la scheda in posizione.</span><span class="sxs-lookup"><span data-stu-id="d3e32-223">A renderer **SHOULD** fire an event when an element's visibility has changed, allowing the host app to scroll the card into position.</span></span>
