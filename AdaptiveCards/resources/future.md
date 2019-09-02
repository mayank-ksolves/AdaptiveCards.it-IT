---
title: Roadmap delle schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 05/16/2018
ms.topic: article
ms.openlocfilehash: f879c164b3471347ba8fa058827b3d79b09be4cd
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2019
ms.locfileid: "67138004"
---
# <a name="future-work"></a><span data-ttu-id="fecb2-102">Lavoro futuro</span><span class="sxs-lookup"><span data-stu-id="fecb2-102">Future work</span></span>

<span data-ttu-id="fecb2-103">Anche se è stato realizzato un ottimo lavoro nella definizione delle schede adattive, c'è ancora molto da fare.</span><span class="sxs-lookup"><span data-stu-id="fecb2-103">While we have made excellent progress defining adaptive cards, there is still lots of work to do.</span></span> <span data-ttu-id="fecb2-104">La speranza è che attraverso community attive di sviluppatori come Botness e partner eccezionali come Slack e Kik, sarà possibile creare un grande ecosistema di schede multipiattaforma.</span><span class="sxs-lookup"><span data-stu-id="fecb2-104">Our hope is that through active developer communities like botness, and great partners like Slack and Kik, we can create a great ecosystem of cross-platform cards.</span></span>

## <a name="roadmap"></a><span data-ttu-id="fecb2-105">Roadmap</span><span class="sxs-lookup"><span data-stu-id="fecb2-105">Roadmap</span></span>

