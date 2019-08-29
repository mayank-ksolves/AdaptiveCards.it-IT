---
title: Configurazione host-iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: b788ecc5c2371d2575e0165296365238535dd7c5
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553703"
---
# <a name="host-config---ios"></a>Configurazione host-iOS

L'host può essere configurato tramite HostConfig che può essere generato da una stringa JSON

```objective-c
ACOParseResult *hostconfigParseResult = [ACOHostConfig FromJson:self.hostconfig];
```

È possibile creare un'istanza di HostConfig predefinito

```objective-c
ACOHostConfig *defaultConfig = [[ACHostConfig alloc] init];
```

## <a name="render-a-card-using-host-config"></a>Eseguire il rendering di una scheda usando la configurazione host

Il renderer accetta la scheda adattiva e la configurazione dell'host. HostConfig può essere Null. In tal caso, verrà usato il valore predefinito.

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:hostconfigParseResult.config
                   widthConstraint:300.0];
```