---
title: Implementazione di un Renderer
author: matthidinger
ms.author: mahiding
ms.date: 09/15/2017
ms.topic: article
ms.openlocfilehash: 3c79d768d5c979626b66614a1856ad6c2e390805
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552553"
---
# <a name="adaptive-card-renderer-specification"></a><span data-ttu-id="7ebde-102">Specifica del Renderer scheda adattiva</span><span class="sxs-lookup"><span data-stu-id="7ebde-102">Adaptive Card Renderer Specification</span></span>

<span data-ttu-id="7ebde-103">La specifica seguente viene descritto come implementare un renderer scheda adattiva in qualsiasi piattaforma dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="7ebde-103">The following specification describes how implement an Adaptive Card renderer on any UI platform.</span></span>

> [!IMPORTANT]
> 
> <span data-ttu-id="7ebde-104">Questo contenuto non è ancora stato completato.</span><span class="sxs-lookup"><span data-stu-id="7ebde-104">This content is not finished yet.</span></span> <span data-ttu-id="7ebde-105">Ricontrollare a breve.</span><span class="sxs-lookup"><span data-stu-id="7ebde-105">Check back shortly.</span></span>

## <a name="sdk-versioning"></a><span data-ttu-id="7ebde-106">Controllo delle versioni SDK</span><span class="sxs-lookup"><span data-stu-id="7ebde-106">SDK Versioning</span></span>

1. <span data-ttu-id="7ebde-107">La versione del SDK major e minor **SHOULD** corrispondere il `schema` versione.</span><span class="sxs-lookup"><span data-stu-id="7ebde-107">The SDK major and minor version **SHOULD** match the `schema` version.</span></span> 
1. <span data-ttu-id="7ebde-108">Patch/build **SHOULD** essere usato per gli aggiornamenti di renderer che non hanno le modifiche dello schema.</span><span class="sxs-lookup"><span data-stu-id="7ebde-108">Patch/build **SHOULD** be used for renderer updates that don't have schema changes.</span></span>

## <a name="parsing-json"></a><span data-ttu-id="7ebde-109">L'analisi JSON</span><span class="sxs-lookup"><span data-stu-id="7ebde-109">Parsing JSON</span></span>

### <a name="error-conditions"></a><span data-ttu-id="7ebde-110">Condizioni di errore</span><span class="sxs-lookup"><span data-stu-id="7ebde-110">Error conditions</span></span>
1. <span data-ttu-id="7ebde-111">Un parser **necessario** che sia contenuto JSON valido</span><span class="sxs-lookup"><span data-stu-id="7ebde-111">A parser **MUST** check that it's valid JSON content</span></span>
1. <span data-ttu-id="7ebde-112">Un parser **necessario** convalidare a fronte dello schema (proprietà obbligatorie e così via)</span><span class="sxs-lookup"><span data-stu-id="7ebde-112">A parser **MUST** validate against the schema (required properties, etc)</span></span>
1. <span data-ttu-id="7ebde-113">Gli errori citati **necessario** segnalati per l'app host (un'eccezione o equivalente)</span><span class="sxs-lookup"><span data-stu-id="7ebde-113">The above errors **MUST** be reported to the host app (exception or equivalent)</span></span>

### <a name="unknown-types"></a><span data-ttu-id="7ebde-114">Tipi sconosciuti</span><span class="sxs-lookup"><span data-stu-id="7ebde-114">Unknown types</span></span>
1. <span data-ttu-id="7ebde-115">Se vengono rilevati sconosciuti "tipi" essi **devono essere eliminati** dal risultato</span><span class="sxs-lookup"><span data-stu-id="7ebde-115">If unknown "types" are encountered they **MUST BE DROPPED** from the result</span></span>
1. <span data-ttu-id="7ebde-116">Modifiche del payload (come sopra) **SHOULD** siano segnalati come avvisi per l'applicazione host</span><span class="sxs-lookup"><span data-stu-id="7ebde-116">Any alterations of the payload (like above) **SHOULD** be reported as warnings to the host app</span></span>

