---
title: Ospitare config - Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: c44cf609fd52423a1ca17988a875c6dc48550007
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553343"
---
# <a name="host-config---android"></a><span data-ttu-id="322ec-102">Configurazione di host - Android</span><span class="sxs-lookup"><span data-stu-id="322ec-102">Host config - Android</span></span>

<span data-ttu-id="322ec-103">Per personalizzare il renderer è fornire un'istanza dell'oggetto HostConfig.</span><span class="sxs-lookup"><span data-stu-id="322ec-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="322ec-104">(Vedere [Schema di configurazione Host](../../../rendering-cards/host-config.md) per la descrizione completa.)</span><span class="sxs-lookup"><span data-stu-id="322ec-104">(See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)</span></span>

<span data-ttu-id="322ec-105">Per creare un oggetto HostConfig da una stringa, usare il metodo DeserializeFromString</span><span class="sxs-lookup"><span data-stu-id="322ec-105">To Create a HostConfig object from a string, use the DeserializeFromString method</span></span>

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```