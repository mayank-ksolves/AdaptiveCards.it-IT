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
# <a name="host-config---android"></a>Configurazione host-Android

Per personalizzare il renderer, fornire un'istanza dell'oggetto HostConfig. Per la descrizione completa, vedere [schema di configurazione host](../../../rendering-cards/host-config.md) .

Per creare un oggetto HostConfig da una stringa, usare il Metodo DeserializeFromString

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```