### <a name="unknown-properties"></a><span data-ttu-id="7ebde-117">Proprietà sconosciute</span><span class="sxs-lookup"><span data-stu-id="7ebde-117">Unknown properties</span></span>
1. <span data-ttu-id="7ebde-118">Un parser **devono** includono **aggiuntive** sulle proprietà degli elementi</span><span class="sxs-lookup"><span data-stu-id="7ebde-118">A parser **MUST** include **additional** properties on elements</span></span>

### <a name="additional-considerations"></a><span data-ttu-id="7ebde-119">Considerazioni aggiuntive</span><span class="sxs-lookup"><span data-stu-id="7ebde-119">Additional considerations</span></span>
1. <span data-ttu-id="7ebde-120">Il `speak` proprietà contenga il markup SSML e **necessario** restituito all'app host come specificata</span><span class="sxs-lookup"><span data-stu-id="7ebde-120">The `speak` property may contain SSML markup and **MUST** be returned to the host app as-specified</span></span>

## <a name="parsing-host-config"></a><span data-ttu-id="7ebde-121">L'analisi di configurazione di Host</span><span class="sxs-lookup"><span data-stu-id="7ebde-121">Parsing Host Config</span></span>
1. <span data-ttu-id="7ebde-122">TODO</span><span class="sxs-lookup"><span data-stu-id="7ebde-122">TODO</span></span>

## <a name="versioning"></a><span data-ttu-id="7ebde-123">Controllo delle versioni</span><span class="sxs-lookup"><span data-stu-id="7ebde-123">Versioning</span></span>

1. <span data-ttu-id="7ebde-124">Un renderer **necessario** implementare una particolare versione dello schema.</span><span class="sxs-lookup"><span data-stu-id="7ebde-124">A renderer **MUST** implement a particular version of the schema.</span></span> 
1. <span data-ttu-id="7ebde-125">Il `AdaptiveCard` costruttore **necessario** assegnare il `version` proprietà valore predefinito è basato sulla versione corrente dello schema</span><span class="sxs-lookup"><span data-stu-id="7ebde-125">The `AdaptiveCard` constructor **MUST** give the `version` property a default value based on the current schema version</span></span> 
1. <span data-ttu-id="7ebde-126">Se viene rilevato un renderer di un `version` proprietà nel `AdaptiveCard` che è superiore alla versione supportata, viene **deve** restituiscono il `fallbackText` invece.</span><span class="sxs-lookup"><span data-stu-id="7ebde-126">If a renderer encounters a `version` property in the `AdaptiveCard` that is higher than the supported version, it **MUST** return the `fallbackText` instead.</span></span>

## <a name="rendering"></a><span data-ttu-id="7ebde-127">Per il rendering</span><span class="sxs-lookup"><span data-stu-id="7ebde-127">Rendering</span></span>

<span data-ttu-id="7ebde-128">Un' `AdaptiveCard` è costituito da un `body` e `actions`.</span><span class="sxs-lookup"><span data-stu-id="7ebde-128">An `AdaptiveCard` consists of a `body` and `actions`.</span></span> <span data-ttu-id="7ebde-129">Il `body` è una raccolta di `CardElement`che un renderer enumererà ed eseguire il rendering in ordine.</span><span class="sxs-lookup"><span data-stu-id="7ebde-129">The `body` is a collection of `CardElement`s that a renderer will enumerate and render in order.</span></span> 

1. <span data-ttu-id="7ebde-130">Ogni elemento **devono** stretch per la larghezza dell'elemento padre (pensare `display: block` in formato HTML).</span><span class="sxs-lookup"><span data-stu-id="7ebde-130">Each Element **MUST** stretch to the width of its parent (think `display: block` in HTML).</span></span>
1. <span data-ttu-id="7ebde-131">Un renderer **necessario** ignorano i tipi di elemento sconosciuto e continuare il resto del payload di rendering.</span><span class="sxs-lookup"><span data-stu-id="7ebde-131">A renderer **MUST** ignore unknown element types, and continue rendering the rest of the payload.</span></span>

### <a name="spacing-and-separators"></a><span data-ttu-id="7ebde-132">Spaziatura e separatori</span><span class="sxs-lookup"><span data-stu-id="7ebde-132">Spacing and Separators</span></span>

