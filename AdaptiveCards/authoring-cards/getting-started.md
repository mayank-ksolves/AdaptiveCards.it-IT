---
title: Introduzione
author: matthidinger
ms.author: mahiding
ms.date: 11/9/2017
ms.topic: article
ms.openlocfilehash: 9cc7344ac357dcb95c7e47e377dbb12fbcd66957
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417486"
---
# <a name="getting-started"></a><span data-ttu-id="cc2f3-102">Guida introduttiva</span><span class="sxs-lookup"><span data-stu-id="cc2f3-102">Getting Started</span></span> 

<span data-ttu-id="cc2f3-103">Una scheda adattiva è un modello a oggetti per le schede con serializzazione JSON.</span><span class="sxs-lookup"><span data-stu-id="cc2f3-103">An Adaptive Card is a JSON-serialized card object model.</span></span>

## <a name="adaptive-card-structure"></a><span data-ttu-id="cc2f3-104">Struttura delle schede adattive</span><span class="sxs-lookup"><span data-stu-id="cc2f3-104">Adaptive Card structure</span></span>

<span data-ttu-id="cc2f3-105">La struttura di base di una scheda è la seguente:</span><span class="sxs-lookup"><span data-stu-id="cc2f3-105">The basic structure of a card is as follows:</span></span>

* <span data-ttu-id="cc2f3-106">`AdaptiveCard` - L'oggetto radice descrive la scheda adattiva stessa, tra cui la composizione degli elementi, le azioni, le modalità di pronuncia e la versione dello schema richiesta per il rendering.</span><span class="sxs-lookup"><span data-stu-id="cc2f3-106">`AdaptiveCard` - The root object describes the AdaptiveCard itself, including its element makeup, its actions, how it should be spoken, and the schema version required to render it.</span></span>
* <span data-ttu-id="cc2f3-107">`body` - Il corpo della scheda è costituito da componenti denominati `elements`.</span><span class="sxs-lookup"><span data-stu-id="cc2f3-107">`body` - The body of the card is made up of building-blocks known as `elements`.</span></span> <span data-ttu-id="cc2f3-108">Gli elementi possono essere composti in modi praticamente illimitati per creare diversi tipi di schede.</span><span class="sxs-lookup"><span data-stu-id="cc2f3-108">Elements can be composed in nearly infinite arrangements to create many types of cards.</span></span> 
* <span data-ttu-id="cc2f3-109">`actions` - Molte schede includono un set di azioni che un utente può eseguire su di esse.</span><span class="sxs-lookup"><span data-stu-id="cc2f3-109">`actions` - Many cards have a set of actions a user may take on it.</span></span> <span data-ttu-id="cc2f3-110">Questa proprietà descrive tali azioni, di cui in genere viene eseguito il rendering in una "barra delle azioni" nella parte inferiore.</span><span class="sxs-lookup"><span data-stu-id="cc2f3-110">This property describes those actions which typically get rendered in an "action bar" at the bottom.</span></span>

### <a name="example-card"></a><span data-ttu-id="cc2f3-111">Scheda di esempio</span><span class="sxs-lookup"><span data-stu-id="cc2f3-111">Example Card</span></span>

<span data-ttu-id="cc2f3-112">Questa scheda di esempio include una singola riga di testo seguita da un'immagine.</span><span class="sxs-lookup"><span data-stu-id="cc2f3-112">This sample card which includes a single line of text followed by an image.</span></span>

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

## <a name="type-property"></a><span data-ttu-id="cc2f3-113">Proprietà `Type`</span><span class="sxs-lookup"><span data-stu-id="cc2f3-113">`Type` property</span></span>

<span data-ttu-id="cc2f3-114">Ogni elemento ha una proprietà `type` che identifica il tipo di oggetto.</span><span class="sxs-lookup"><span data-stu-id="cc2f3-114">Every element has a `type` property which identifies what kind of object it is.</span></span> <span data-ttu-id="cc2f3-115">Esaminando la scheda precedente, puoi notare che sono presenti due elementi, `TextBlock` e `Image`.</span><span class="sxs-lookup"><span data-stu-id="cc2f3-115">Looking at the above card, you can see we have two elements, a `TextBlock` and an `Image`.</span></span>

