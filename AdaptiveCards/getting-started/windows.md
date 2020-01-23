---
title: Schede adattive per gli sviluppatori Windows
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 39bdc64ed3244aca68d36c886a9562d964ded217
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145391"
---
# <a name="adaptive-cards-for-windows-developers"></a>Schede adattive per gli sviluppatori Windows

## <a name="timeline"></a>Sequenza temporale

La prima esperienza Windows a supportare le schede adattive è la sequenza temporale, un'esperienza completamente nuova introdotta in Windows 10 1803. 

![Sequenza temporale](media/windows/timeline.png)

### <a name="useractivity-api"></a>API UserActivity

L'API [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity) è ciò che inserisce un'attività nella sequenza temporale.

La scheda adattiva verrà fornita tramite la proprietà `Content` di `VisualElement`, come illustrato di seguito:

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learning-module"></a>Modulo di apprendimento

È disponibile un modulo di apprendimento dalla durata di 45 minuti che illustra tutti i passaggi.

[Integrare le schede adattive nella sequenza temporale di Windows 10](https://docs.microsoft.com/learn/modules/integrate-app-into-windows-10-timeline/)

### <a name="learn-more"></a>Altre informazioni

Questa sessione della conferenza Build 2017 illustra in dettaglio le attività utente.

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a>Altre esperienze Windows
Anche se non è ancora possibile condividere informazioni, stiamo lavorando per incorporare le schede adattive in altre esperienze Windows.

## <a name="dive-in"></a>Approfondimento

In questa esercitazione è stata fornita solo una presentazione generale. Ricontrolla questa pagina e visita i collegamenti seguenti per altre informazioni sulle schede adattive.

* [Esamina le schede di esempio](http://adaptivecards.io/samples/) per trovare l'ispirazione
* Usa [Schema Explorer](http://adaptivecards.io/explorer) per informazioni sugli elementi disponibili
* Crea una scheda usando il [visualizzatore interattivo](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)
* [Contattaci](http://adaptivecards.io/connect) per eventuali commenti
