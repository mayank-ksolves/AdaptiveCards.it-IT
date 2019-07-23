---
title: .NET SDK per schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 10/01/2017
ms.topic: article
ms.openlocfilehash: fa86d83a8f20490ec286b69653099ac8cd81b8ef
ms.sourcegitcommit: 4d80c553ab574befa8c84706fd85d22077915745
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387353"
---
# <a name="net-sdk-for-authoring-cards"></a><span data-ttu-id="c2a5f-102">.NET SDK per la creazione di schede</span><span class="sxs-lookup"><span data-stu-id="c2a5f-102">.NET SDK for Authoring Cards</span></span>

<span data-ttu-id="c2a5f-103">Come descritto nella pagina [Introduzione](../../authoring-cards/getting-started.md) , una scheda adattiva è un modello a oggetti JSON.</span><span class="sxs-lookup"><span data-stu-id="c2a5f-103">As we described in the [Getting Started](../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON object model.</span></span> <span data-ttu-id="c2a5f-104">La libreria .NET rende molto più semplice l'uso di tale JSON.</span><span class="sxs-lookup"><span data-stu-id="c2a5f-104">The .NET library makes working with that JSON much easier.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c2a5f-105">**Modifiche di rilievo da v 0,5**</span><span class="sxs-lookup"><span data-stu-id="c2a5f-105">**Breaking changes from v0.5**</span></span>
> 
> 1. <span data-ttu-id="c2a5f-106">Il pacchetto è stato rinominato da `Microsoft.AdaptiveCards` a`AdaptiveCards`</span><span class="sxs-lookup"><span data-stu-id="c2a5f-106">Package renamed from `Microsoft.AdaptiveCards` to `AdaptiveCards`</span></span>
> 1. <span data-ttu-id="c2a5f-107">A causa di conflitti di nomi frequenti con i tipi di Framework, tutte le classi modello sono state precedute dal prefisso "Adaptive".</span><span class="sxs-lookup"><span data-stu-id="c2a5f-107">Due to frequent name collisions with framework types, all model classes have been prefixed with "Adaptive".</span></span> <span data-ttu-id="c2a5f-108">Ad esempio, `TextBlock` è ora`AdaptiveTextBlock`</span><span class="sxs-lookup"><span data-stu-id="c2a5f-108">E.g., `TextBlock` is now `AdaptiveTextBlock`</span></span>
> 1. <span data-ttu-id="c2a5f-109">Tutte le proprietà "URI" sono state modificate `string` dal tipo in`Uri`</span><span class="sxs-lookup"><span data-stu-id="c2a5f-109">All "uri" properties were changed from type `string` to `Uri`</span></span>
> 1. <span data-ttu-id="c2a5f-110">Sono state apportate anche alcune modifiche dello schema rispetto alla versione 0.5 Preview, [descritte qui](https://github.com/Microsoft/AdaptiveCards/pull/633)</span><span class="sxs-lookup"><span data-stu-id="c2a5f-110">There have also been some schema changes from the v0.5 preview, which are [outlined here](https://github.com/Microsoft/AdaptiveCards/pull/633)</span></span>


## <a name="nuget-install"></a><span data-ttu-id="c2a5f-111">Installazione di NuGet</span><span class="sxs-lookup"><span data-stu-id="c2a5f-111">NuGet Install</span></span>
<span data-ttu-id="c2a5f-112">Il `AdaptiveCards` pacchetto NuGet fornisce tipi per l'uso di schede adattive in .NET</span><span class="sxs-lookup"><span data-stu-id="c2a5f-112">The `AdaptiveCards` NuGet package provides types for working with adaptive cards in .NET</span></span>

<span data-ttu-id="c2a5f-113">[![Installazione di NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span><span class="sxs-lookup"><span data-stu-id="c2a5f-113">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span></span>

```console
Install-Package AdaptiveCards -IncludePrerelease
```

## <a name="example-create-an-adaptivecard-and-serialize-to-json"></a><span data-ttu-id="c2a5f-114">Esempio: Creare una AdaptiveCard e serializzarla in JSON</span><span class="sxs-lookup"><span data-stu-id="c2a5f-114">Example: Create an AdaptiveCard and serialize to JSON</span></span>

<span data-ttu-id="c2a5f-115">Questo esempio illustra come compilare una scheda adattiva usando oggetti standard C# e quindi serializzarla in JSON per il trasporto in transito.</span><span class="sxs-lookup"><span data-stu-id="c2a5f-115">This example demonstrates how to build an Adaptive Card using standard C# objects and then serialize it to JSON for transport over the wire.</span></span>

```csharp
using AdaptiveCards;
// ...

AdaptiveCard card = new AdaptiveCard();

card.Body.Add(new AdaptiveTextBlock() 
{
    Text = "Hello",
    Size = AdaptiveTextSize.ExtraLarge
});

card.Body.Add(new AdaptiveImage() 
{
    Url = new Uri("http://adaptivecards.io/content/cats/1.png")
});

// serialize the card to JSON
string json = card.ToJson();
```

## <a name="example-parse-an-adaptivecard-from-json"></a><span data-ttu-id="c2a5f-116">Esempio: Analizzare un AdaptiveCard da JSON</span><span class="sxs-lookup"><span data-stu-id="c2a5f-116">Example: Parse an AdaptiveCard from JSON</span></span>

<span data-ttu-id="c2a5f-117">Questo esempio illustra come analizzare un payload JSON in una scheda adattiva.</span><span class="sxs-lookup"><span data-stu-id="c2a5f-117">This example demonstrates how to parse a JSON payload into an Adaptive Card.</span></span> <span data-ttu-id="c2a5f-118">Questo semplifica la manipolazione del modello a oggetti o persino il rendering di schede adattive all'interno dell'app usando gli [SDK renderer](../../rendering-cards/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="c2a5f-118">This makes it easy to manipulate the object model or even render Adaptive Cards inside your app by using our [renderer SDKs](../../rendering-cards/getting-started.md).</span></span>

```csharp
try
{
    // Get a JSON-serialized payload
    // Your app will probably get cards from somewhere else :)
    var client = new HttpClient();
    var response = await client.GetAsync("http://adaptivecards.io/payloads/ActivityUpdate.json");
    var json = await response.Content.ReadAsStringAsync();

    // Parse the JSON 
    AdaptiveCardParseResult result = AdaptiveCard.FromJson(json);

    // Get card from result
    AdaptiveCard card = result.Card;

    // Optional: check for any parse warnings
    // This includes things like unknown element "type"
    // or unknown properties on element
    IList<AdaptiveWarning> warnings = result.Warnings;
}
catch(AdaptiveSerializationException ex)
{
    // Failed to deserialize card 
    // This occurs from malformed JSON
    // or schema violations like required properties missing 
}
```