<span data-ttu-id="cc2f3-116">Tutti gli elementi della scheda adattiva **sono raggruppati verticalmente** e **si espandono in base alla larghezza del relativo elemento padre** (in modo simile a `display: block` nel codice HTML).</span><span class="sxs-lookup"><span data-stu-id="cc2f3-116">All Adaptive Card elements **stack vertically** and **expand to the width of their parent** (think `display: block` in HTML).</span></span> <span data-ttu-id="cc2f3-117">Tuttavia, puoi usare un `ColumnSet` per creare colonne affiancate di contenitori.</span><span class="sxs-lookup"><span data-stu-id="cc2f3-117">However, you can use a `ColumnSet` to create side-by-side columns of containers.</span></span>

## <a name="adaptive-elements"></a><span data-ttu-id="cc2f3-118">Elementi adattivi</span><span class="sxs-lookup"><span data-stu-id="cc2f3-118">Adaptive Elements</span></span>

<span data-ttu-id="cc2f3-119">Gli elementi più importanti sono:</span><span class="sxs-lookup"><span data-stu-id="cc2f3-119">The most fundamental elements are:</span></span>

* <span data-ttu-id="cc2f3-120">**TextBlock** - Aggiunge un blocco di testo con le proprietà per controllare l'aspetto del testo</span><span class="sxs-lookup"><span data-stu-id="cc2f3-120">**TextBlock** - adds a block of text with properties to control what the text looks like</span></span>
* <span data-ttu-id="cc2f3-121">**Image** - Aggiunge un'immagine con le proprietà per controllare l'aspetto dell'immagine</span><span class="sxs-lookup"><span data-stu-id="cc2f3-121">**Image** - adds an image with properties to control what the image looks like</span></span>

## <a name="container-elements"></a><span data-ttu-id="cc2f3-122">Elementi contenitore</span><span class="sxs-lookup"><span data-stu-id="cc2f3-122">Container elements</span></span>

<span data-ttu-id="cc2f3-123">Le schede possono anche includere contenitori, che organizzano una raccolta di elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="cc2f3-123">Cards can also have containers, which arrange a collection of child elements.</span></span>

* <span data-ttu-id="cc2f3-124">**Container** - Definisce una raccolta di elementi</span><span class="sxs-lookup"><span data-stu-id="cc2f3-124">**Container** - Defines a a collection of elements</span></span>
* <span data-ttu-id="cc2f3-125">**ColumnSet/Column** - Definisce una raccolta di colonne, in cui ogni colonna è un contenitore</span><span class="sxs-lookup"><span data-stu-id="cc2f3-125">**ColumnSet/Column** - Defines a collection of columns, each column is a container</span></span>
* <span data-ttu-id="cc2f3-126">**FactSet** - Contenitore di fatti</span><span class="sxs-lookup"><span data-stu-id="cc2f3-126">**FactSet** - Container of Facts</span></span>
* <span data-ttu-id="cc2f3-127">**ImageSet** - Contenitore di immagini che consente all'interfaccia utente di visualizzare l'esperienza Raccolta foto appropriata per una raccolta di immagini.</span><span class="sxs-lookup"><span data-stu-id="cc2f3-127">**ImageSet** - Container of Images so that UI can show appropriate photo gallery experience for a collection of images.</span></span>

## <a name="input-elements"></a><span data-ttu-id="cc2f3-128">Elementi di input</span><span class="sxs-lookup"><span data-stu-id="cc2f3-128">Input elements</span></span>

<span data-ttu-id="cc2f3-129">Gli elementi di input consentono di richiedere all'interfaccia utente nativa di creare semplici moduli:</span><span class="sxs-lookup"><span data-stu-id="cc2f3-129">Input elements allow you to ask for native UI to build simple forms:</span></span>

