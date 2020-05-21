---
title: Configurazione host-iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 614fc4a91941f59e422470c37ee90faa547bcede
ms.sourcegitcommit: c921a7bb15a95c0ceb803ad375501ee3b8bef028
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2020
ms.locfileid: "83631299"
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

Renderer acquisisce scheda e configurazione host. HostConfig può essere null e, se Nil, verrà usato il valore predefinito.

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
