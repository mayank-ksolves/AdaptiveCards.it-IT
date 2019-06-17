---
title: Guida di orientamento per le schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 05/16/2018
ms.topic: article
ms.openlocfilehash: f879c164b3471347ba8fa058827b3d79b09be4cd
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2019
ms.locfileid: "67138004"
---
# <a name="future-work"></a><span data-ttu-id="5db99-102">Lavoro futuro</span><span class="sxs-lookup"><span data-stu-id="5db99-102">Future work</span></span>

<span data-ttu-id="5db99-103">Anche se sono stati apportati corso eccellente che definisce le schede adattive, è ancora presente un numero elevato di operazioni da eseguire.</span><span class="sxs-lookup"><span data-stu-id="5db99-103">While we have made excellent progress defining adaptive cards, there is still lots of work to do.</span></span> <span data-ttu-id="5db99-104">La nostra speranza è che tramite le community di sviluppatori attivi, ad esempio botness e i partner ideali come Slack e Kik, possiamo creare un grande ecosistema di schede multipiattaforma.</span><span class="sxs-lookup"><span data-stu-id="5db99-104">Our hope is that through active developer communities like botness, and great partners like Slack and Kik, we can create a great ecosystem of cross-platform cards.</span></span>

## <a name="roadmap"></a><span data-ttu-id="5db99-105">Guida di orientamento</span><span class="sxs-lookup"><span data-stu-id="5db99-105">Roadmap</span></span>

