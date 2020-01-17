---
title: Classe AdaptiveCardRenderer-Novell. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: c90fb22f60fa75a37b6372c2660f8599535fd961
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146065"
---
# <a name="adaptivecardrenderer"></a><span data-ttu-id="28feb-102">AdaptiveCardRenderer</span><span class="sxs-lookup"><span data-stu-id="28feb-102">AdaptiveCardRenderer</span></span>

```csharp
public class AdaptiveCardRenderer : global::Java.Lang.Object
```

<span data-ttu-id="28feb-103">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="28feb-103">**Namespace**</span></span>
```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer
```

### <a name="summary"></a><span data-ttu-id="28feb-104">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="28feb-104">Summary</span></span>

| <span data-ttu-id="28feb-105">Metodi pubblici</span><span class="sxs-lookup"><span data-stu-id="28feb-105">Public methods</span></span> | |
| --- | ---- |
| ```RenderedAdaptiveCard``` | [```Render (Context context, FragmentManager fragmentManager, AdaptiveCard adaptiveCard, ICardActionHandler cardActionHandler)```](#render0) |
| ```RenderedAdaptiveCard``` | [```Render (Context context, FragmentManager fragmentManager, AdaptiveCard adaptiveCard, ICardActionHandler cardActionHandler, HostConfig hostConfig)```](#render1) |

## <a name="public-methods"></a><span data-ttu-id="28feb-106">Metodi pubblici</span><span class="sxs-lookup"><span data-stu-id="28feb-106">Public Methods</span></span>

---

### <a id="render0"></a><span data-ttu-id="28feb-107">Rendering</span><span class="sxs-lookup"><span data-stu-id="28feb-107">Render</span></span>
<p style='text-align:right'><span data-ttu-id="28feb-108">Aggiunto nella versione 0.1.0</span><span class="sxs-lookup"><span data-stu-id="28feb-108">Added in version 0.1.0</span></span></p>

```csharp
public RenderedAdaptiveCard Render (Context context, 
                                    FragmentManager fragmentManager, 
                                    AdaptiveCard adaptiveCard,
                                    ICardActionHandler cardActionHandler)
```

<span data-ttu-id="28feb-109">Esegue il rendering della scheda adattiva specificata con i valori predefiniti per la configurazione host.</span><span class="sxs-lookup"><span data-stu-id="28feb-109">Renders the specified adaptive card with default values for the host config.</span></span>

| <span data-ttu-id="28feb-110">Parametri</span><span class="sxs-lookup"><span data-stu-id="28feb-110">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="28feb-111">context</span><span class="sxs-lookup"><span data-stu-id="28feb-111">context</span></span> | ```Android.Content.Context``` |
| <span data-ttu-id="28feb-112">fragmentManager</span><span class="sxs-lookup"><span data-stu-id="28feb-112">fragmentManager</span></span> | ```Android.Support.V4.App.FragmentManager``` |
| <span data-ttu-id="28feb-113">adaptiveCard</span><span class="sxs-lookup"><span data-stu-id="28feb-113">adaptiveCard</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard```](adaptivecards-rendering-xamarin-android-objectmodel-adaptivecard.md) |
| <span data-ttu-id="28feb-114">cardActionHandler</span><span class="sxs-lookup"><span data-stu-id="28feb-114">cardActionHandler</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler.ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md) |

| <span data-ttu-id="28feb-115">Returns</span><span class="sxs-lookup"><span data-stu-id="28feb-115">Returns</span></span> |
| --- | --- |
| [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md) | |

#### <a name="sample"></a><span data-ttu-id="28feb-116">Esempio</span><span class="sxs-lookup"><span data-stu-id="28feb-116">Sample</span></span>

```csharp
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.Instance.Render(context, SupportFragmentManager, parseResult.AdaptiveCard, cardActionHandler);
```

---

### <a id="render1"></a><span data-ttu-id="28feb-117">Rendering</span><span class="sxs-lookup"><span data-stu-id="28feb-117">Render</span></span>
<p style='text-align:right'><span data-ttu-id="28feb-118">Aggiunto nella versione 0.1.0</span><span class="sxs-lookup"><span data-stu-id="28feb-118">Added in version 0.1.0</span></span></p>

```csharp
RenderedAdaptiveCard Render (Context context, 
                            FragmentManager fragmentManager, 
                            AdaptiveCard adaptiveCard, 
                            ICardActionHandler cardActionHandler, 
                            HostConfig hostConfig)
```

<span data-ttu-id="28feb-119">Esegue il rendering della scheda adattiva specificata con utilizzando la configurazione host specificata.</span><span class="sxs-lookup"><span data-stu-id="28feb-119">Renders the specified adaptive card with using the given host config.</span></span>

| <span data-ttu-id="28feb-120">Parametri</span><span class="sxs-lookup"><span data-stu-id="28feb-120">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="28feb-121">context</span><span class="sxs-lookup"><span data-stu-id="28feb-121">context</span></span> | ```Android.Content.Context``` |
| <span data-ttu-id="28feb-122">fragmentManager</span><span class="sxs-lookup"><span data-stu-id="28feb-122">fragmentManager</span></span> | ```Android.Support.V4.App.FragmentManager``` |
| <span data-ttu-id="28feb-123">adaptiveCard</span><span class="sxs-lookup"><span data-stu-id="28feb-123">adaptiveCard</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard```](adaptivecards-rendering-xamarin-android-objectmodel-adaptivecard.md) |
| <span data-ttu-id="28feb-124">cardActionHandler</span><span class="sxs-lookup"><span data-stu-id="28feb-124">cardActionHandler</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler.ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md) |
| <span data-ttu-id="28feb-125">hostConfig</span><span class="sxs-lookup"><span data-stu-id="28feb-125">hostConfig</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HostConfig``` |

| <span data-ttu-id="28feb-126">Returns</span><span class="sxs-lookup"><span data-stu-id="28feb-126">Returns</span></span> | |
| --- | --- |
| [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md) | |

#### <a name="sample"></a><span data-ttu-id="28feb-127">Esempio</span><span class="sxs-lookup"><span data-stu-id="28feb-127">Sample</span></span>

```csharp
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.Instance.Render(context, SupportFragmentManager, parseResult.AdaptiveCard, cardActionHandler, hostConfig);
```