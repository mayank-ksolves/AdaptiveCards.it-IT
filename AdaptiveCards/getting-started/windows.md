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
# <a name="adaptive-cards-for-windows-developers"></a><span data-ttu-id="a17ca-102">Schede adattive per gli sviluppatori Windows</span><span class="sxs-lookup"><span data-stu-id="a17ca-102">Adaptive Cards for Windows Developers</span></span>



## <a name="timeline"></a><span data-ttu-id="a17ca-103">Sequenza temporale</span><span class="sxs-lookup"><span data-stu-id="a17ca-103">Timeline</span></span>

<span data-ttu-id="a17ca-104">Il primo Windows esperienza a supporta che le schede adattive è un'esperienza tutta nuova introdotta in Windows 10 1803 sequenza temporale.</span><span class="sxs-lookup"><span data-stu-id="a17ca-104">The first Windows experience to supports Adaptive Cards is Timeline, a brand new experience first introduced in Windows 10 1803.</span></span> 

![Sequenza temporale](media/windows/timeline.png)

### <a name="useractivity-api"></a><span data-ttu-id="a17ca-106">UserActivity API</span><span class="sxs-lookup"><span data-stu-id="a17ca-106">UserActivity API</span></span>

<span data-ttu-id="a17ca-107">Il [ `Windows.ApplicationModel.UserActivities.UserActivity` ](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API è ciò che popola un'attività nella sequenza temporale.</span><span class="sxs-lookup"><span data-stu-id="a17ca-107">The [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API is what populates an Activity into Timeline.</span></span>

<span data-ttu-id="a17ca-108">La scheda adattiva verrà fornita tramite il `Content` proprietà di `VisualElement`, come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="a17ca-108">The Adaptive Card will be supplied via the `Content` property of `VisualElement`, as seen below:</span></span>

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learn-more"></a><span data-ttu-id="a17ca-109">Scopri di più</span><span class="sxs-lookup"><span data-stu-id="a17ca-109">Learn more</span></span>

<span data-ttu-id="a17ca-110">Questa sessione conferenza Build 2017 illustra le attività degli utenti in detial.</span><span class="sxs-lookup"><span data-stu-id="a17ca-110">This session at Build 2017 covers User Activities in detial.</span></span>

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a><span data-ttu-id="a17ca-111">Altre superfici di Windows</span><span class="sxs-lookup"><span data-stu-id="a17ca-111">Other Windows Surfaces</span></span>
<span data-ttu-id="a17ca-112">Non è niente da condividere ancora, ma ci stiamo impegnando per incorporare le schede adattive altre esperienze di Windows.</span><span class="sxs-lookup"><span data-stu-id="a17ca-112">We don't have anything to share just yet, but we're working on incorporating Adaptive Cards into more Windows experiences.</span></span>

## <a name="dive-in"></a><span data-ttu-id="a17ca-113">Approfondimento!</span><span class="sxs-lookup"><span data-stu-id="a17ca-113">Dive in!</span></span>

<span data-ttu-id="a17ca-114">È stata solo annunciati in questa esercitazione, quindi controllare più tardi e passare i collegamenti seguenti per altre informazioni sulle schede adattive.</span><span class="sxs-lookup"><span data-stu-id="a17ca-114">We've barely scratched the surface in this tutorial, so check back soon and browse the links below to explore more about Adaptive Cards.</span></span>

* <span data-ttu-id="a17ca-115">[Individuare le schede di esempio](http://adaptivecards.io/samples/) per trovare l'ispirazione</span><span class="sxs-lookup"><span data-stu-id="a17ca-115">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="a17ca-116">Usare la [Schema Explorer](http://adaptivecards.io/explorer) apprendere gli elementi disponibili</span><span class="sxs-lookup"><span data-stu-id="a17ca-116">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="a17ca-117">Creare una scheda usando il [Visualizzatore interattivo](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span><span class="sxs-lookup"><span data-stu-id="a17ca-117">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="a17ca-118">[Contattare il supporto](http://adaptivecards.io/connect) con eventuali commenti</span><span class="sxs-lookup"><span data-stu-id="a17ca-118">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