<span data-ttu-id="5db99-106">È possibile visualizzare nostri [corrente (non finali) Guida di orientamento qui](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span><span class="sxs-lookup"><span data-stu-id="5db99-106">You can see our [current (non-final) roadmap here](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span></span> <span data-ttu-id="5db99-107">Si noti che qualsiasi elemento in questa posizione è soggetta a modifiche e non è una garanzia di spedizione.</span><span class="sxs-lookup"><span data-stu-id="5db99-107">Note that anything on here is subject to change, and is not a guarantee of shipping.</span></span>

## <a name="future-ideas"></a><span data-ttu-id="5db99-108">Idee future</span><span class="sxs-lookup"><span data-stu-id="5db99-108">Future ideas</span></span>

<span data-ttu-id="5db99-109">Di seguito è riportate alcune idee future è disponibile, che sono semplicemente in fase di definizione.</span><span class="sxs-lookup"><span data-stu-id="5db99-109">The following are some future ideas we have, which are simply in the brainstorm stage.</span></span> <span data-ttu-id="5db99-110">Se è interessati a uno di questi, segnalarlo in un commento.</span><span class="sxs-lookup"><span data-stu-id="5db99-110">If you're interested in any of these, let us know in a comment.</span></span>

### <a name="great-looking-cards-from-data"></a><span data-ttu-id="5db99-111">Schede dall'aspetto professionale eccezionali dai dati</span><span class="sxs-lookup"><span data-stu-id="5db99-111">Great looking Cards from Data</span></span>

<span data-ttu-id="5db99-112">Sappiamo che molti autori di smart card già disponibili dati ben definiti dietro le relative schede.</span><span class="sxs-lookup"><span data-stu-id="5db99-112">We know many card authors already have well-defined data behind their cards.</span></span> <span data-ttu-id="5db99-113">È intenzione di Microsoft per esplorare un modello di creazione di modelli che consentirebbe a schede deve essere generato (sul lato server o lato client) in base i dati e un repository dei modelli ben definiti e personalizzabili.</span><span class="sxs-lookup"><span data-stu-id="5db99-113">Our plan is to explore a templating model that would allow cards to be generated (server side or client side) based on the data and a repository of well-defined and customizable templates.</span></span>

### <a name="make-cards-responsive"></a><span data-ttu-id="5db99-114">Migliorare schede di risposta</span><span class="sxs-lookup"><span data-stu-id="5db99-114">Make cards responsive</span></span>

<span data-ttu-id="5db99-115">Layout delle smart card deve essere reattive allo spazio disponibile.</span><span class="sxs-lookup"><span data-stu-id="5db99-115">Card layouts should be reactive to available space.</span></span> <span data-ttu-id="5db99-116">Le schede adattive sono adattabili ai diversi dispositivi, gli stili dell'esperienza utente ed e Framework dell'interfaccia utente, ma non sono reattivi ancora.</span><span class="sxs-lookup"><span data-stu-id="5db99-116">Adaptive cards are adaptable to different devices, ux styles and and ui frameworks, but they are not reactive yet.</span></span> <span data-ttu-id="5db99-117">È necessario definire le proprietà aggiuntive sugli elementi che consentono di producer di smart card fornire i riferimenti necessari per le librerie per il rendering in modo che cambiano in modo intelligente il layout in modo che mantiene la finalità della scheda.</span><span class="sxs-lookup"><span data-stu-id="5db99-117">Additional properties must be defined on elements which allow card producers to provide the necessary hints to the rendering libraries so that they can intelligently change the layout in a way which maintains the intent of the card.</span></span>

### <a name="responsive-exploration"></a><span data-ttu-id="5db99-118">Esplorazione reattive</span><span class="sxs-lookup"><span data-stu-id="5db99-118">Responsive exploration</span></span>

* <span data-ttu-id="5db99-119">Aggiungere un **importanza** proprietà che Annota l'importanza del contenuto.</span><span class="sxs-lookup"><span data-stu-id="5db99-119">Add an **importance** property which annotates importance of content.</span></span> <span data-ttu-id="5db99-120">Contenuto meno importante può essere eliminato in base allo spazio disponibile</span><span class="sxs-lookup"><span data-stu-id="5db99-120">Less important content can be dropped to fit available space</span></span>
* <span data-ttu-id="5db99-121">Aggiungere **vincoli** e **criterio** proprietà che descrivono come reagire quando non possono essere soddisfatti i vincoli.</span><span class="sxs-lookup"><span data-stu-id="5db99-121">Add **constraints** and **policy** properties describing how to react when constraints can't be met.</span></span> 
  * <span data-ttu-id="5db99-122">Nascondere il contenuto o comprimere il contenuto a dimensioni inferiori.</span><span class="sxs-lookup"><span data-stu-id="5db99-122">Hide content or collapse content to smaller size.</span></span>
  * <span data-ttu-id="5db99-123">Aggiunge una soglia che, quando superata, viene modificato `columnSet` alla sequenza di colonne.</span><span class="sxs-lookup"><span data-stu-id="5db99-123">Add a threshold that, when exceeded, changes `columnSet` to carousel of columns.</span></span>

### <a name="new-element-types"></a><span data-ttu-id="5db99-124">Nuovi tipi di elementi</span><span class="sxs-lookup"><span data-stu-id="5db99-124">New element types</span></span>

* <span data-ttu-id="5db99-125">Mappe?</span><span class="sxs-lookup"><span data-stu-id="5db99-125">Maps?</span></span> <span data-ttu-id="5db99-126">-incorporare una mappa in una scheda con funzionalità interattive o di fallback per la mappa di bit</span><span class="sxs-lookup"><span data-stu-id="5db99-126">- embed a map into a card with interactivity or fallback to bitmap</span></span>
* <span data-ttu-id="5db99-127">*Quali elementi è preferibile o necessario*?</span><span class="sxs-lookup"><span data-stu-id="5db99-127">*What elements do you want or need*?</span></span>

### <a name="new-rendering-libraries"></a><span data-ttu-id="5db99-128">Nuove librerie di rendering</span><span class="sxs-lookup"><span data-stu-id="5db99-128">New rendering libraries</span></span>

* <span data-ttu-id="5db99-129">React?</span><span class="sxs-lookup"><span data-stu-id="5db99-129">React?</span></span>
* <span data-ttu-id="5db99-130">Xamarin?</span><span class="sxs-lookup"><span data-stu-id="5db99-130">Xamarin?</span></span>
* <span data-ttu-id="5db99-131">*Quali Framework di eseguire?*</span><span class="sxs-lookup"><span data-stu-id="5db99-131">*What frameworks do you want?*</span></span>
