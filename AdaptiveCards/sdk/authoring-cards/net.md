---
title: .NET SDK per le schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 10/01/2017
ms.topic: article
ms.openlocfilehash: 37dec7651a574194eb00d46014431dfb5764f9b7
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553743"
---
# <a name="net-sdk-for-authoring-cards"></a><span data-ttu-id="e8a52-102">.NET SDK per la creazione di schede</span><span class="sxs-lookup"><span data-stu-id="e8a52-102">.NET SDK for Authoring Cards</span></span>

<span data-ttu-id="e8a52-103">Come illustrato nel [introduttiva](../../authoring-cards/getting-started.md) pagina, una scheda adattiva è un modello a oggetti JSON.</span><span class="sxs-lookup"><span data-stu-id="e8a52-103">As we described in the [Getting Started](../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON object model.</span></span> <span data-ttu-id="e8a52-104">La libreria .NET semplifica molto più semplice l'uso con tale codice JSON.</span><span class="sxs-lookup"><span data-stu-id="e8a52-104">The .NET library makes working with that JSON much easier.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8a52-105">**Modifiche di rilievo rispetto versione 0.5**</span><span class="sxs-lookup"><span data-stu-id="e8a52-105">**Breaking changes from v0.5**</span></span>
> 
> 1. <span data-ttu-id="e8a52-106">Pacchetto rinominato da `Microsoft.AdaptiveCards` a `AdaptiveCards`</span><span class="sxs-lookup"><span data-stu-id="e8a52-106">Package renamed from `Microsoft.AdaptiveCards` to `AdaptiveCards`</span></span>
> 1. <span data-ttu-id="e8a52-107">A causa di conflitti di nomi di frequente con i tipi di framework, tutte le classi modello sono state precedute "Adaptive".</span><span class="sxs-lookup"><span data-stu-id="e8a52-107">Due to frequent name collisions with framework types, all model classes have been prefixed with "Adaptive".</span></span> <span data-ttu-id="e8a52-108">Ad esempio, `TextBlock` è ora `AdaptiveTextBlock`</span><span class="sxs-lookup"><span data-stu-id="e8a52-108">E.g., `TextBlock` is now `AdaptiveTextBlock`</span></span>
> 1. <span data-ttu-id="e8a52-109">Tutte le proprietà "uri" sono state modificate da tipo `string` a `Uri`</span><span class="sxs-lookup"><span data-stu-id="e8a52-109">All "uri" properties were changed from type `string` to `Uri`</span></span>
> 1. <span data-ttu-id="e8a52-110">Sono state apportate anche alcune modifiche dello schema dalla versione di anteprima versione 0.5, ovvero [descritti qui](https://github.com/Microsoft/AdaptiveCards/pull/633)</span><span class="sxs-lookup"><span data-stu-id="e8a52-110">There have also been some schema changes from the v0.5 preview, which are [outlined here](https://github.com/Microsoft/AdaptiveCards/pull/633)</span></span>


## <a name="nuget-install"></a><span data-ttu-id="e8a52-111">Installazione di NuGet</span><span class="sxs-lookup"><span data-stu-id="e8a52-111">NuGet Install</span></span>
<span data-ttu-id="e8a52-112">Il `AdaptiveCards` pacchetto NuGet fornisce tipi per lavorare con le schede adattive in .NET</span><span class="sxs-lookup"><span data-stu-id="e8a52-112">The `AdaptiveCards` NuGet package provides types for working with adaptive cards in .NET</span></span>

<span data-ttu-id="e8a52-113">[![Installazione di NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span><span class="sxs-lookup"><span data-stu-id="e8a52-113">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span></span>

```console
Install-Package AdaptiveCards -IncludePrerelease
```

## <a name="example-create-an-adaptivecard-and-serialize-to-json"></a><span data-ttu-id="e8a52-114">Esempio: Creare un AdaptiveCard e serializzare in JSON</span><span class="sxs-lookup"><span data-stu-id="e8a52-114">Example: Create an AdaptiveCard and serialize to JSON</span></span>

<span data-ttu-id="e8a52-115">In questo esempio viene illustrato come creare una scheda adattiva usando standard di C# degli oggetti e quindi eseguirne la serializzazione in JSON per il trasporto in rete.</span><span class="sxs-lookup"><span data-stu-id="e8a52-115">This example demonstrates how to build an Adaptive Card using standard C# objects and then serialize it to JSON for transport over the wire.</span></span>

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

## <a name="example-parse-an-adaptivecard-from-json"></a><span data-ttu-id="e8a52-116">Esempio: Analizzare un AdaptiveCard da JSON</span><span class="sxs-lookup"><span data-stu-id="e8a52-116">Example: Parse an AdaptiveCard from JSON</span></span>

<span data-ttu-id="e8a52-117">In questo esempio viene illustrato come analizzare un payload JSON in una scheda adattiva.</span><span class="sxs-lookup"><span data-stu-id="e8a52-117">This example demonstrates how to parse a JSON payload into an Adaptive Card.</span></span> <span data-ttu-id="e8a52-118">Questo rende facile modificare il modello a oggetti o anche eseguire il rendering le schede adattive all'interno dell'app tramite il [renderer SDK](../../rendering-cards/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="e8a52-118">This makes it easy to manipulate the object model or even render Adaptive Cards inside your app by using our [renderer SDKs](../../rendering-cards/getting-started.md).</span></span>

```csharp
try
{
    // Get a JSON-serialized payload
    // Your app will probably get cards from somewhere else :)
    var client = new HttpClient("http://adaptivecards.io/payloads/ActivityUpdate.json");
    var response = await client.GetAsync(cardUrl);
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
