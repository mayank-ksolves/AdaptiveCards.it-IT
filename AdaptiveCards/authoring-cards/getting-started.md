---
title: Attività iniziali
author: matthidinger
ms.author: mahiding
ms.date: 11/9/2017
ms.topic: article
ms.openlocfilehash: 9d363da0c10b242e23d2594984292fcc1f31382f
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552683"
---
# <a name="getting-started"></a><span data-ttu-id="273fa-102">Attività iniziali</span><span class="sxs-lookup"><span data-stu-id="273fa-102">Getting Started</span></span> 

<span data-ttu-id="273fa-103">Una scheda adattiva è un modello a oggetti serializzati con JSON smart card.</span><span class="sxs-lookup"><span data-stu-id="273fa-103">An Adaptive Card is a JSON-serialized card object model.</span></span>

## <a name="adaptive-card-structure"></a><span data-ttu-id="273fa-104">Struttura della scheda adattiva</span><span class="sxs-lookup"><span data-stu-id="273fa-104">Adaptive Card structure</span></span>

<span data-ttu-id="273fa-105">La struttura di base di una scheda è come segue:</span><span class="sxs-lookup"><span data-stu-id="273fa-105">The basic structure of a card is as follows:</span></span>

* <span data-ttu-id="273fa-106">`AdaptiveCard` -L'oggetto radice descrive AdaptiveCard, tra cui la composizione di elemento, le azioni, come devono essere pronunciato e la versione dello schema necessario per eseguirne il rendering.</span><span class="sxs-lookup"><span data-stu-id="273fa-106">`AdaptiveCard` - The root object describes the AdaptiveCard itself, including its element makeup, its actions, how it should be spoken, and the schema version required to render it.</span></span>
* <span data-ttu-id="273fa-107">`body` -Il corpo della scheda è costituito da blocchi predefiniti noto come `elements`.</span><span class="sxs-lookup"><span data-stu-id="273fa-107">`body` - The body of the card is made up of building-blocks known as `elements`.</span></span> <span data-ttu-id="273fa-108">Gli elementi possono essere composte negli accordi quasi infinite per creare molti tipi di schede.</span><span class="sxs-lookup"><span data-stu-id="273fa-108">Elements can be composed in nearly infinite arrangements to create many types of cards.</span></span> 
* <span data-ttu-id="273fa-109">`actions` -Molte schede includono un set di azioni che un utente può eseguire su di esso.</span><span class="sxs-lookup"><span data-stu-id="273fa-109">`actions` - Many cards have a set of actions a user may take on it.</span></span> <span data-ttu-id="273fa-110">Questa proprietà descrive le azioni che in genere sottoposti a rendering in una barra"azione" nella parte inferiore.</span><span class="sxs-lookup"><span data-stu-id="273fa-110">This property describes those actions which typically get rendered in an "action bar" at the bottom.</span></span>

### <a name="example-card"></a><span data-ttu-id="273fa-111">Scheda di esempio</span><span class="sxs-lookup"><span data-stu-id="273fa-111">Example Card</span></span>

<span data-ttu-id="273fa-112">Questa scheda di esempio che include una singola riga di testo seguita da un'immagine.</span><span class="sxs-lookup"><span data-stu-id="273fa-112">This sample card which includes a single line of text followed by an image.</span></span>

```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Here is a ninja cat"
        },
        {
            "type": "Image",
            "url": "http://adaptivecards.io/content/cats/1.png"
        }
    ]
}
```

## <a name="type-property"></a><span data-ttu-id="273fa-113">Proprietà `Type`</span><span class="sxs-lookup"><span data-stu-id="273fa-113">`Type` property</span></span>

<span data-ttu-id="273fa-114">Ogni elemento ha un `type` è la proprietà che identifica quale tipo di oggetto.</span><span class="sxs-lookup"><span data-stu-id="273fa-114">Every element has a `type` property which identifies what kind of object it is.</span></span> <span data-ttu-id="273fa-115">Esaminando la scheda precedente, si possono individuare sono di due elementi, un `TextBlock` e un `Image`.</span><span class="sxs-lookup"><span data-stu-id="273fa-115">Looking at the above card, you can see we have two elements, a `TextBlock` and an `Image`.</span></span>

