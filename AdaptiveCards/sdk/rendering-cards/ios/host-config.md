---
title: Configurazione host-iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: fa420c0a6e9e9b7e5713b6cc528de39335f0b56c
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727480"
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

Rederer accetta la configurazione dell'host e della scheda adattiva. HostConfig può essere null e, se Nil, verrà usato il valore predefinito.

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:hostconfigParseResult.config
                   widthConstraint:300.0];
```

## <a name="customization"></a>Personalizzazione

Sono disponibili tre modi per personalizzare il rendering adattivo della scheda:

1. Configurazione dell'host
2. XIB
3. Rendering di elementi personalizzati
