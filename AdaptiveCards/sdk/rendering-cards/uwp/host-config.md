---
title: Configurazione host-UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 6f14830a643b064c6169cf3143bbc7cd4ce45937
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454974"
---
# <a name="host-config---uwp"></a>Configurazione host-UWP

Per personalizzare il renderer, fornire un'istanza dell'oggetto HostConfig. Per la descrizione completa, vedere [schema di configurazione host](../../../rendering-cards/host-config.md) .

> Verrà creata un'istanza dell'oggetto HostConfig con le impostazioni predefinite, quindi è possibile impostare solo le proprietà che si desidera modificare.

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

> In alternativa, è possibile caricare HostConfig da una stringa JSON.

Esempio:

```csharp
var hostConfig = AdaptiveHostConfig.FromJsonString(jsonString); 

renderer.HostConfig = hostConfig;
```

Quando si passa a UWPRenderer, si imposta il valore predefinito di HostConfig da usare per ogni scheda sottoposta a rendering.