1. <span data-ttu-id="7ebde-133">Il `spacing` proprietà su ogni elemento influisce sulla quantità di spazio tra il **corrente** elemento e quello **BEFORE** è.</span><span class="sxs-lookup"><span data-stu-id="7ebde-133">The `spacing` property on every element influences the amount of space between the **CURRENT** element and the one **BEFORE** it.</span></span>
1. <span data-ttu-id="7ebde-134">Spaziatura **devono solo** applicare se si è effettivamente un elemento che la precede.</span><span class="sxs-lookup"><span data-stu-id="7ebde-134">Spacing **MUST ONLY** apply when there actually is an element preceding it.</span></span> <span data-ttu-id="7ebde-135">(Ad esempio, non verranno applicati al primo elemento in una matrice)</span><span class="sxs-lookup"><span data-stu-id="7ebde-135">(E.g., won't apply to the first item in an array)</span></span>
1. <span data-ttu-id="7ebde-136">Un renderer **devono** cercare la quantità di spazio da utilizzare dal `hostConfig` spaziatura per il valore di enumerazione applicato all'elemento corrente.</span><span class="sxs-lookup"><span data-stu-id="7ebde-136">A renderer **MUST** look up the amount of space to use from the `hostConfig` spacing for the enum value applied to the current element.</span></span>
1. <span data-ttu-id="7ebde-137">Se l'elemento ha un `separator` pari a `true`, quindi una riga visibile **necessario** separazione tra l'elemento corrente e quella prima di esso.</span><span class="sxs-lookup"><span data-stu-id="7ebde-137">If the element has a `separator` value of `true`, then a visible line **MUST** be drawn between the current element and the one before it.</span></span>
1. <span data-ttu-id="7ebde-138">La linea di separazione **devono** essere disegnata usando il `container.style.default.foregroundColor`.</span><span class="sxs-lookup"><span data-stu-id="7ebde-138">The separator line **MUST** be drawn using the `container.style.default.foregroundColor`.</span></span>
1. <span data-ttu-id="7ebde-139">Un separatore **devono solo** da disegnare se l'elemento **non è** il primo elemento nella matrice.</span><span class="sxs-lookup"><span data-stu-id="7ebde-139">A separator **MUST ONLY** be drawn if the item **IS NOT** the first in the array.</span></span>

### <a name="columns"></a><span data-ttu-id="7ebde-140">Colonne</span><span class="sxs-lookup"><span data-stu-id="7ebde-140">Columns</span></span>

1. <span data-ttu-id="7ebde-141">`Column` `width` **È necessario** essere interpretata dalle "auto", "stretch" o un rapporto ponderato.</span><span class="sxs-lookup"><span data-stu-id="7ebde-141">`Column` `width` **MUST** be interpreted by "auto", "stretch" or a weighted ratio.</span></span>

### <a name="textblock"></a><span data-ttu-id="7ebde-142">TextBlock</span><span class="sxs-lookup"><span data-stu-id="7ebde-142">TextBlock</span></span>

1. <span data-ttu-id="7ebde-143">Un elemento TextBlock **devono** occupano una singola riga, a meno che il `wrap` è di proprietà `true`.</span><span class="sxs-lookup"><span data-stu-id="7ebde-143">A TextBlock **MUST** take up a single line unless the `wrap` property is `true`.</span></span> 
1. <span data-ttu-id="7ebde-144">Il blocco di testo **SHOULD** tagliare il testo in eccesso con i puntini di sospensione (...)</span><span class="sxs-lookup"><span data-stu-id="7ebde-144">The text block **SHOULD** trim any excess text with an ellipsis (...)</span></span>

#### <a name="markdown"></a><span data-ttu-id="7ebde-145">Markdown</span><span class="sxs-lookup"><span data-stu-id="7ebde-145">Markdown</span></span>

1. <span data-ttu-id="7ebde-146">Le schede adattive consentono un sottoinsieme di Markdown e **SHOULD** supportata in `TextBlock`.</span><span class="sxs-lookup"><span data-stu-id="7ebde-146">Adaptive Cards allow for a subset of Markdown and **SHOULD** be supported in `TextBlock`.</span></span> 
1. <span data-ttu-id="7ebde-147">Vedere completi [requisiti markdown](../authoring-cards/text-features.md)</span><span class="sxs-lookup"><span data-stu-id="7ebde-147">See full [markdown requirements](../authoring-cards/text-features.md)</span></span>

#### <a name="formatting-functions"></a><span data-ttu-id="7ebde-148">Le funzioni di formattazione</span><span class="sxs-lookup"><span data-stu-id="7ebde-148">Formatting functions</span></span>

1. <span data-ttu-id="7ebde-149">`TextBlock` Consente [funzioni di formattazione di data/ora](../authoring-cards/text-features.md) che **necessario** siano supportate in ogni renderer.</span><span class="sxs-lookup"><span data-stu-id="7ebde-149">`TextBlock` allows [DATE/TIME formatting functions](../authoring-cards/text-features.md) that **MUST** be supported on every renderer.</span></span>
1. <span data-ttu-id="7ebde-150">**TUTTI gli errori devono** visualizzare la stringa non elaborata nella scheda.</span><span class="sxs-lookup"><span data-stu-id="7ebde-150">**ALL FAILURES MUST** display the raw string in the card.</span></span> <span data-ttu-id="7ebde-151">Nessun messaggio descrittivo tentato.</span><span class="sxs-lookup"><span data-stu-id="7ebde-151">No friendly message attempted.</span></span> <span data-ttu-id="7ebde-152">(L'obiettivo a rendere lo sviluppatore consapevole immediatamente si è verificato un problema)</span><span class="sxs-lookup"><span data-stu-id="7ebde-152">(The goal being to make the developer immediately aware there is a problem)</span></span>

1. <span data-ttu-id="7ebde-153">TODO: Includere espressioni regolari</span><span class="sxs-lookup"><span data-stu-id="7ebde-153">TODO: Include regex</span></span>

### <a name="images"></a><span data-ttu-id="7ebde-154">Immagini</span><span class="sxs-lookup"><span data-stu-id="7ebde-154">Images</span></span>

1. <span data-ttu-id="7ebde-155">Un renderer **SHOULD** consente l'hosting di App di sapere quando sono state scaricate tutte le immagini HTTP e la scheda è "completamente rendererd"</span><span class="sxs-lookup"><span data-stu-id="7ebde-155">A renderer **SHOULD** allow host apps to know when all HTTP images have been downloaded and the card is "fully rendererd"</span></span>
1. <span data-ttu-id="7ebde-156">Un renderer **devono** ispezionare la configurazione Host `maxImageSize` param durante il download delle immagini HTTP</span><span class="sxs-lookup"><span data-stu-id="7ebde-156">A renderer **MUST** inspect the Host Config `maxImageSize` param when downloading HTTP images</span></span>
1. <span data-ttu-id="7ebde-157">Un renderer **devono** supportano `.png` e `.jpeg`</span><span class="sxs-lookup"><span data-stu-id="7ebde-157">A renderer **MUST** support `.png` and `.jpeg`</span></span>
1. <span data-ttu-id="7ebde-158">Un renderer **SHOULD** supportano `.gif` immagini</span><span class="sxs-lookup"><span data-stu-id="7ebde-158">A renderer **SHOULD** support `.gif` images</span></span>

### <a name="host-config"></a><span data-ttu-id="7ebde-159">Configurazione di host</span><span class="sxs-lookup"><span data-stu-id="7ebde-159">Host Config</span></span>

* <span data-ttu-id="7ebde-160">TODO: Quale dovrebbero essere i valori predefiniti?</span><span class="sxs-lookup"><span data-stu-id="7ebde-160">TODO: What should the defaults be?</span></span> <span data-ttu-id="7ebde-161">Dovrebbe condividono tutti lo?</span><span class="sxs-lookup"><span data-stu-id="7ebde-161">Should they all share it?</span></span> <span data-ttu-id="7ebde-162">Dovremmo si incorpora un file hostConfig.json comune nei file binari?</span><span class="sxs-lookup"><span data-stu-id="7ebde-162">Should we embed a common hostConfig.json file in the binaries?</span></span>
* <span data-ttu-id="7ebde-163">TODO: Ritengo che HostConfig deve essere eseguito anche per l'analisi?</span><span class="sxs-lookup"><span data-stu-id="7ebde-163">TODO: I think HostConfig needs to be versioned as well for parsing?</span></span>

<span data-ttu-id="7ebde-164">[`HostConfig`](host-config.md) è un oggetto di configurazione condivisa che specifica la modalità di generazione dell'interfaccia utente in un Renderer scheda adattiva.</span><span class="sxs-lookup"><span data-stu-id="7ebde-164">[`HostConfig`](host-config.md) is a shared configuration object that specifies how an Adaptive Card Renderer generates UI.</span></span>  

<span data-ttu-id="7ebde-165">In questo modo le proprietà che sono indipendenti dalla piattaforma per la condivisione tra i renderer su diverse piattaforme e dispositivi.</span><span class="sxs-lookup"><span data-stu-id="7ebde-165">This allows properties which are platform agnostic to be shared among renderers on different platforms and devices.</span></span> <span data-ttu-id="7ebde-166">Consente inoltre gli strumenti da creare che ti offre un'idea dell'aspetto che scheda sarebbe necessario per un determinato ambiente.</span><span class="sxs-lookup"><span data-stu-id="7ebde-166">It also allows tooling to be created which gives you an idea of the look and feel that card would have for a given environment.</span></span>

1. <span data-ttu-id="7ebde-167">I renderer **devono** esporre una **Host Config** parametro per ospitare App</span><span class="sxs-lookup"><span data-stu-id="7ebde-167">Renderers **MUST** expose a **Host Config** parameter to host apps</span></span>
1. <span data-ttu-id="7ebde-168">Tutti gli elementi **necessario** applicare stili in base a delle rispettive impostazioni di configurazione di Host</span><span class="sxs-lookup"><span data-stu-id="7ebde-168">All elements **MUST** be styled according to their respective Host Config settings</span></span>

### <a name="native-platform-styling"></a><span data-ttu-id="7ebde-169">Stile di piattaforma nativa</span><span class="sxs-lookup"><span data-stu-id="7ebde-169">Native platform styling</span></span>

1. <span data-ttu-id="7ebde-170">Ogni tipo di elemento **SHOULD** allegare uno stile di piattaforma nativa con l'elemento dell'interfaccia utente generato.</span><span class="sxs-lookup"><span data-stu-id="7ebde-170">Each element type **SHOULD** attach a native platform style with the generated UI element.</span></span> <span data-ttu-id="7ebde-171">Ad esempio, in formato HTML è stata aggiunta una classe CSS per i tipi di elemento e in XAML è assegnare uno stile specifico.</span><span class="sxs-lookup"><span data-stu-id="7ebde-171">E.g., in HTML we added a CSS class to the element types, and in XAML we assign a specific Style.</span></span>

## <a name="extensibility"></a><span data-ttu-id="7ebde-172">Estendibilità</span><span class="sxs-lookup"><span data-stu-id="7ebde-172">Extensibility</span></span> 

1. <span data-ttu-id="7ebde-173">Un renderer **necessario** consentire l'hosting delle App eseguire l'override di renderer di elemento predefinito.</span><span class="sxs-lookup"><span data-stu-id="7ebde-173">A renderer **MUST** allow host apps to override default element renderers.</span></span> <span data-ttu-id="7ebde-174">Ad esempio, sostituire `TextBlock` esegue il rendering con la propria logica.</span><span class="sxs-lookup"><span data-stu-id="7ebde-174">E.g., replace `TextBlock` rendering with their own logic.</span></span>
1. <span data-ttu-id="7ebde-175">Un renderer **necessario** consentire l'hosting delle App registrare i tipi di elemento personalizzati.</span><span class="sxs-lookup"><span data-stu-id="7ebde-175">A renderer **MUST** allow host apps to register custom element types.</span></span> <span data-ttu-id="7ebde-176">Ad esempio, aggiungere il supporto per un oggetto personalizzato `Rating` elemento</span><span class="sxs-lookup"><span data-stu-id="7ebde-176">E.g., add support for a custom `Rating` element</span></span>
1. <span data-ttu-id="7ebde-177">Un renderer **necessario** consentire alle App host di rimuovere il supporto per un elemento predefinito.</span><span class="sxs-lookup"><span data-stu-id="7ebde-177">A renderer **MUST** allow host apps to remove support for a default element.</span></span> <span data-ttu-id="7ebde-178">Ad esempio, rimuovere `Action.Submit` se si preferisce non supportata.</span><span class="sxs-lookup"><span data-stu-id="7ebde-178">E.g., remove `Action.Submit` if they don't want it supported.</span></span>

## <a name="actions"></a><span data-ttu-id="7ebde-179">Azioni</span><span class="sxs-lookup"><span data-stu-id="7ebde-179">Actions</span></span>

1. <span data-ttu-id="7ebde-180">Se HostConfig `supportsInteractivity` viene `false`, un renderer **non deve** eseguire il rendering di eventuali azioni.</span><span class="sxs-lookup"><span data-stu-id="7ebde-180">If HostConfig `supportsInteractivity` is `false`, a renderer **MUST NOT** render any actions.</span></span>
1. <span data-ttu-id="7ebde-181">Il `actions` proprietà **necessario** sottoposta a rendering come pulsanti nello stesso tipo di barra delle azioni, in genere nella parte inferiore della scheda.</span><span class="sxs-lookup"><span data-stu-id="7ebde-181">The `actions` property **MUST** be rendered as buttons in some kind of action bar, usually at the bottom of the card.</span></span> 
1. <span data-ttu-id="7ebde-182">Quando si tocca un pulsante viene **necessario** consentire all'app di host gestire l'evento.</span><span class="sxs-lookup"><span data-stu-id="7ebde-182">When a button is tapped it **MUST** allow the host app to handle the event.</span></span> 
1. <span data-ttu-id="7ebde-183">L'evento **necessario** pass lungo tutte le relative proprietà con l'azione</span><span class="sxs-lookup"><span data-stu-id="7ebde-183">The event **MUST** pass along all associated properties with the action</span></span>
1. <span data-ttu-id="7ebde-184">L'evento **devono** passano il `AdaptiveCard` quale è stato eseguito</span><span class="sxs-lookup"><span data-stu-id="7ebde-184">The event **MUST** pass along the `AdaptiveCard` which was executed</span></span>

<span data-ttu-id="7ebde-185">Azione</span><span class="sxs-lookup"><span data-stu-id="7ebde-185">Action</span></span> | <span data-ttu-id="7ebde-186">Comportamento</span><span class="sxs-lookup"><span data-stu-id="7ebde-186">Behavior</span></span>
--- | ---
<span data-ttu-id="7ebde-187">**Action.OpenUrl**</span><span class="sxs-lookup"><span data-stu-id="7ebde-187">**Action.OpenUrl**</span></span> | <span data-ttu-id="7ebde-188">Aprire un URL esterno per la visualizzazione</span><span class="sxs-lookup"><span data-stu-id="7ebde-188">Open an external URL for viewing</span></span>
<span data-ttu-id="7ebde-189">**Action.ShowCard**</span><span class="sxs-lookup"><span data-stu-id="7ebde-189">**Action.ShowCard**</span></span> | <span data-ttu-id="7ebde-190">Richiede una carta secondari da visualizzare all'utente.</span><span class="sxs-lookup"><span data-stu-id="7ebde-190">Requests a sub-card to be shown to the user.</span></span>
<span data-ttu-id="7ebde-191">**Action.Submit**</span><span class="sxs-lookup"><span data-stu-id="7ebde-191">**Action.Submit**</span></span> | <span data-ttu-id="7ebde-192">Porre per tutti gli elementi di input di raccogliere in un oggetto che viene quindi inviato all'utente tramite un metodo definito dall'applicazione host.</span><span class="sxs-lookup"><span data-stu-id="7ebde-192">Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

### <a name="actionopenurl"></a><span data-ttu-id="7ebde-193">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="7ebde-193">Action.OpenUrl</span></span>
1. <span data-ttu-id="7ebde-194">`Action.OpenUrl` **DOVREBBE** aprire un URL usando il meccanismo di piattaforma nativa</span><span class="sxs-lookup"><span data-stu-id="7ebde-194">`Action.OpenUrl` **SHOULD** open a URL using the native platform mechanism</span></span>
1. <span data-ttu-id="7ebde-195">Se questo non è possibile **necessario** generare un evento per l'applicazione host per gestire aprendo l'URL.</span><span class="sxs-lookup"><span data-stu-id="7ebde-195">If this is not possible it **MUST** raise an event to the host app to handle opening the URL.</span></span> <span data-ttu-id="7ebde-196">Questo evento **necessario** consentire all'app di host eseguire l'override del comportamento predefinito.</span><span class="sxs-lookup"><span data-stu-id="7ebde-196">This event **MUST** allow the host app to override the default behavior.</span></span> <span data-ttu-id="7ebde-197">Ad esempio, consentendogli di aprire l'URL interno le proprie app.</span><span class="sxs-lookup"><span data-stu-id="7ebde-197">E.g., let them open the URL within their own app.</span></span>

### <a name="actionshowcard"></a><span data-ttu-id="7ebde-198">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="7ebde-198">Action.ShowCard</span></span>

1. <span data-ttu-id="7ebde-199">`Action.ShowCard` **È necessario** supportato in qualche modo, in base all'impostazione hostConfig.</span><span class="sxs-lookup"><span data-stu-id="7ebde-199">`Action.ShowCard` **MUST** be supported in some way, based on the hostConfig setting.</span></span> <span data-ttu-id="7ebde-200">Sono disponibili due modalità: inline e finestra popup.</span><span class="sxs-lookup"><span data-stu-id="7ebde-200">There are two modes: inline, and popup.</span></span> <span data-ttu-id="7ebde-201">Le schede inline **SHOULD** attivare/disattivare la visibilità di smart card automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7ebde-201">Inline cards **SHOULD** toggle the card visibility automatically.</span></span> <span data-ttu-id="7ebde-202">In modalità finestra popup, un evento **SHOULD** generato per l'app host venga visualizzata la scheda in qualche modo.</span><span class="sxs-lookup"><span data-stu-id="7ebde-202">In popup mode, an event **SHOULD** be fired to the host app to show the card in some way.</span></span>

### <a name="actionsubmit"></a><span data-ttu-id="7ebde-203">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="7ebde-203">Action.Submit</span></span>

<span data-ttu-id="7ebde-204">L'azione di invio si comporta come un invio di form HTML, ad eccezione del fatto che in cui in genere HTML attiva una richiesta post HTTP, le schede adattive lasciandolo fino a ogni app host di determinare quali "Invia" significa che a loro.</span><span class="sxs-lookup"><span data-stu-id="7ebde-204">The Submit Action behaves like an HTML form submit, except that where HTML typically triggers an HTTP post, Adaptive Cards leaves it up to each host app to determine what "submit" means to them.</span></span> 

1. <span data-ttu-id="7ebde-205">Quando ciò **necessario** generare un evento, l'utente tocca invokved l'azione.</span><span class="sxs-lookup"><span data-stu-id="7ebde-205">When this **MUST** raise an event the user taps the action invokved.</span></span>  
1. <span data-ttu-id="7ebde-206">Il `data` proprietà **necessario** da includere nel payload del callback.</span><span class="sxs-lookup"><span data-stu-id="7ebde-206">The `data` property **MUST** be included in the callback payload.</span></span>
1. <span data-ttu-id="7ebde-207">Per la `Action.Submit`, un renderer **necessario** raccogliere tutti gli input della scheda e recuperare i valori.</span><span class="sxs-lookup"><span data-stu-id="7ebde-207">For `Action.Submit`, a renderer **MUST** gather all inputs on the card and retrieve their values.</span></span> 

### <a name="selectaction"></a><span data-ttu-id="7ebde-208">selectAction</span><span class="sxs-lookup"><span data-stu-id="7ebde-208">selectAction</span></span>

1. <span data-ttu-id="7ebde-209">Se Host Config `supportedInteractivity` viene `false` un' `selectAction` **non deve** sottoposti a rendering come una destinazione di tocco.</span><span class="sxs-lookup"><span data-stu-id="7ebde-209">If Host Config `supportedInteractivity` is `false` then a `selectAction` **MUST NOT** render as a touch target.</span></span>
1. <span data-ttu-id="7ebde-210">`Image`, `ColumnSet`, e `Column` offrono una `selectAction` proprietà, quali **SHOULD** da eseguire quando l'utente richiama, ad esempio, toccare l'elemento.</span><span class="sxs-lookup"><span data-stu-id="7ebde-210">`Image`, `ColumnSet`, and `Column` offer a `selectAction` property, which **SHOULD** be executed when the user invokes it, e.g., by tapping the element.</span></span>

## <a name="inputs"></a><span data-ttu-id="7ebde-211">Input</span><span class="sxs-lookup"><span data-stu-id="7ebde-211">Inputs</span></span>

1. <span data-ttu-id="7ebde-212">Se HostConfig `supportsInteractivity` viene `false` un renderer **non deve** eseguire il rendering di alcun input.</span><span class="sxs-lookup"><span data-stu-id="7ebde-212">If HostConfig `supportsInteractivity` is `false` a renderer **MUST NOT** render any inputs.</span></span>
2. <span data-ttu-id="7ebde-213">Gli input **SHOULD** rendering con la massima fedeltà possibili.</span><span class="sxs-lookup"><span data-stu-id="7ebde-213">Inputs **SHOULD** render with the highest fidelity possible.</span></span> <span data-ttu-id="7ebde-214">Ad esempio, un' `Input.Date` offrirebbe idealmente un controllo selezione data a un utente, ma se questo non è possibile lo stack di interfaccia utente, quindi il renderer **necessario** il fallback al rendering di una casella di testo standard.</span><span class="sxs-lookup"><span data-stu-id="7ebde-214">For example, an `Input.Date` would ideally offer a date picker to a user, but if this isn't possible on your UI stack, then the renderer **MUST** fall back to rendering a standard text box.</span></span>
3. <span data-ttu-id="7ebde-215">Un renderer **SHOULD** visualizzare il `placeholderText` se possibile</span><span class="sxs-lookup"><span data-stu-id="7ebde-215">A renderer **SHOULD** display the `placeholderText` if possible</span></span>
4. <span data-ttu-id="7ebde-216">Un renderer **non implica** disporre implementare la convalida dell'input.</span><span class="sxs-lookup"><span data-stu-id="7ebde-216">A renderer **DOES NOT** have to implement validation of the input.</span></span> <span data-ttu-id="7ebde-217">Gli utenti delle schede adattive devono pianificare convalidare tutti i dati ricevuti estremità.</span><span class="sxs-lookup"><span data-stu-id="7ebde-217">Users of Adaptive Cards must plan to validate any receieved data on their end.</span></span>
5. <span data-ttu-id="7ebde-218">Associazione del valore di input **necessario** utilizzare correttamente caratteri di escape</span><span class="sxs-lookup"><span data-stu-id="7ebde-218">Input value binding **MUST** be properly escaped</span></span>

6. <span data-ttu-id="7ebde-219">L'oggetto **necessario** da restituire per l'applicazione host come segue:</span><span class="sxs-lookup"><span data-stu-id="7ebde-219">The object **MUST** be returned to the host app as follows:</span></span>

   <span data-ttu-id="7ebde-220">È non apportare qualsiasi promesse di convalida dell'input nelle schede adattive, in modo che spetta alla parte ricevente per analizzare correttamente la risposta.</span><span class="sxs-lookup"><span data-stu-id="7ebde-220">We do not make any promises of input validation in adaptive cards, so it's up to the receiving party to properly parse the response.</span></span> <span data-ttu-id="7ebde-221">Ad esempio, un Input.Number potrebbe restituire "hello" e devono essere preparati per che.</span><span class="sxs-lookup"><span data-stu-id="7ebde-221">E.g., a Input.Number could return "hello" and they need to be prepared for that.</span></span>


## <a name="events"></a><span data-ttu-id="7ebde-222">Eventi</span><span class="sxs-lookup"><span data-stu-id="7ebde-222">Events</span></span>

1. <span data-ttu-id="7ebde-223">Un renderer **SHOULD** generare un evento quando la visibilità di un elemento è stato modificato, consentendo all'app di host scorrere la scheda nella posizione desiderata.</span><span class="sxs-lookup"><span data-stu-id="7ebde-223">A renderer **SHOULD** fire an event when an element's visibility has changed, allowing the host app to scroll the card into position.</span></span>
