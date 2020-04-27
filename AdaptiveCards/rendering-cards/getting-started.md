---
title: Rendering delle schede in un'applicazione
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: a562a05a91676dc5e6d8b51690acc4788802fb99
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2020
ms.locfileid: "77454934"
---
# <a name="rendering-cards-inside-your-application"></a>Rendering delle schede in un'applicazione

È facile eseguire il rendering di schede adattive in un'applicazione. Sono disponibili SDK per tutte le comuni piattaforme, nonché una [specifica dettagliata](implement-a-renderer.md) per la creazione di un renderer di schede adattive personalizzato.

1. **Installa l'SDK di un renderer** per la piattaforma di destinazione.
2. **Crea un'istanza del renderer** configurata con lo stile, le regole e i gestori eventi di azione dell'app.
3. **Esegui il rendering di una scheda nell'interfaccia utente nativa** con l'applicazione automatica dello stile all'app.

## <a name="adaptive-cards-sdks"></a>SDK di schede adattive

|Piattaforma|Installa|Creare|Docs|Stato|
|---|---|---|---|---|
| JavaScript | [![Installazione di NPM](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/nodejs)| [Docs](../sdk/rendering-cards/javascript/getting-started.md) | ![Stato della compilazione](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20564.svg) |
| WPF .NET | [![Installazione di Nuget](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet)| [Docs](../sdk/rendering-cards/net-wpf/getting-started.md) | ![Stato della compilazione](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| HTML .NET | [![Installazione di Nuget](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Html.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Html) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet) | [Docs](../sdk/rendering-cards/net-html/getting-started.md) | ![Stato della compilazione](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| Piattaforma UWP di Windows | [![Installazione di Nuget](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Uwp.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Uwp) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/uwp) | [Docs](../sdk/rendering-cards/uwp/getting-started.md) | ![Stato della compilazione](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20583.svg) |
| Android | [![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/android) | [Docs](../sdk/rendering-cards/android/getting-started.md) | ![Stato della compilazione](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/17651.svg)
| iOS | [![CocoaPods](https://img.shields.io/cocoapods/v/AdaptiveCards.svg)](https://cocoapods.org/pods/AdaptiveCards) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/ios) | [Docs](../sdk/rendering-cards/ios/getting-started.md) |  ![Stato della compilazione](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/16990.svg) |

## <a name="create-an-instance-of-the-renderer"></a>Creare un'istanza del renderer

Il passaggio successivo consiste nel creare un'istanza di un oggetto `AdaptiveCardRenderer`. 

### <a name="hook-up-action-events"></a>Associare eventi azione

Per impostazione predefinita, le azioni verranno sottoposte a rendering come pulsanti nella scheda, ma spetta all'app fare in modo che si comportino come previsto. Ogni SDK dispone dell'equivalente di un evento `OnAction` da gestire.

* **Action.OpenURL**: apre l'oggetto `url` specificato.  
* **Action.Submit**: invia all'origine il risultato dell'invio. Spetta a te scegliere come inviarlo all'origine della scheda.
* **Action.ShowCard**: richiama una finestra di dialogo ed esegue il rendering della scheda secondaria in tale finestra. Considera che devi gestire questa operazione solo se l'impostazione di `ShowCardActionMode` è `popup`.

## <a name="render-a-card"></a>Eseguire il rendering di una scheda

Dopo aver acquisito il payload di una scheda, chiama semplicemente il renderer e passa la scheda. Otterrai un oggetto dell'interfaccia utente nativa costituito dal contenuto della scheda. A questo punto, devi solo inserire questa interfaccia utente in un punto dell'app.

## <a name="customization"></a>Personalizzazione

Esistono diversi modi per personalizzare gli elementi di cui viene eseguito il rendering. 

### <a name="hostconfig"></a>HostConfig

[Hostconfig](host-config.md) è un oggetto di configurazione multipiattaforma condiviso che controlla lo stile di base e il comportamento delle schede all'interno dell'app. Definisce elementi come le dimensioni dei caratteri, la spaziatura tra elementi, i colori, il numero di azioni supportate e così via. 

### <a name="native-platform-styling"></a>Applicazione di stili della piattaforma nativa

La maggior parte dei framework dell'interfaccia utente consente di applicare uno stile alla scheda sottoposta a rendering usando lo stile del framework dell'interfaccia utente nativa. In HTML ad esempio puoi specificare le classi CSS per il codice HTML oppure in XAML puoi passare un oggetto ResourceDictionary personalizzato per un controllo granulare dell'output.

### <a name="customize-per-element-rendering"></a>Personalizzare il rendering per elemento

Ogni SDK ti consente di eseguire l'override del rendering di qualsiasi elemento o persino di aggiungere il supporto per elementi completamente nuovi che definisci.  Puoi ad esempio modificare il renderer `Input.Date` in modo da restituire un controllo personalizzato mantenendo comunque il resto dell'output del renderer. In alternativa, puoi aggiungere il supporto di un elemento personalizzato `Rating` che hai definito.



