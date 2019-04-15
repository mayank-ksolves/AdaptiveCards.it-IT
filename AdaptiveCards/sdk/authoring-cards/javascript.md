---
title: JavaScript SDK per le schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 6372f2f23a817ecc4d07d950d6513d14357547b7
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552663"
---
# <a name="javascript-sdk-for-creating-cards"></a><span data-ttu-id="8b695-102">JavaScript SDK per la creazione di schede</span><span class="sxs-lookup"><span data-stu-id="8b695-102">JavaScript SDK for creating cards</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8b695-103">La libreria per la serializzazione JSON è ancora in fase di sviluppo e il milage può variare.</span><span class="sxs-lookup"><span data-stu-id="8b695-103">The library for serializing JSON is still in development and your milage may vary.</span></span>

<span data-ttu-id="8b695-104">Come illustrato nelle operazioni preliminari sezione, una scheda adattiva è nient'altro, un oggetto json serializzato di un modello di oggetto di biglietto.</span><span class="sxs-lookup"><span data-stu-id="8b695-104">As we described in the getting started section, an adaptive card is nothing more then a serialized json object of a card object model.</span></span>  <span data-ttu-id="8b695-105">Per renderlo semplice modificare il modello a oggetti è stato definito alcune librerie che consentono di definire una gerarchia di classi fortemente tipizzate che è facile da serializzare o deserializzare json.</span><span class="sxs-lookup"><span data-stu-id="8b695-105">To make it easy to manipulate the object model we have defined some libraries which define a strongly typed class hierarchy that is easy to serialize/deserialize json.</span></span>

<span data-ttu-id="8b695-106">È possibile usare qualsiasi strumento che si desidera creare il codice json scheda adattiva.</span><span class="sxs-lookup"><span data-stu-id="8b695-106">You can use any tooling that you want to create the adaptive card json.</span></span>

<span data-ttu-id="8b695-107">Il `adaptivecards` pacchetto npm definisce una libreria per l'utilizzo con le schede adattive in javascript</span><span class="sxs-lookup"><span data-stu-id="8b695-107">The `adaptivecards` npm package defines a library for working with adaptive cards in javascript</span></span>

## <a name="to-install"></a><span data-ttu-id="8b695-108">Per installare</span><span class="sxs-lookup"><span data-stu-id="8b695-108">To install</span></span>
```console
npm install adaptivecards
```

## <a name="example-creating"></a><span data-ttu-id="8b695-109">Creazione di esempio</span><span class="sxs-lookup"><span data-stu-id="8b695-109">Example creating</span></span> 
<span data-ttu-id="8b695-110">Sono disponibili le definizioni di interfaccia in `schema.d.ts` che descrivono la forma dello schema</span><span class="sxs-lookup"><span data-stu-id="8b695-110">There are interface definitions in `schema.d.ts` which describe the shape of the schema</span></span>

```typescript
let card = {
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "Container",
            "items": [
                {
                    "type": "TextBlock",
                    "text": "Meow!"
                },
                {
                    "type": "Image",
                    "url": "http://adaptivecards.io/content/cats/1.png"
                }
            ]
        }
    ]
};
```

<span data-ttu-id="8b695-111">È inoltre disponibile un modello a oggetti per la creazione di schede.</span><span class="sxs-lookup"><span data-stu-id="8b695-111">There is also an object model for creating cards.</span></span>


```typescript
let card :IAdaptiveCard =  new AdaptiveCard();
card.body.add(new TextBlock() 
{
    text = "hello world"
});
```
