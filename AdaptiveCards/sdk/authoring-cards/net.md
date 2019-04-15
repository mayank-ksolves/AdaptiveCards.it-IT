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
# <a name="net-sdk-for-authoring-cards"></a>.NET SDK per la creazione di schede

Come illustrato nel [introduttiva](../../authoring-cards/getting-started.md) pagina, una scheda adattiva è un modello a oggetti JSON. La libreria .NET semplifica molto più semplice l'uso con tale codice JSON.

> [!IMPORTANT]
> **Modifiche di rilievo rispetto versione 0.5**
> 
> 1. Pacchetto rinominato da `Microsoft.AdaptiveCards` a `AdaptiveCards`
> 1. A causa di conflitti di nomi di frequente con i tipi di framework, tutte le classi modello sono state precedute "Adaptive". Ad esempio, `TextBlock` è ora `AdaptiveTextBlock`
> 1. Tutte le proprietà "uri" sono state modificate da tipo `string` a `Uri`
> 1. Sono state apportate anche alcune modifiche dello schema dalla versione di anteprima versione 0.5, ovvero [descritti qui](https://github.com/Microsoft/AdaptiveCards/pull/633)


## <a name="nuget-install"></a>Installazione di NuGet
Il `AdaptiveCards` pacchetto NuGet fornisce tipi per lavorare con le schede adattive in .NET

[![Installazione di NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)

```console
Install-Package AdaptiveCards -IncludePrerelease
```

## <a name="example-create-an-adaptivecard-and-serialize-to-json"></a>Esempio: Creare un AdaptiveCard e serializzare in JSON

In questo esempio viene illustrato come creare una scheda adattiva usando standard di C# degli oggetti e quindi eseguirne la serializzazione in JSON per il trasporto in rete.

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

In questo esempio viene illustrato come analizzare un payload JSON in una scheda adattiva. Questo rende facile modificare il modello a oggetti o anche eseguire il rendering le schede adattive all'interno dell'app tramite il [renderer SDK](../../rendering-cards/getting-started.md).

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
