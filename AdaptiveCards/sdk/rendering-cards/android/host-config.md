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
# <a name="host-config---android"></a>Configurazione di host - Android

Per personalizzare il renderer è fornire un'istanza dell'oggetto HostConfig. (Vedere [Schema di configurazione Host](../../../rendering-cards/host-config.md) per la descrizione completa.)

Per creare un oggetto HostConfig da una stringa, usare il metodo DeserializeFromString

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```