* <span data-ttu-id="cc2f3-130">**Input.Text** - Consente di ottenere contenuto di testo dall'utente</span><span class="sxs-lookup"><span data-stu-id="cc2f3-130">**Input.Text** - get text content from the user</span></span>
* <span data-ttu-id="cc2f3-131">**Input.Date** - Consente di ottenere una data dall'utente</span><span class="sxs-lookup"><span data-stu-id="cc2f3-131">**Input.Date** - get a Date from the user</span></span>
* <span data-ttu-id="cc2f3-132">**Input.Time** - Consente di ottenere un'ora dall'utente</span><span class="sxs-lookup"><span data-stu-id="cc2f3-132">**Input.Time** - get a Time from the user</span></span>
* <span data-ttu-id="cc2f3-133">**Input.Number** - Consente di ottenere un numero dall'utente</span><span class="sxs-lookup"><span data-stu-id="cc2f3-133">**Input.Number** - get a Number from the user</span></span>
* <span data-ttu-id="cc2f3-134">**Input.ChoiceSet** - Consente di offrire all'utente un set di scelte da cui può effettuare una selezione</span><span class="sxs-lookup"><span data-stu-id="cc2f3-134">**Input.ChoiceSet** - Give the user a set of choices and have them pick</span></span>
* <span data-ttu-id="cc2f3-135">**Input.Toggle** - Consente di offrire all'utente una singola scelta tra due elementi da cui può effettuare una selezione</span><span class="sxs-lookup"><span data-stu-id="cc2f3-135">**Input.Toggle** - Give the user a single choice between two items and have them pick</span></span>

## <a name="actions"></a><span data-ttu-id="cc2f3-136">Azioni</span><span class="sxs-lookup"><span data-stu-id="cc2f3-136">Actions</span></span>

<span data-ttu-id="cc2f3-137">Le azioni aggiungono pulsanti alla scheda.</span><span class="sxs-lookup"><span data-stu-id="cc2f3-137">Actions add buttons to the card.</span></span> <span data-ttu-id="cc2f3-138">Questi pulsanti consentono di eseguire un'ampia varietà di azioni, come l'apertura di un URL o l'invio di dati.</span><span class="sxs-lookup"><span data-stu-id="cc2f3-138">These can perform a variety of actions, like opening a URL or submitting some data.</span></span>

* <span data-ttu-id="cc2f3-139">**Action.OpenUrl** - Il pulsante apre un URL esterno per la visualizzazione</span><span class="sxs-lookup"><span data-stu-id="cc2f3-139">**Action.OpenUrl** - the button opens an external URL for viewing</span></span>
* <span data-ttu-id="cc2f3-140">**Action.ShowCard** - Richiede la visualizzazione all'utente di una scheda secondaria.</span><span class="sxs-lookup"><span data-stu-id="cc2f3-140">**Action.ShowCard** - Requests a sub-card to be shown to the user.</span></span>
* <span data-ttu-id="cc2f3-141">**Action.Submit** - Richiede la raccolta di tutti gli elementi di input in un oggetto che viene quindi inviato all'utente tramite un metodo definito dall'applicazione host.</span><span class="sxs-lookup"><span data-stu-id="cc2f3-141">**Action.Submit** - Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

> <span data-ttu-id="cc2f3-142">**Esempio di Action.Submit**: Con Skype, Action.Submit invierà al bot un'attività bot di Bot Framework con la proprietà **Value** che contiene un oggetto con tutti i dati di input.</span><span class="sxs-lookup"><span data-stu-id="cc2f3-142">**Example Action.Submit**: With Skype, an Action.Submit will send a Bot Framework bot activity back to the bot with the **Value** property containing an object with all of the input data on it.</span></span>

## <a name="learn-more"></a><span data-ttu-id="cc2f3-143">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="cc2f3-143">Learn More</span></span>

* <span data-ttu-id="cc2f3-144">[Esamina le schede di esempio](https://adaptivecards.io/samples/) per trovare l'ispirazione</span><span class="sxs-lookup"><span data-stu-id="cc2f3-144">[Browse Sample cards](https://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="cc2f3-145">Usa [Schema Explorer](https://adaptivecards.io/explorer) per informazioni sugli elementi disponibili</span><span class="sxs-lookup"><span data-stu-id="cc2f3-145">Use the [Schema Explorer](https://adaptivecards.io/explorer) to browse the available elements</span></span>
* <span data-ttu-id="cc2f3-146">Crea una scheda usando il [visualizzatore interattivo](https://adaptivecards.io/visualizer/)</span><span class="sxs-lookup"><span data-stu-id="cc2f3-146">Build a card using the [Interactive Visualizer](https://adaptivecards.io/visualizer/)</span></span>
* <span data-ttu-id="cc2f3-147">[Contattaci](https://adaptivecards.io/connect) per eventuali commenti</span><span class="sxs-lookup"><span data-stu-id="cc2f3-147">[Get in touch](https://adaptivecards.io/connect) with any feedback you have</span></span>
