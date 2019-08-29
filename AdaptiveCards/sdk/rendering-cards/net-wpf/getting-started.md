---
title: SDK WPF .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: a3f63fc812c97014af06dd1a197b24c5d07361c2
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553623"
---
# <a name="getting-started---net-wpf"></a>Introduzione-WPF .NET

Come descritto in [Introduzione](../../../authoring-cards/getting-started.md) pagina, una scheda adattiva è un modello a oggetti della scheda serializzato JSON. Questa libreria semplifica il rendering di tale JSON nell'interfaccia utente WPF che è possibile usare all'interno dell'app.

## <a name="nuget-install"></a>Installazione di NuGet

[![Installazione di NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)

```console
Install-Package AdaptiveCards.Rendering.Wpf
```

### <a name="xceed-enhanced-input-package"></a>Pacchetto di input migliorato Xceed

Questo pacchetto facoltativo consente di migliorare i controlli di input della scheda adattivo oltre a quelli forniti da WPF. Ha una dipendenza da`Extended.Wpf.Toolkit`

[![Installazione di NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)

```console
Install-Package AdaptiveCards.Rendering.Wpf.Xceed
```

## <a name="wpf-visualizer-sample"></a>Esempio di visualizzatore WPF

![Screenshot del Visualizzatore](../../../resources/media/tools/wpfvisualizer.png)

L' [esempio visualizzatore WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) consente di visualizzare le schede utilizzando WPF.  Un `Host Config` Editor è integrato per la modifica e la visualizzazione delle impostazioni di configurazione host. Salvare queste impostazioni come JSON per usarle nel rendering nell'applicazione.

## <a name="next-steps"></a>Passaggi successivi

Per i passaggi successivi, vedi [Eseguire il rendering di una scheda](render-a-card.md).
