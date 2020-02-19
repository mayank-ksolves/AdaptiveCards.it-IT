---
title: SDK WPF .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 999f8ac3cd6a18fbbfc8b8bbdcf47465d8bb314f
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454284"
---
# <a name="getting-started---net-wpf"></a>Introduzione-WPF .NET

Come descritto in [Introduzione](../../../authoring-cards/getting-started.md) pagina, una scheda adattiva è un modello a oggetti della scheda serializzato JSON. Questa libreria semplifica il rendering di tale JSON nell'interfaccia utente WPF che è possibile usare all'interno dell'app.

## <a name="nuget-install"></a>Installazione di NuGet

[![Installazione di Nuget](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)

```console
Install-Package AdaptiveCards.Rendering.Wpf
```

### <a name="xceed-enhanced-input-package"></a>Pacchetto di input migliorato Xceed

Questo pacchetto facoltativo consente di migliorare i controlli di input della scheda adattivo oltre a quelli forniti da WPF. Ha una dipendenza da `Extended.Wpf.Toolkit`

[![Installazione di Nuget](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)

```console
Install-Package AdaptiveCards.Rendering.Wpf.Xceed
```

## <a name="wpf-visualizer-sample"></a>Esempio di visualizzatore WPF

![Screenshot del Visualizzatore](../../../resources/media/tools/wpfvisualizer.png)

L' [esempio visualizzatore WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) consente di visualizzare le schede utilizzando WPF.  Un editor `Host Config` è integrato per la modifica e la visualizzazione delle impostazioni di configurazione host. Salva tali impostazioni come JSON per usarle nel rendering all'interno dell'applicazione.

## <a name="next-steps"></a>Passaggi successivi

Per i passaggi successivi, vedi [Eseguire il rendering di una scheda](render-a-card.md).
