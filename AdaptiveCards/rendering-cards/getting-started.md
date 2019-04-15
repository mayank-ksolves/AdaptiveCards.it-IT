---
title: Il rendering di schede all'interno dell'applicazione
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 0a9507c56a8bae9f038c220cdf55e34b2c3b0829
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552923"
---
# <a name="rendering-cards-inside-your-application"></a>Il rendering di schede all'interno dell'applicazione

È facile eseguire il rendering le schede adattive all'interno dell'applicazione. Sono forniti SDK per le piattaforme comuni tutti, nonché fornire una [dettagliate specifica](implement-a-renderer.md) per creare il proprio renderer scheda adattiva.

1. **Installare un renderer SDK** - per la piattaforma di destinazione.
2. **Creare un'istanza del renderer** - configurata con gestori di eventi di stile, le regole e azioni dell'app.
3. **Eseguire il rendering di una scheda di interfaccia utente nativa** - automaticamente con stile all'app.

## <a name="adaptive-cards-sdks"></a>Le schede adattive SDK

|Piattaforma|Installazione|Build|Documentazione|Stato|
|---|---|---|---|---|
| JavaScript | [![installazione di npm](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/nodejs)| [Docs](../sdk/rendering-cards/javascript/getting-started.md) | ![Lo stato della compilazione](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20564.svg) |
| .NET WPF | [![Installazione di NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet)| [Docs](../sdk/rendering-cards/net-wpf/getting-started.md) | ![Lo stato della compilazione](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| .NET HTML | [![Installazione di NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Html.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Html) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet) | [Docs](../sdk/rendering-cards/net-html/getting-started.md) | ![Lo stato della compilazione](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| Windows UWP | [![Installazione di NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Uwp.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Uwp) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/uwp) | [Docs](../sdk/rendering-cards/uwp/getting-started.md) | ![Lo stato della compilazione](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20583.svg) |
| Android | [![Centrale di Maven](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/android) | [Docs](../sdk/rendering-cards/android/getting-started.md) | ![Lo stato della compilazione](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/17651.svg)
| iOS | [![CocoaPods](https://img.shields.io/cocoapods/v/AdaptiveCards.svg)](https://cocoapods.org/pods/AdaptiveCards) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/ios) | [Docs](../sdk/rendering-cards/ios/getting-started.md) |  ![Lo stato della compilazione](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/16990.svg) |

## <a name="create-an-instance-of-the-renderer"></a>Creare un'istanza del renderer

Il passaggio successivo consiste nel creare un'istanza di un `AdaptiveCardRenderer`. 

### <a name="hook-up-action-events"></a>Associare gli eventi di azione

Per impostazione predefinita, le azioni verranno sottoposti a rendering come pulsanti della scheda, ma spetta all'App in modo che siano comportarsi come previsto. Ogni SDK include l'equivalente di un `OnAction` eventi che è necessario gestire.

* **Action.OpenUrl** -aprire l'oggetto specificato `url`.  
* **Action.Submit** : accettare il risultato dell'invio e inviarlo all'origine. Come si invia all'origine della scheda è completamente responsabilità dell'utente.
* **Action.ShowCard** : richiama una finestra di dialogo e viene eseguito il rendering scheda secondario in tale finestra di dialogo. Si noti che è solo necessario gestire questa operazione se `ShowCardActionMode` è impostata su `popup`.

## <a name="render-a-card"></a>Eseguire il rendering di una scheda

Dopo che si acquisisce un payload di smart card, è sufficiente chiamare il renderer e passare nella scheda. Sarà possibile ottenere un oggetto nativo di interfaccia utente costituito dal contenuto della scheda. A questo punto sufficiente inserire questa interfaccia utente in un punto qualsiasi nell'app.

## <a name="customization"></a>Personalizzazione

Esistono diversi modi, che è possibile personalizzare ciò che viene eseguito il rendering. 

### <a name="hostconfig"></a>HostConfig

Oggetto [HostConfig](host-config.md) è un oggetto di configurazione condivisa, lo sviluppo multipiattaforma che consente di controllare il comportamento di schede all'interno dell'app e lo stile di base. Definisce elementi quali le dimensioni dei caratteri, la spaziatura tra gli elementi, i colori, il numero di azioni supportate e così via. 

### <a name="native-platform-styling"></a>Stile di piattaforma nativa

La maggior parte dei framework dell'interfaccia utente consentono di definire lo stile scheda sottoposto a rendering utilizzando lo stile di framework dell'interfaccia utente nativo. Ad esempio, in formato HTML è possibile specificare le classi CSS per HTML, o in XAML è possibile passare un oggetto ResourceDictionary personalizzato per il controllo con granularità fine dell'output.

### <a name="customize-per-element-rendering"></a>Personalizzare il rendering per ogni elemento

Ogni SDK consente l'override del rendering di qualsiasi elemento, o persino aggiungere supporto per gli elementi completamente nuovi che definiscono.  Ad esempio, è possibile modificare il `Input.Date` renderer per creare un controllo personalizzato, pur mantenendo il resto dell'output del renderer. Oppure è possibile aggiungere il supporto per un oggetto personalizzato `Rating` definire elemento all'utente.



