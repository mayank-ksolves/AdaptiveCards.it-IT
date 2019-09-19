---
title: Schede adattive per gli sviluppatori Windows
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 65494ed437303d26a202c9a5b95f88255147cbd0
ms.sourcegitcommit: 48838a50b5f0316e15b48d740a7dd0a5f96ebae4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/12/2019
ms.locfileid: "70923080"
---
# <a name="adaptive-cards-for-windows-developers"></a><span data-ttu-id="2d54e-102">Schede adattive per gli sviluppatori Windows</span><span class="sxs-lookup"><span data-stu-id="2d54e-102">Adaptive Cards for Windows Developers</span></span>

## <a name="timeline"></a><span data-ttu-id="2d54e-103">Sequenza temporale</span><span class="sxs-lookup"><span data-stu-id="2d54e-103">Timeline</span></span>

<span data-ttu-id="2d54e-104">La prima esperienza Windows a supportare le schede adattive è la sequenza temporale, un'esperienza completamente nuova introdotta in Windows 10 1803.</span><span class="sxs-lookup"><span data-stu-id="2d54e-104">The first Windows experience to supports Adaptive Cards is Timeline, a brand new experience first introduced in Windows 10 1803.</span></span> 

![Sequenza temporale](media/windows/timeline.png)

### <a name="useractivity-api"></a><span data-ttu-id="2d54e-106">API UserActivity</span><span class="sxs-lookup"><span data-stu-id="2d54e-106">UserActivity API</span></span>

<span data-ttu-id="2d54e-107">L'API [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) è ciò che inserisce un'attività nella sequenza temporale.</span><span class="sxs-lookup"><span data-stu-id="2d54e-107">The [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API is what populates an Activity into Timeline.</span></span>

<span data-ttu-id="2d54e-108">La scheda adattiva verrà fornita tramite la proprietà `Content` di `VisualElement`, come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="2d54e-108">The Adaptive Card will be supplied via the `Content` property of `VisualElement`, as seen below:</span></span>

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learning-module"></a><span data-ttu-id="2d54e-109">Modulo di apprendimento</span><span class="sxs-lookup"><span data-stu-id="2d54e-109">Learning Module</span></span>

<span data-ttu-id="2d54e-110">È disponibile un modulo di apprendimento dalla durata di 45 minuti che illustra tutti i passaggi.</span><span class="sxs-lookup"><span data-stu-id="2d54e-110">There is a great 45-min learn module that covers these steps end-to-end.</span></span>

[<span data-ttu-id="2d54e-111">Integrare le schede adattive nella sequenza temporale di Windows 10</span><span class="sxs-lookup"><span data-stu-id="2d54e-111">Integrate adaptive cards into Windows 10 Timeline</span></span>](https://docs.microsoft.com/en-us/learn/modules/integrate-app-into-windows-10-timeline/)

### <a name="learn-more"></a><span data-ttu-id="2d54e-112">Scopri di più</span><span class="sxs-lookup"><span data-stu-id="2d54e-112">Learn more</span></span>

<span data-ttu-id="2d54e-113">Questa sessione della conferenza Build 2017 illustra in dettaglio le attività utente.</span><span class="sxs-lookup"><span data-stu-id="2d54e-113">This session at Build 2017 covers User Activities in detial.</span></span>

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a><span data-ttu-id="2d54e-114">Altre esperienze Windows</span><span class="sxs-lookup"><span data-stu-id="2d54e-114">Other Windows Surfaces</span></span>
<span data-ttu-id="2d54e-115">Anche se non è ancora possibile condividere informazioni, stiamo lavorando per incorporare le schede adattive in altre esperienze Windows.</span><span class="sxs-lookup"><span data-stu-id="2d54e-115">We don't have anything to share just yet, but we're working on incorporating Adaptive Cards into more Windows experiences.</span></span>

## <a name="dive-in"></a><span data-ttu-id="2d54e-116">Approfondimento</span><span class="sxs-lookup"><span data-stu-id="2d54e-116">Dive in!</span></span>

<span data-ttu-id="2d54e-117">In questa esercitazione è stata fornita solo una presentazione generale. Ricontrolla questa pagina e visita i collegamenti seguenti per altre informazioni sulle schede adattive.</span><span class="sxs-lookup"><span data-stu-id="2d54e-117">We've barely scratched the surface in this tutorial, so check back soon and browse the links below to explore more about Adaptive Cards.</span></span>

* <span data-ttu-id="2d54e-118">[Esamina le schede di esempio](http://adaptivecards.io/samples/) per trovare l'ispirazione</span><span class="sxs-lookup"><span data-stu-id="2d54e-118">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="2d54e-119">Usa [Schema Explorer](http://adaptivecards.io/explorer) per informazioni sugli elementi disponibili</span><span class="sxs-lookup"><span data-stu-id="2d54e-119">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="2d54e-120">Crea una scheda usando il [visualizzatore interattivo](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span><span class="sxs-lookup"><span data-stu-id="2d54e-120">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="2d54e-121">[Contattaci](http://adaptivecards.io/connect) per eventuali commenti</span><span class="sxs-lookup"><span data-stu-id="2d54e-121">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
