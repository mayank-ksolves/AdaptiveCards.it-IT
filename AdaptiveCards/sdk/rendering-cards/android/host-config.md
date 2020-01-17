---
title: Configurazione host-Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 091e2093c380affc8c895d069a2f52061b991d2f
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145491"
---
# <a name="host-config---android"></a><span data-ttu-id="50197-102">Configurazione host-Android</span><span class="sxs-lookup"><span data-stu-id="50197-102">Host config - Android</span></span>

<span data-ttu-id="50197-103">Per personalizzare il renderer, fornire un'istanza dell'oggetto HostConfig.</span><span class="sxs-lookup"><span data-stu-id="50197-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="50197-104">Per la descrizione completa, vedere [schema di configurazione host](../../../rendering-cards/host-config.md) .</span><span class="sxs-lookup"><span data-stu-id="50197-104">(See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)</span></span>

<span data-ttu-id="50197-105">Per creare un oggetto HostConfig da una stringa, usare il Metodo DeserializeFromString</span><span class="sxs-lookup"><span data-stu-id="50197-105">To Create a HostConfig object from a string, use the DeserializeFromString method</span></span>

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```