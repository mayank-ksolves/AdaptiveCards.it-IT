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
# <a name="net-sdk-for-authoring-cards"></a>.NET SDK per la creazione di schede

Come descritto nella pagina [Introduzione](../../authoring-cards/getting-started.md) , una scheda adattiva è un modello a oggetti JSON. La libreria .NET rende molto più semplice l'uso di tale JSON.

> [!IMPORTANT]
> **Modifiche di rilievo da v 0,5**
> 
> 1. Il pacchetto è stato rinominato da `Microsoft.AdaptiveCards` a`AdaptiveCards`
> 1. A causa di conflitti di nomi frequenti con i tipi di Framework, tutte le classi modello sono state precedute dal prefisso "Adaptive". Ad esempio, `TextBlock` è ora`AdaptiveTextBlock`
> 1. Tutte le proprietà "URI" sono state modificate `string` dal tipo in`Uri`
> 1. Sono state apportate anche alcune modifiche dello schema rispetto alla versione 0.5 Preview, [descritte qui](https://github.com/Microsoft/AdaptiveCards/pull/633)


## <a name="nuget-install"></a>Installazione di NuGet
Il `AdaptiveCards` pacchetto NuGet fornisce tipi per l'uso di schede adattive in .NET

[![Installazione di NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)

```console
Install-Package AdaptiveCards -IncludePrerelease
```

## <a name="example-create-an-adaptivecard-and-serialize-to-json"></a>Esempio: Creare una AdaptiveCard e serializzarla in JSON

Questo esempio illustra come compilare una scheda adattiva usando oggetti standard C# e quindi serializzarla in JSON per il trasporto in transito.

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

## <a name="example-parse-an-adaptivecard-from-json"></a>Esempio: Analizzare un AdaptiveCard da JSON

Questo esempio illustra come analizzare un payload JSON in una scheda adattiva. Questo semplifica la manipolazione del modello a oggetti o persino il rendering di schede adattive all'interno dell'app usando gli [SDK renderer](../../rendering-cards/getting-started.md).

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
