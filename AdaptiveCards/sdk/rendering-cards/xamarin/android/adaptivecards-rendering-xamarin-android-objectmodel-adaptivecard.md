---
title: Classe AdaptiveCard-Novell. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: 0f64bf635023271d8b40bf55fce079300aae7652
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146085"
---
# <a name="adaptivecard"></a><span data-ttu-id="ff6bb-102">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="ff6bb-102">AdaptiveCard</span></span>

```csharp
public class AdaptiveCard : Java.Lang.Object 
```

<span data-ttu-id="ff6bb-103">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="ff6bb-103">**Namespace**</span></span>

```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.ObjectModel
```

## <a name="summary"></a><span data-ttu-id="ff6bb-104">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="ff6bb-104">Summary</span></span>

| <span data-ttu-id="ff6bb-105">Attributi</span><span class="sxs-lookup"><span data-stu-id="ff6bb-105">Attributes</span></span> | |
| ---- | --- |
| <span data-ttu-id="ff6bb-106">Azioni</span><span class="sxs-lookup"><span data-stu-id="ff6bb-106">Actions</span></span> | <span data-ttu-id="ff6bb-107">Azioni da visualizzare nella barra delle azioni della scheda.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-107">The Actions to show in the card’s action bar.</span></span> |
| <span data-ttu-id="ff6bb-108">BackgroundImage</span><span class="sxs-lookup"><span data-stu-id="ff6bb-108">BackgroundImage</span></span> | <span data-ttu-id="ff6bb-109">Specifica l'immagine di sfondo della scheda.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-109">Specifies the background image of the card.</span></span> |
| <span data-ttu-id="ff6bb-110">Corpo</span><span class="sxs-lookup"><span data-stu-id="ff6bb-110">Body</span></span> | <span data-ttu-id="ff6bb-111">Elementi della scheda da visualizzare nell'area della scheda primaria.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-111">The card elements to show in the primary card region.</span></span> |
| <span data-ttu-id="ff6bb-112">ElementType</span><span class="sxs-lookup"><span data-stu-id="ff6bb-112">ElementType</span></span> | <span data-ttu-id="ff6bb-113">Deve essere "AdaptiveCard".</span><span class="sxs-lookup"><span data-stu-id="ff6bb-113">Must be "AdaptiveCard".</span></span> |
| <span data-ttu-id="ff6bb-114">FallbackText</span><span class="sxs-lookup"><span data-stu-id="ff6bb-114">FallbackText</span></span> | <span data-ttu-id="ff6bb-115">Testo visualizzato quando il client non supporta la versione specificata (può contenere Markdown).</span><span class="sxs-lookup"><span data-stu-id="ff6bb-115">Text shown when the client doesn’t support the version specified (may contain markdown).</span></span> |
| <span data-ttu-id="ff6bb-116">Altezza</span><span class="sxs-lookup"><span data-stu-id="ff6bb-116">Height</span></span> | |
| <span data-ttu-id="ff6bb-117">InputNecessityIndicators</span><span class="sxs-lookup"><span data-stu-id="ff6bb-117">InputNecessityIndicators</span></span> | |
| <span data-ttu-id="ff6bb-118">Lingua</span><span class="sxs-lookup"><span data-stu-id="ff6bb-118">Language</span></span> | <span data-ttu-id="ff6bb-119">Lingua ISO-639-1 di 2 lettere utilizzata nella scheda.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-119">The 2-letter ISO-639-1 language used in the card.</span></span> <span data-ttu-id="ff6bb-120">Utilizzato per localizzare le funzioni di data/ora.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-120">Used to localize any date/time functions.</span></span> |
| <span data-ttu-id="ff6bb-121">Altezza minima</span><span class="sxs-lookup"><span data-stu-id="ff6bb-121">MinHeight</span></span> | <span data-ttu-id="ff6bb-122">Specifica l'altezza minima della scheda.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-122">Specifies the minimum height of the card.</span></span> |
| <span data-ttu-id="ff6bb-123">SelectAction</span><span class="sxs-lookup"><span data-stu-id="ff6bb-123">SelectAction</span></span> | <span data-ttu-id="ff6bb-124">Azione che verrà richiamata quando la scheda viene toccata o selezionata.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-124">An Action that will be invoked when the card is tapped or selected.</span></span> <span data-ttu-id="ff6bb-125">Action. ShowCard non è supportato.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-125">Action.ShowCard is not supported.</span></span> |
| <span data-ttu-id="ff6bb-126">Speak</span><span class="sxs-lookup"><span data-stu-id="ff6bb-126">Speak</span></span> | <span data-ttu-id="ff6bb-127">Specifica l'elemento da pronunciare per l'intera scheda.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-127">Specifies what should be spoken for this entire card.</span></span> <span data-ttu-id="ff6bb-128">Si tratta di un frammento di testo semplice o SSML.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-128">This is simple text or SSML fragment.</span></span> |
| <span data-ttu-id="ff6bb-129">Stile</span><span class="sxs-lookup"><span data-stu-id="ff6bb-129">Style</span></span> | |
| <span data-ttu-id="ff6bb-130">Version</span><span class="sxs-lookup"><span data-stu-id="ff6bb-130">Version</span></span> | <span data-ttu-id="ff6bb-131">Versione dello schema richiesta da questa scheda.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-131">Schema version that this card requires.</span></span> <span data-ttu-id="ff6bb-132">Se un client è inferiore a questa versione, verrà eseguito il rendering di fallbackText.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-132">If a client is lower than this version, the fallbackText will be rendered.</span></span> <span data-ttu-id="ff6bb-133">Nota: la versione non è necessaria per le schede all'interno di un'azione. ShowCard.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-133">NOTE: Version is not required for cards within an Action.ShowCard.</span></span> <span data-ttu-id="ff6bb-134">Tuttavia, è obbligatorio per la scheda di livello superiore.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-134">However, it is required for the top-level card.</span></span> |
| <span data-ttu-id="ff6bb-135">VerticalContentAlignment</span><span class="sxs-lookup"><span data-stu-id="ff6bb-135">VerticalContentAlignment</span></span> | <span data-ttu-id="ff6bb-136">Definisce il modo in cui il contenuto deve essere allineato verticalmente all'interno del contenitore.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-136">Defines how the content should be aligned vertically within the container.</span></span> <span data-ttu-id="ff6bb-137">Pertinente solo per schede a altezza fissa o schede con minHeight specificato.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-137">Only relevant for fixed-height cards, or cards with a minHeight specified.</span></span> |