<span data-ttu-id="273fa-116">Tutti gli elementi di scheda adattiva **raggruppati verticalmente** e **espandere la larghezza del relativo elemento padre** (pensare `display: block` in formato HTML).</span><span class="sxs-lookup"><span data-stu-id="273fa-116">All Adaptive Card elements **stack vertically** and **expand to the width of their parent** (think `display: block` in HTML).</span></span> <span data-ttu-id="273fa-117">Tuttavia, è possibile usare un `ColumnSet` creare colonne side-by-side di contenitori.</span><span class="sxs-lookup"><span data-stu-id="273fa-117">However, you can use a `ColumnSet` to create side-by-side columns of containers.</span></span>

## <a name="adaptive-elements"></a><span data-ttu-id="273fa-118">Elementi adattivi</span><span class="sxs-lookup"><span data-stu-id="273fa-118">Adaptive Elements</span></span>

<span data-ttu-id="273fa-119">Gli elementi più importanti sono:</span><span class="sxs-lookup"><span data-stu-id="273fa-119">The most fundamental elements are:</span></span>

* <span data-ttu-id="273fa-120">**TextBlock** -aggiunge un blocco di testo con le proprietà per controllare l'aspetto del testo</span><span class="sxs-lookup"><span data-stu-id="273fa-120">**TextBlock** - adds a block of text with properties to control what the text looks like</span></span>
* <span data-ttu-id="273fa-121">**Immagine** -aggiunge un'immagine con le proprietà per controllare l'aspetto dell'immagine</span><span class="sxs-lookup"><span data-stu-id="273fa-121">**Image** - adds an image with properties to control what the image looks like</span></span>

## <a name="container-elements"></a><span data-ttu-id="273fa-122">Elementi contenitore</span><span class="sxs-lookup"><span data-stu-id="273fa-122">Container elements</span></span>

<span data-ttu-id="273fa-123">Le schede possono avere anche i contenitori, disporre di una raccolta di elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="273fa-123">Cards can also have containers, which arrange a collection of child elements.</span></span>

* <span data-ttu-id="273fa-124">**Contenitore** -definisce una raccolta di elementi</span><span class="sxs-lookup"><span data-stu-id="273fa-124">**Container** - Defines a a collection of elements</span></span>
* <span data-ttu-id="273fa-125">**/ Colonna ColumnSet** -definisce una raccolta di colonne, ogni colonna è un contenitore</span><span class="sxs-lookup"><span data-stu-id="273fa-125">**ColumnSet/Column** - Defines a collection of columns, each column is a container</span></span>
* <span data-ttu-id="273fa-126">**FactSet** -contenitore di fact</span><span class="sxs-lookup"><span data-stu-id="273fa-126">**FactSet** - Container of Facts</span></span>
* <span data-ttu-id="273fa-127">**ImageSet** -esperienza di raccolta per una raccolta di immagini di foto di immagini del contenitore in modo da tale interfaccia utente può visualizzare appropriato.</span><span class="sxs-lookup"><span data-stu-id="273fa-127">**ImageSet** - Container of Images so that UI can show appropriate photo gallery experience for a collection of images.</span></span>

## <a name="input-elements"></a><span data-ttu-id="273fa-128">Elementi di input</span><span class="sxs-lookup"><span data-stu-id="273fa-128">Input elements</span></span>

<span data-ttu-id="273fa-129">Gli elementi di input consentono di porre per interfaccia utente nativa compilare moduli semplici:</span><span class="sxs-lookup"><span data-stu-id="273fa-129">Input elements allow you to ask for native UI to build simple forms:</span></span>

