---
title: Schede adattive per gli sviluppatori Windows
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 20b324c12cd7cec10f2142fc2cf76039b5c329de
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552853"
---
# <a name="adaptive-cards-for-windows-developers"></a>Schede adattive per gli sviluppatori Windows



## <a name="timeline"></a>Sequenza temporale

Il primo Windows esperienza a supporta che le schede adattive è un'esperienza tutta nuova introdotta in Windows 10 1803 sequenza temporale. 

![Sequenza temporale](media/windows/timeline.png)

### <a name="useractivity-api"></a>UserActivity API

Il [ `Windows.ApplicationModel.UserActivities.UserActivity` ](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API è ciò che popola un'attività nella sequenza temporale.

La scheda adattiva verrà fornita tramite il `Content` proprietà di `VisualElement`, come illustrato di seguito:

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learn-more"></a>Scopri di più

Questa sessione conferenza Build 2017 illustra le attività degli utenti in detial.

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a>Altre superfici di Windows
Non è niente da condividere ancora, ma ci stiamo impegnando per incorporare le schede adattive altre esperienze di Windows.

## <a name="dive-in"></a>Approfondimento!

È stata solo annunciati in questa esercitazione, quindi controllare più tardi e passare i collegamenti seguenti per altre informazioni sulle schede adattive.

* [Individuare le schede di esempio](http://adaptivecards.io/samples/) per trovare l'ispirazione
* Usare la [Schema Explorer](http://adaptivecards.io/explorer) apprendere gli elementi disponibili
* Creare una scheda usando il [Visualizzatore interattivo](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)
* [Contattare il supporto](http://adaptivecards.io/connect) con eventuali commenti