<span data-ttu-id="fecb2-106">Puoi vedere [qui il roadmap corrente (non finale)](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span><span class="sxs-lookup"><span data-stu-id="fecb2-106">You can see our [current (non-final) roadmap here](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span></span> <span data-ttu-id="fecb2-107">Considera che è tutto soggetto a modifiche e che non è una garanzia di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="fecb2-107">Note that anything on here is subject to change, and is not a guarantee of shipping.</span></span>

## <a name="future-ideas"></a><span data-ttu-id="fecb2-108">Idee future</span><span class="sxs-lookup"><span data-stu-id="fecb2-108">Future ideas</span></span>

<span data-ttu-id="fecb2-109">Di seguito sono riportate alcune idee future che sono ancora in fase di brainstorming.</span><span class="sxs-lookup"><span data-stu-id="fecb2-109">The following are some future ideas we have, which are simply in the brainstorm stage.</span></span> <span data-ttu-id="fecb2-110">Se sei interessato a una di queste idee, invia un commento.</span><span class="sxs-lookup"><span data-stu-id="fecb2-110">If you're interested in any of these, let us know in a comment.</span></span>

### <a name="great-looking-cards-from-data"></a><span data-ttu-id="fecb2-111">Schede di aspetto perfetto a partire dai dati</span><span class="sxs-lookup"><span data-stu-id="fecb2-111">Great looking Cards from Data</span></span>

<span data-ttu-id="fecb2-112">È noto come molti autori di schede dispongano già di dati ben definiti alla base delle loro schede.</span><span class="sxs-lookup"><span data-stu-id="fecb2-112">We know many card authors already have well-defined data behind their cards.</span></span> <span data-ttu-id="fecb2-113">L'obiettivo è di esplorare un modello che consenta di generare schede (lato server o client) in base ai dati e a un repository di modelli ben definiti e personalizzabili.</span><span class="sxs-lookup"><span data-stu-id="fecb2-113">Our plan is to explore a templating model that would allow cards to be generated (server side or client side) based on the data and a repository of well-defined and customizable templates.</span></span>

### <a name="make-cards-responsive"></a><span data-ttu-id="fecb2-114">Creare schede reattive</span><span class="sxs-lookup"><span data-stu-id="fecb2-114">Make cards responsive</span></span>

<span data-ttu-id="fecb2-115">I layout delle schede devono essere reattivi in base allo spazio disponibile.</span><span class="sxs-lookup"><span data-stu-id="fecb2-115">Card layouts should be reactive to available space.</span></span> <span data-ttu-id="fecb2-116">Le schede adattive sono adattabili a dispositivi, stili di esperienza utente e framework di interfaccia utente diversi, ma non sono ancora reattive.</span><span class="sxs-lookup"><span data-stu-id="fecb2-116">Adaptive cards are adaptable to different devices, ux styles and and ui frameworks, but they are not reactive yet.</span></span> <span data-ttu-id="fecb2-117">Per gli elementi devono essere definite proprietà aggiuntive che consentano ai produttori di schede di fornire i suggerimenti necessari alle librerie di rendering, affinché possano modificare il layout in modo intelligente e mantenere lo scopo della scheda.</span><span class="sxs-lookup"><span data-stu-id="fecb2-117">Additional properties must be defined on elements which allow card producers to provide the necessary hints to the rendering libraries so that they can intelligently change the layout in a way which maintains the intent of the card.</span></span>

### <a name="responsive-exploration"></a><span data-ttu-id="fecb2-118">Esplorazione reattiva</span><span class="sxs-lookup"><span data-stu-id="fecb2-118">Responsive exploration</span></span>

* <span data-ttu-id="fecb2-119">Aggiungi una proprietà di **importanza** per annotare l'importanza del contenuto.</span><span class="sxs-lookup"><span data-stu-id="fecb2-119">Add an **importance** property which annotates importance of content.</span></span> <span data-ttu-id="fecb2-120">In questo modo il contenuto meno importante può essere rimosso per l'adattamento allo spazio disponibile.</span><span class="sxs-lookup"><span data-stu-id="fecb2-120">Less important content can be dropped to fit available space</span></span>
* <span data-ttu-id="fecb2-121">Aggiungi proprietà di **vincoli** e **criteri** per descrivere come reagire se i vincoli non vengono soddisfatti.</span><span class="sxs-lookup"><span data-stu-id="fecb2-121">Add **constraints** and **policy** properties describing how to react when constraints can't be met.</span></span> 
  * <span data-ttu-id="fecb2-122">Nascondi contenuto o comprimilo riducendo le dimensioni.</span><span class="sxs-lookup"><span data-stu-id="fecb2-122">Hide content or collapse content to smaller size.</span></span>
  * <span data-ttu-id="fecb2-123">Aggiungi una soglia che, se superata, trasforma `columnSet` in colonne carousel.</span><span class="sxs-lookup"><span data-stu-id="fecb2-123">Add a threshold that, when exceeded, changes `columnSet` to carousel of columns.</span></span>

### <a name="new-element-types"></a><span data-ttu-id="fecb2-124">Nuovi tipi di elementi</span><span class="sxs-lookup"><span data-stu-id="fecb2-124">New element types</span></span>

* <span data-ttu-id="fecb2-125">Mappe?</span><span class="sxs-lookup"><span data-stu-id="fecb2-125">Maps?</span></span> <span data-ttu-id="fecb2-126">Incorpora una mappa in una scheda con interattività o fallback in bitmap</span><span class="sxs-lookup"><span data-stu-id="fecb2-126">- embed a map into a card with interactivity or fallback to bitmap</span></span>
* <span data-ttu-id="fecb2-127">*Quali sono gli elementi che vuoi o che sono necessari*?</span><span class="sxs-lookup"><span data-stu-id="fecb2-127">*What elements do you want or need*?</span></span>

### <a name="new-rendering-libraries"></a><span data-ttu-id="fecb2-128">Nuove librerie di rendering</span><span class="sxs-lookup"><span data-stu-id="fecb2-128">New rendering libraries</span></span>

* <span data-ttu-id="fecb2-129">React?</span><span class="sxs-lookup"><span data-stu-id="fecb2-129">React?</span></span>
* <span data-ttu-id="fecb2-130">Xamarin?</span><span class="sxs-lookup"><span data-stu-id="fecb2-130">Xamarin?</span></span>
* <span data-ttu-id="fecb2-131">*Quali framework vuoi?*</span><span class="sxs-lookup"><span data-stu-id="fecb2-131">*What frameworks do you want?*</span></span>
