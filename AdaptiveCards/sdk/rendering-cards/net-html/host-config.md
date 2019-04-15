---
title: Configurazione di host - HTML .NET SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: dc5b6767d5f8611111b56f30f05a7b5fc8d1cbf4
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552413"
---
# <a name="host-config---net-html"></a>Configurazione - .NET HTML host

Oggetto [Host Config](../../../rendering-cards/host-config.md) è un oggetto di configurazione condivisa che comprendere tutti i renderer. In questo modo è possibile definire stili comuni (ad esempio, famiglia di caratteri, le dimensioni dei caratteri, spaziatura predefinita) e i comportamenti (ad esempio, numero massimo di azioni) che verranno interpretati automaticamente dal renderer ogni piattaforma. 

L'obiettivo è che l'interfaccia utente nativa generato da ogni renderer piattaforma avrà un aspetto molto simile con un intervento minimo da parte dell'utente.

```csharp
// Construct programmatically
renderer.HostConfig = new AdaptiveHostConfig() 
{
    FontFamily = "Comic Sans",
    FontSizes = {
        Small = 15,
        Default = 20,
        Medium = 25,
        Large = 30,
        ExtraLarge= 40
    }
};

// Or parse from JSON
renderer.HostConfig  = AdaptiveHostConfig.FromJson(@"{
    ""fontFamily"": ""Comic Sans"",
    ""fontSizes"": {
        ""small"": 25,
        ""default"": 26,
        ""medium"": 27,
        ""large"": 28,
        ""extraLarge"": 29
    }
}");
```