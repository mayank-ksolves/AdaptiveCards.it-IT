---
title: Schede adattive per gli sviluppatori Windows
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 20b324c12cd7cec10f2142fc2cf76039b5c329de
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2019
ms.locfileid: "59552853"
---
# <a name="adaptive-cards-for-windows-developers"></a><span data-ttu-id="f67ce-102">Schede adattive per gli sviluppatori Windows</span><span class="sxs-lookup"><span data-stu-id="f67ce-102">Adaptive Cards for Windows Developers</span></span>



## <a name="timeline"></a><span data-ttu-id="f67ce-103">Sequenza temporale</span><span class="sxs-lookup"><span data-stu-id="f67ce-103">Timeline</span></span>

<span data-ttu-id="f67ce-104">La prima esperienza Windows a supportare le schede adattive è la sequenza temporale, un'esperienza completamente nuova introdotta in Windows 10 1803.</span><span class="sxs-lookup"><span data-stu-id="f67ce-104">The first Windows experience to supports Adaptive Cards is Timeline, a brand new experience first introduced in Windows 10 1803.</span></span> 

![Sequenza temporale](media/windows/timeline.png)

### <a name="useractivity-api"></a><span data-ttu-id="f67ce-106">API UserActivity</span><span class="sxs-lookup"><span data-stu-id="f67ce-106">UserActivity API</span></span>

<span data-ttu-id="f67ce-107">L'API [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) è ciò che inserisce un'attività nella sequenza temporale.</span><span class="sxs-lookup"><span data-stu-id="f67ce-107">The [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API is what populates an Activity into Timeline.</span></span>

<span data-ttu-id="f67ce-108">La scheda adattiva verrà fornita tramite la proprietà `Content` di `VisualElement`, come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f67ce-108">The Adaptive Card will be supplied via the `Content` property of `VisualElement`, as seen below:</span></span>

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learn-more"></a><span data-ttu-id="f67ce-109">Scopri di più</span><span class="sxs-lookup"><span data-stu-id="f67ce-109">Learn more</span></span>

<span data-ttu-id="f67ce-110">Questa sessione della conferenza Build 2017 illustra in dettaglio le attività utente.</span><span class="sxs-lookup"><span data-stu-id="f67ce-110">This session at Build 2017 covers User Activities in detial.</span></span>

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a><span data-ttu-id="f67ce-111">Altre esperienze Windows</span><span class="sxs-lookup"><span data-stu-id="f67ce-111">Other Windows Surfaces</span></span>
<span data-ttu-id="f67ce-112">Anche se non è ancora possibile condividere informazioni, stiamo lavorando per incorporare le schede adattive in altre esperienze Windows.</span><span class="sxs-lookup"><span data-stu-id="f67ce-112">We don't have anything to share just yet, but we're working on incorporating Adaptive Cards into more Windows experiences.</span></span>

## <a name="dive-in"></a><span data-ttu-id="f67ce-113">Approfondimento</span><span class="sxs-lookup"><span data-stu-id="f67ce-113">Dive in!</span></span>

<span data-ttu-id="f67ce-114">In questa esercitazione è stata fornita solo una presentazione generale. Ricontrolla questa pagina e visita i collegamenti seguenti per altre informazioni sulle schede adattive.</span><span class="sxs-lookup"><span data-stu-id="f67ce-114">We've barely scratched the surface in this tutorial, so check back soon and browse the links below to explore more about Adaptive Cards.</span></span>

* <span data-ttu-id="f67ce-115">[Esamina le schede di esempio](http://adaptivecards.io/samples/) per trovare l'ispirazione</span><span class="sxs-lookup"><span data-stu-id="f67ce-115">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="f67ce-116">Usa [Schema Explorer](http://adaptivecards.io/explorer) per informazioni sugli elementi disponibili</span><span class="sxs-lookup"><span data-stu-id="f67ce-116">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="f67ce-117">Crea una scheda usando il [visualizzatore interattivo](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span><span class="sxs-lookup"><span data-stu-id="f67ce-117">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="f67ce-118">[Contattaci](http://adaptivecards.io/connect) per eventuali commenti</span><span class="sxs-lookup"><span data-stu-id="f67ce-118">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
