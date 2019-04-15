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
# <a name="host-config---uwp"></a><span data-ttu-id="29c11-102">Configurazione di host - UWP</span><span class="sxs-lookup"><span data-stu-id="29c11-102">Host config - UWP</span></span>

<span data-ttu-id="29c11-103">Per personalizzare il renderer è fornire un'istanza dell'oggetto HostConfig.</span><span class="sxs-lookup"><span data-stu-id="29c11-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="29c11-104">(Vedere [Schema di configurazione Host](../../../rendering-cards/host-config.md) per la descrizione completa.)</span><span class="sxs-lookup"><span data-stu-id="29c11-104">(See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)</span></span>

> <span data-ttu-id="29c11-105">Verrà creata un'istanza di oggetto HostConfig con valori predefiniti, pertanto è possibile impostare solo le proprietà che si desidera modificare.</span><span class="sxs-lookup"><span data-stu-id="29c11-105">The HostConfig object will be instantiated with defaults, so you can set just the properties you want to change.</span></span>

<span data-ttu-id="29c11-106">Esempio:</span><span class="sxs-lookup"><span data-stu-id="29c11-106">Example:</span></span>

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

> <span data-ttu-id="29c11-107">In alternativa, è possibile caricare il HostConfig da una stringa JSON.</span><span class="sxs-lookup"><span data-stu-id="29c11-107">Alternatively, you can load the HostConfig from a JSON string.</span></span>

<span data-ttu-id="29c11-108">Esempio:</span><span class="sxs-lookup"><span data-stu-id="29c11-108">Example:</span></span>

```csharp
var hostConfig = AdaptiveHostConfig.FromJsonString(jsonString); 

renderer.HostConfig = hostConfig;
```

<span data-ttu-id="29c11-109">Quando si passa al UWPRenderer si imposta il valore predefinito HostConfig da usare per ogni scheda che è eseguire il rendering.</span><span class="sxs-lookup"><span data-stu-id="29c11-109">When you pass it in to the UWPRenderer you are setting the default HostConfig to use for every card you render.</span></span>