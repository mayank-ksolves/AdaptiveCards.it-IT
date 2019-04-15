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
# <a name="javascript-sdk-for-creating-cards"></a>JavaScript SDK per la creazione di schede

> [!IMPORTANT]
> La libreria per la serializzazione JSON è ancora in fase di sviluppo e il milage può variare.

Come illustrato nelle operazioni preliminari sezione, una scheda adattiva è nient'altro, un oggetto json serializzato di un modello di oggetto di biglietto.  Per renderlo semplice modificare il modello a oggetti è stato definito alcune librerie che consentono di definire una gerarchia di classi fortemente tipizzate che è facile da serializzare o deserializzare json.

È possibile usare qualsiasi strumento che si desidera creare il codice json scheda adattiva.

Il `adaptivecards` pacchetto npm definisce una libreria per l'utilizzo con le schede adattive in javascript

## <a name="to-install"></a>Per installare
```console
npm install adaptivecards
```

## <a name="example-creating"></a>Creazione di esempio 
Sono disponibili le definizioni di interfaccia in `schema.d.ts` che descrivono la forma dello schema

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

È inoltre disponibile un modello a oggetti per la creazione di schede.


```typescript
let card :IAdaptiveCard =  new AdaptiveCard();
card.body.add(new TextBlock() 
{
    text = "hello world"
});
```
