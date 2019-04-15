---
title: Host config - UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 85c8807d2a368e00b414b427fae8a9f0253873c8
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553673"
---
# <a name="host-config---uwp"></a>Configurazione di host - UWP

Per personalizzare il renderer è fornire un'istanza dell'oggetto HostConfig. (Vedere [Schema di configurazione Host](../../../rendering-cards/host-config.md) per la descrizione completa.)

> Verrà creata un'istanza di oggetto HostConfig con valori predefiniti, pertanto è possibile impostare solo le proprietà che si desidera modificare.

Esempio:

```csharp
var hostConfig = new AdaptiveHostConfig() 
{
    FontSizes = {
        Small = 15,
        Normal = 20,
        Medium = 25,
        Large = 30,
        ExtraLarge= 40
    }
};
renderer.HostConfig = hostConfig;
```

> In alternativa, è possibile caricare il HostConfig da una stringa JSON.

Esempio:

```csharp
var hostConfig = AdaptiveHostConfig.FromJsonString(jsonString); 

renderer.HostConfig = hostConfig;
```

Quando si passa al UWPRenderer si imposta il valore predefinito HostConfig da usare per ogni scheda che è eseguire il rendering.