* <span data-ttu-id="273fa-130">**Input.Text** -ottenere contenuto di testo dall'utente</span><span class="sxs-lookup"><span data-stu-id="273fa-130">**Input.Text** - get text content from the user</span></span>
* <span data-ttu-id="273fa-131">**Input.Date** -ottenere una data dall'utente</span><span class="sxs-lookup"><span data-stu-id="273fa-131">**Input.Date** - get a Date from the user</span></span>
* <span data-ttu-id="273fa-132">**Input.Time** -ottenere una volta dall'utente</span><span class="sxs-lookup"><span data-stu-id="273fa-132">**Input.Time** - get a Time from the user</span></span>
* <span data-ttu-id="273fa-133">**Input.Number** -ottenere un numero da parte dell'utente</span><span class="sxs-lookup"><span data-stu-id="273fa-133">**Input.Number** - get a Number from the user</span></span>
* <span data-ttu-id="273fa-134">**Input.ChoiceSet** : concedere all'utente un set di scelte e che siano selezionate</span><span class="sxs-lookup"><span data-stu-id="273fa-134">**Input.ChoiceSet** - Give the user a set of choices and have them pick</span></span>
* <span data-ttu-id="273fa-135">**Input.Toggle** : concedere all'utente una scelta singola tra due elementi e che siano selezionate</span><span class="sxs-lookup"><span data-stu-id="273fa-135">**Input.Toggle** - Give the user a single choice between two items and have them pick</span></span>

## <a name="actions"></a><span data-ttu-id="273fa-136">Azioni</span><span class="sxs-lookup"><span data-stu-id="273fa-136">Actions</span></span>

<span data-ttu-id="273fa-137">Azioni aggiungere pulsanti alla scheda.</span><span class="sxs-lookup"><span data-stu-id="273fa-137">Actions add buttons to the card.</span></span> <span data-ttu-id="273fa-138">Si può eseguire una serie di azioni, ad esempio l'apertura di un URL o l'invio di alcuni dati.</span><span class="sxs-lookup"><span data-stu-id="273fa-138">These can perform a variety of actions, like opening a URL or submitting some data.</span></span>

* <span data-ttu-id="273fa-139">**Action.OpenUrl** -pulsante consente di aprire un URL esterno per la visualizzazione</span><span class="sxs-lookup"><span data-stu-id="273fa-139">**Action.OpenUrl** - the button opens an external URL for viewing</span></span>
* <span data-ttu-id="273fa-140">**Action.ShowCard** -richiede una carta secondari da visualizzare all'utente.</span><span class="sxs-lookup"><span data-stu-id="273fa-140">**Action.ShowCard** - Requests a sub-card to be shown to the user.</span></span>
* <span data-ttu-id="273fa-141">**Action.Submit** -porre per tutti gli elementi di input di raccogliere in un oggetto che viene quindi inviato all'utente tramite un metodo definito dall'applicazione host.</span><span class="sxs-lookup"><span data-stu-id="273fa-141">**Action.Submit** - Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

> <span data-ttu-id="273fa-142">**Esempio Action.Submit**: Con Skype, un Action.Submit invierà un bot di Bot Framework attività al bot con i **valore** proprietà che contiene un oggetto con tutti i dati di input su di esso.</span><span class="sxs-lookup"><span data-stu-id="273fa-142">**Example Action.Submit**: With Skype, an Action.Submit will send a Bot Framework bot activity back to the bot with the **Value** property containing an object with all of the input data on it.</span></span>

## <a name="learn-more"></a><span data-ttu-id="273fa-143">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="273fa-143">Learn More</span></span>

* <span data-ttu-id="273fa-144">[Individuare le schede di esempio](http://adaptivecards.io/samples/) per trovare l'ispirazione</span><span class="sxs-lookup"><span data-stu-id="273fa-144">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="273fa-145">Usare la [Schema Explorer](http://adaptivecards.io/explorer) per esplorare gli elementi disponibili</span><span class="sxs-lookup"><span data-stu-id="273fa-145">Use the [Schema Explorer](http://adaptivecards.io/explorer) to browse the available elements</span></span>
* <span data-ttu-id="273fa-146">Creare una scheda usando il [Visualizzatore interattivo](http://adaptivecards.io/visualizer/)</span><span class="sxs-lookup"><span data-stu-id="273fa-146">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/)</span></span>
* <span data-ttu-id="273fa-147">[Contattare il supporto](http://adaptivecards.io/connect) con eventuali commenti</span><span class="sxs-lookup"><span data-stu-id="273fa-147">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
