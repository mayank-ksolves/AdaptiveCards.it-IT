---
title: Configurazione host-.NET HTML SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: a51b64f5f9783a187d7c3eb56c563a1d4497d3e2
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454994"
---
# <a name="host-config---net-html"></a>Configurazione host-HTML .NET

Una [configurazione dell'host](../../../rendering-cards/host-config.md) è un oggetto di configurazione condiviso che può essere interpretato da tutti i renderer. Questo consente di definire stili comuni (ad esempio, famiglia di caratteri, dimensioni dei caratteri, spaziatura predefinita) e comportamenti (ad esempio, numero massimo di azioni) che verranno interpretati automaticamente dal renderer di ogni piattaforma. 

L'obiettivo è che l'interfaccia utente nativa generata dal renderer di ogni piattaforma abbia un aspetto molto simile, con un intervento minimo da parte dello sviluppatore.

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