&nbsp;

<span data-ttu-id="ff6bb-138">**Costruttori pubblici**</span><span class="sxs-lookup"><span data-stu-id="ff6bb-138">**Public Constructors**</span></span>

---

<a href="#ctor0"><div>
```csharp
AdaptiveCard(string version, string fallbackText, BackgroundImage backgroundImage, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight)
```
</div></a>

<a href="#ctor1"><div>
```csharp
AdaptiveCard(string version, string fallbackText, BackgroundImage backgroundImage, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight, BaseCardElementVector body, BaseActionElementVector actions)
```
</div></a>

<a href="#ctor2"><div>
```csharp
AdaptiveCard(string version, string fallbackText, string backgroundImageUrl, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight)
```
</div></a>

<a href="#ctor3"><div>
```csharp
AdaptiveCard(string version, string fallbackText, string backgroundImageUrl, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight, BaseCardElementVector body, BaseActionElementVector actions)
```
</div></a>

&nbsp;
| <span data-ttu-id="ff6bb-139">Metodi pubblici</span><span class="sxs-lookup"><span data-stu-id="ff6bb-139">Public methods</span></span> | |
| --- | ---- |
| ```static ParseResult``` | [```DeserializeFromString(string jsonString, string rendererVersion)```](#deserializefromstring0) |
| ```static ParseResult``` | [```DeserializeFromString(string jsonString, string rendererVersion, ParseContext context)```](#deserializefromstring1) |
| ```static AdaptiveCard``` | [```MakeFallbackTextCard(string fallbackText, string language, string speak)```](#makefallbacktextcard) |
| ```string``` | [```Serialize()```](#serialize) |
| ```JsonValue``` | [```SerializeToJsonValue()```](#serializetojsonvalue) |

&nbsp;
## <a name="public-constructors"></a><span data-ttu-id="ff6bb-140">Costruttori pubblici</span><span class="sxs-lookup"><span data-stu-id="ff6bb-140">Public Constructors</span></span>
---

### <a id="ctor0"></a><span data-ttu-id="ff6bb-141">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="ff6bb-141">AdaptiveCard</span></span>
<p style='text-align:right'><span data-ttu-id="ff6bb-142">Aggiunto nella versione 0,1</span><span class="sxs-lookup"><span data-stu-id="ff6bb-142">Added in version 0.1</span></span></p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    BackgroundImage backgroundImage, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment, 
                    HeightType height, 
                    long minHeight) 
```

| <span data-ttu-id="ff6bb-143">Parametri</span><span class="sxs-lookup"><span data-stu-id="ff6bb-143">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="ff6bb-144">Versione di</span><span class="sxs-lookup"><span data-stu-id="ff6bb-144">version</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-145">fallbackText</span><span class="sxs-lookup"><span data-stu-id="ff6bb-145">fallbackText</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-146">backgroundImage</span><span class="sxs-lookup"><span data-stu-id="ff6bb-146">backgroundImage</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BackgroundImage``` |
| <span data-ttu-id="ff6bb-147">stile</span><span class="sxs-lookup"><span data-stu-id="ff6bb-147">style</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| <span data-ttu-id="ff6bb-148">speak</span><span class="sxs-lookup"><span data-stu-id="ff6bb-148">speak</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-149">language</span><span class="sxs-lookup"><span data-stu-id="ff6bb-149">language</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-150">verticalContentAlignment</span><span class="sxs-lookup"><span data-stu-id="ff6bb-150">verticalContentAlignment</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| <span data-ttu-id="ff6bb-151">height</span><span class="sxs-lookup"><span data-stu-id="ff6bb-151">height</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| <span data-ttu-id="ff6bb-152">minHeight</span><span class="sxs-lookup"><span data-stu-id="ff6bb-152">minHeight</span></span> | ```long``` |

&nbsp;&nbsp;

### <a id="ctor1"></a><span data-ttu-id="ff6bb-153">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="ff6bb-153">AdaptiveCard</span></span>
<p style='text-align:right'><span data-ttu-id="ff6bb-154">Aggiunto nella versione 0,1</span><span class="sxs-lookup"><span data-stu-id="ff6bb-154">Added in version 0.1</span></span></p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    BackgroundImage backgroundImage, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment, 
                    HeightType height, 
                    long minHeight, 
                    BaseCardElementVector body, 
                    BaseActionElementVector actions)
```

| <span data-ttu-id="ff6bb-155">Parametri</span><span class="sxs-lookup"><span data-stu-id="ff6bb-155">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="ff6bb-156">Versione di</span><span class="sxs-lookup"><span data-stu-id="ff6bb-156">version</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-157">fallbackText</span><span class="sxs-lookup"><span data-stu-id="ff6bb-157">fallbackText</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-158">backgroundImage</span><span class="sxs-lookup"><span data-stu-id="ff6bb-158">backgroundImage</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BackgroundImage``` |
| <span data-ttu-id="ff6bb-159">stile</span><span class="sxs-lookup"><span data-stu-id="ff6bb-159">style</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| <span data-ttu-id="ff6bb-160">speak</span><span class="sxs-lookup"><span data-stu-id="ff6bb-160">speak</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-161">language</span><span class="sxs-lookup"><span data-stu-id="ff6bb-161">language</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-162">verticalContentAlignment</span><span class="sxs-lookup"><span data-stu-id="ff6bb-162">verticalContentAlignment</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| <span data-ttu-id="ff6bb-163">height</span><span class="sxs-lookup"><span data-stu-id="ff6bb-163">height</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| <span data-ttu-id="ff6bb-164">minHeight</span><span class="sxs-lookup"><span data-stu-id="ff6bb-164">minHeight</span></span> | ```long``` |
| <span data-ttu-id="ff6bb-165">body</span><span class="sxs-lookup"><span data-stu-id="ff6bb-165">body</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElementVector``` |
| <span data-ttu-id="ff6bb-166">azioni</span><span class="sxs-lookup"><span data-stu-id="ff6bb-166">actions</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElementVector``` |

&nbsp;&nbsp;

### <a id="ctor2"></a><span data-ttu-id="ff6bb-167">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="ff6bb-167">AdaptiveCard</span></span>
<p style='text-align:right'><span data-ttu-id="ff6bb-168">Aggiunto nella versione 0,1</span><span class="sxs-lookup"><span data-stu-id="ff6bb-168">Added in version 0.1</span></span></p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    string backgroundImageUrl, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment,
                    HeightType height, 
                    long minHeight) 
```

| <span data-ttu-id="ff6bb-169">Parametri</span><span class="sxs-lookup"><span data-stu-id="ff6bb-169">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="ff6bb-170">Versione di</span><span class="sxs-lookup"><span data-stu-id="ff6bb-170">version</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-171">fallbackText</span><span class="sxs-lookup"><span data-stu-id="ff6bb-171">fallbackText</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-172">backgroundImage</span><span class="sxs-lookup"><span data-stu-id="ff6bb-172">backgroundImage</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-173">stile</span><span class="sxs-lookup"><span data-stu-id="ff6bb-173">style</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| <span data-ttu-id="ff6bb-174">speak</span><span class="sxs-lookup"><span data-stu-id="ff6bb-174">speak</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-175">language</span><span class="sxs-lookup"><span data-stu-id="ff6bb-175">language</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-176">verticalContentAlignment</span><span class="sxs-lookup"><span data-stu-id="ff6bb-176">verticalContentAlignment</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| <span data-ttu-id="ff6bb-177">height</span><span class="sxs-lookup"><span data-stu-id="ff6bb-177">height</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| <span data-ttu-id="ff6bb-178">minHeight</span><span class="sxs-lookup"><span data-stu-id="ff6bb-178">minHeight</span></span> | ```long``` |

&nbsp;&nbsp;

### <a id="ctor3"></a><span data-ttu-id="ff6bb-179">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="ff6bb-179">AdaptiveCard</span></span>
<p style='text-align:right'><span data-ttu-id="ff6bb-180">Aggiunto nella versione 0,1</span><span class="sxs-lookup"><span data-stu-id="ff6bb-180">Added in version 0.1</span></span></p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    string backgroundImageUrl, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment,
                    HeightType height, 
                    long minHeight, 
                    BaseCardElementVector body,
                    BaseActionElementVector actions)

```

| <span data-ttu-id="ff6bb-181">Parametri</span><span class="sxs-lookup"><span data-stu-id="ff6bb-181">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="ff6bb-182">Versione di</span><span class="sxs-lookup"><span data-stu-id="ff6bb-182">version</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-183">fallbackText</span><span class="sxs-lookup"><span data-stu-id="ff6bb-183">fallbackText</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-184">backgroundImage</span><span class="sxs-lookup"><span data-stu-id="ff6bb-184">backgroundImage</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-185">stile</span><span class="sxs-lookup"><span data-stu-id="ff6bb-185">style</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| <span data-ttu-id="ff6bb-186">speak</span><span class="sxs-lookup"><span data-stu-id="ff6bb-186">speak</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-187">language</span><span class="sxs-lookup"><span data-stu-id="ff6bb-187">language</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-188">verticalContentAlignment</span><span class="sxs-lookup"><span data-stu-id="ff6bb-188">verticalContentAlignment</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| <span data-ttu-id="ff6bb-189">height</span><span class="sxs-lookup"><span data-stu-id="ff6bb-189">height</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| <span data-ttu-id="ff6bb-190">minHeight</span><span class="sxs-lookup"><span data-stu-id="ff6bb-190">minHeight</span></span> | ```long``` |
| <span data-ttu-id="ff6bb-191">body</span><span class="sxs-lookup"><span data-stu-id="ff6bb-191">body</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElementVector``` |
| <span data-ttu-id="ff6bb-192">azioni</span><span class="sxs-lookup"><span data-stu-id="ff6bb-192">actions</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElementVector``` |

&nbsp;

## <a name="public-methods"></a><span data-ttu-id="ff6bb-193">Metodi pubblici</span><span class="sxs-lookup"><span data-stu-id="ff6bb-193">Public Methods</span></span>
---
### <a id="deserializefromstring0"></a><span data-ttu-id="ff6bb-194">DeserializeFromString</span><span class="sxs-lookup"><span data-stu-id="ff6bb-194">DeserializeFromString</span></span>
<p style='text-align:right'><span data-ttu-id="ff6bb-195">Aggiunto nella versione 0.1.0</span><span class="sxs-lookup"><span data-stu-id="ff6bb-195">Added in version 0.1.0</span></span></p>

```csharp
public static ParseResult DeserializeFromString (string jsonString, string rendererVersion)
```

<span data-ttu-id="ff6bb-196">Deserializza la scheda adattiva specificata come stringa JSON per la versione del renderer specificata.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-196">Deserializes the given adaptive card as a json string for the specified renderer version.</span></span>

| <span data-ttu-id="ff6bb-197">Parametri</span><span class="sxs-lookup"><span data-stu-id="ff6bb-197">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="ff6bb-198">jsonString</span><span class="sxs-lookup"><span data-stu-id="ff6bb-198">jsonString</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-199">rendererVersion</span><span class="sxs-lookup"><span data-stu-id="ff6bb-199">rendererVersion</span></span> | ```string``` |

| <span data-ttu-id="ff6bb-200">Returns</span><span class="sxs-lookup"><span data-stu-id="ff6bb-200">Returns</span></span> | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseResult``` | |

#### <a name="sample"></a><span data-ttu-id="ff6bb-201">Esempio</span><span class="sxs-lookup"><span data-stu-id="ff6bb-201">Sample</span></span>

```csharp
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
```

--- 
### <a id="deserializefromstring1"></a><span data-ttu-id="ff6bb-202">DeserializeFromString</span><span class="sxs-lookup"><span data-stu-id="ff6bb-202">DeserializeFromString</span></span>
<p style='text-align:right'><span data-ttu-id="ff6bb-203">Aggiunto nella versione 0.1.0</span><span class="sxs-lookup"><span data-stu-id="ff6bb-203">Added in version 0.1.0</span></span></p>

```csharp
public static ParseResult DeserializeFromString(string jsonString, string rendererVersion, ParseContext context)
```

<span data-ttu-id="ff6bb-204">Deserializza la scheda adattiva specificata come stringa JSON per la versione del renderer specificata usando un oggetto [ParseContext]() per gestire l'analisi degli elementi personalizzata.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-204">Deserializes the given adaptive card as a json string for the specified renderer version using a [ParseContext]() object to handle custom element parsing.</span></span>

| <span data-ttu-id="ff6bb-205">Parametri</span><span class="sxs-lookup"><span data-stu-id="ff6bb-205">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="ff6bb-206">jsonString</span><span class="sxs-lookup"><span data-stu-id="ff6bb-206">jsonString</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-207">rendererVersion</span><span class="sxs-lookup"><span data-stu-id="ff6bb-207">rendererVersion</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-208">context</span><span class="sxs-lookup"><span data-stu-id="ff6bb-208">context</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseContext``` |

| <span data-ttu-id="ff6bb-209">Returns</span><span class="sxs-lookup"><span data-stu-id="ff6bb-209">Returns</span></span> | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseResult``` | |

#### <a name="sample"></a><span data-ttu-id="ff6bb-210">Esempio</span><span class="sxs-lookup"><span data-stu-id="ff6bb-210">Sample</span></span>

```csharp
ParseContext parseContext = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version, parseContext);
```

---

### <a id="makefallbacktextcard"></a><span data-ttu-id="ff6bb-211">MakeFallbackTextCard</span><span class="sxs-lookup"><span data-stu-id="ff6bb-211">MakeFallbackTextCard</span></span>
<p style='text-align:right'><span data-ttu-id="ff6bb-212">Aggiunto nella versione 0.1.0</span><span class="sxs-lookup"><span data-stu-id="ff6bb-212">Added in version 0.1.0</span></span></p>

```csharp
public static AdaptiveCard MakeFallbackTextCard (string fallbackText, string language, string speak)
```

<span data-ttu-id="ff6bb-213">Deserializza la scheda adattiva specificata come stringa JSON per la versione del renderer specificata.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-213">Deserializes the given adaptive card as a json string for the specified renderer version.</span></span>

| <span data-ttu-id="ff6bb-214">Parametri</span><span class="sxs-lookup"><span data-stu-id="ff6bb-214">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="ff6bb-215">fallbackText</span><span class="sxs-lookup"><span data-stu-id="ff6bb-215">fallbackText</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-216">language</span><span class="sxs-lookup"><span data-stu-id="ff6bb-216">language</span></span> | ```string``` |
| <span data-ttu-id="ff6bb-217">speak</span><span class="sxs-lookup"><span data-stu-id="ff6bb-217">speak</span></span> | ```string``` |

| <span data-ttu-id="ff6bb-218">Returns</span><span class="sxs-lookup"><span data-stu-id="ff6bb-218">Returns</span></span> | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard``` | <span data-ttu-id="ff6bb-219">Scheda adattiva che contiene il testo di fallback per una scheda unrendereable</span><span class="sxs-lookup"><span data-stu-id="ff6bb-219">Adaptive card that contains the fallback text for an unrendereable card</span></span> |

#### <a name="sample"></a><span data-ttu-id="ff6bb-220">Esempio</span><span class="sxs-lookup"><span data-stu-id="ff6bb-220">Sample</span></span>

```csharp
AdaptiveCard adaptiveCard = AdaptiveCard.MakeFallbackTextCard("This card failed to render", "es", "Unrendereable card");
```

---

### <a id="serialize"></a><span data-ttu-id="ff6bb-221">Serializzare</span><span class="sxs-lookup"><span data-stu-id="ff6bb-221">Serialize</span></span>
<p style='text-align:right'><span data-ttu-id="ff6bb-222">Aggiunto nella versione 0.1.0</span><span class="sxs-lookup"><span data-stu-id="ff6bb-222">Added in version 0.1.0</span></span></p>

```csharp
public string Serialize ()
```

<span data-ttu-id="ff6bb-223">Serializza la scheda adattiva nel formato stringa JSON.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-223">Serializes the adaptive card into it's json string form.</span></span>

| <span data-ttu-id="ff6bb-224">Returns</span><span class="sxs-lookup"><span data-stu-id="ff6bb-224">Returns</span></span> | |
| --- | --- |
| ```string``` | <span data-ttu-id="ff6bb-225">Scheda adattiva come stringa JSON</span><span class="sxs-lookup"><span data-stu-id="ff6bb-225">Adaptive card as a json string</span></span> |

#### <a name="sample"></a><span data-ttu-id="ff6bb-226">Esempio</span><span class="sxs-lookup"><span data-stu-id="ff6bb-226">Sample</span></span>

```csharp
string jsonString = parseResult.AdaptiveCard.Serialize();
```

---

### <a id="serializetojsonvalue"></a><span data-ttu-id="ff6bb-227">SerializeToJsonValue</span><span class="sxs-lookup"><span data-stu-id="ff6bb-227">SerializeToJsonValue</span></span>
<p style='text-align:right'><span data-ttu-id="ff6bb-228">Aggiunto nella versione 0.1.0</span><span class="sxs-lookup"><span data-stu-id="ff6bb-228">Added in version 0.1.0</span></span></p>

```csharp
public JsonValue SerializeToJsonValue ()
```

<span data-ttu-id="ff6bb-229">Serializza la scheda adattiva in un oggetto valore JSON.</span><span class="sxs-lookup"><span data-stu-id="ff6bb-229">Serializes the adaptive card into a json value object.</span></span>

| <span data-ttu-id="ff6bb-230">Returns</span><span class="sxs-lookup"><span data-stu-id="ff6bb-230">Returns</span></span> | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.JsonValue``` | |

#### <a name="sample"></a><span data-ttu-id="ff6bb-231">Esempio</span><span class="sxs-lookup"><span data-stu-id="ff6bb-231">Sample</span></span>

```csharp
JsonValue value = parseResult.AdaptiveCard.SerializeToJsonValue();
```