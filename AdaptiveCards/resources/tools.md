---
title: Strumenti delle schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: 819788313d78b4057fb5d3dc4d5a9be658566642
ms.sourcegitcommit: 996fc604e59f72ba1dd96c29f4b517862a5264e9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/04/2020
ms.locfileid: "87566025"
---
# <a name="tools-and-samples"></a><span data-ttu-id="10d92-102">Strumenti ed esempi</span><span class="sxs-lookup"><span data-stu-id="10d92-102">Tools and Samples</span></span>

## <a name="card-designer"></a><span data-ttu-id="10d92-103">Strumento di progettazione delle schede</span><span class="sxs-lookup"><span data-stu-id="10d92-103">Card Designer</span></span> 

<span data-ttu-id="10d92-104">Ti serve uno strumento per progettare le schede?</span><span class="sxs-lookup"><span data-stu-id="10d92-104">Need for a tool to design your cards?</span></span> <span data-ttu-id="10d92-105">All'indirizzo [https://adaptivecards.io/designer](https://adaptivecards.io/designer) è disponibile uno strumento basato su browser per la progettazione di schede adattive.</span><span class="sxs-lookup"><span data-stu-id="10d92-105">Look no further than the browser-based adaptive card designer at [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span></span>

<span data-ttu-id="10d92-106">[![screenshot dello strumento di progettazione](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="10d92-106">[![designer screenshot](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span></span>

### <a name="embed-the-designer-into-your-app"></a><span data-ttu-id="10d92-107">Incorporare lo strumento di progettazione nell'app</span><span class="sxs-lookup"><span data-stu-id="10d92-107">Embed the designer into your app</span></span>

<span data-ttu-id="10d92-108">Ma perché dovresti indirizzare gli utenti a tale sito quando puoi **incorporare lo strumento di progettazione delle schede direttamente nell'app Web** usando la libreria JavaScript?</span><span class="sxs-lookup"><span data-stu-id="10d92-108">But why send your users there when you can **embed the card designer directly into your web** app using our JavaScript library.</span></span> 

<span data-ttu-id="10d92-109">Per iniziare, vedi il pacchetto [adaptivecards-designer](https://npmjs.com/adaptivecards-designer).</span><span class="sxs-lookup"><span data-stu-id="10d92-109">Check out the [adaptivecards-designer](https://npmjs.com/adaptivecards-designer) package to get started.</span></span>

## <a name="schema-validation"></a><span data-ttu-id="10d92-110">Convalida dello schema</span><span class="sxs-lookup"><span data-stu-id="10d92-110">Schema validation</span></span>

<span data-ttu-id="10d92-111">La convalida dello schema è un modo efficace per semplificare la creazione e abilitare gli strumenti.</span><span class="sxs-lookup"><span data-stu-id="10d92-111">Schema validation is a powerful way of making authoring easier and enabling tooling.</span></span>

<span data-ttu-id="10d92-112">È stato fornito un [file di schema JSON](https://adaptivecards.io/schemas/1.2.0/adaptive-card.json) completo per la modifica e la convalida di schede adattive in JSON.</span><span class="sxs-lookup"><span data-stu-id="10d92-112">We have provided a complete [JSON Schema file](https://adaptivecards.io/schemas/1.2.0/adaptive-card.json) for editing and validating adaptive cards in json.</span></span> <span data-ttu-id="10d92-113">L'URL dello schema è con versione, pertanto le versioni più recenti delle schede adattive avranno un URL corrispondente.</span><span class="sxs-lookup"><span data-stu-id="10d92-113">Note that the schema URL is versioned, newer versions of Adaptive Cards will have a corresponding URL.</span></span>

<span data-ttu-id="10d92-114">In Visual Studio e Visual Studio Code puoi ottenere IntelliSense automatico includendo un riferimento `$schema`.</span><span class="sxs-lookup"><span data-stu-id="10d92-114">In Visual Studio and Visual Studio Code you can get automatic Intellisense by including a `$schema` reference.</span></span>

![non valido](media/tools/invalidjson1.png)

![completamento automatico](media/tools/autocomplete.png)

## <a name="example"></a><span data-ttu-id="10d92-117">Esempio</span><span class="sxs-lookup"><span data-stu-id="10d92-117">Example</span></span>

```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

## <a name="visual-studio-code-extensions"></a><span data-ttu-id="10d92-118">Estensioni di Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="10d92-118">Visual Studio Code Extensions</span></span>

### <a name="adaptive-cards-studio"></a><span data-ttu-id="10d92-119">**Adaptive Card Studio**</span><span class="sxs-lookup"><span data-stu-id="10d92-119">**Adaptive Cards Studio**</span></span>

![marketplace](https://madewithcards.blob.core.windows.net/uploads/29bb3d02-2158-40b8-8420-4dd1f15da34c-acstudio.png)

<span data-ttu-id="10d92-121">Con Adaptive Card Studio puoi creare e modificare schede direttamente in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="10d92-121">With AdaptiveCards Studio you can author cards directly in Visual Studio Code.</span></span> <span data-ttu-id="10d92-122">L'estensione rileva automaticamente tutte le schede adattive nell'area di lavoro e consente di modificare facilmente il modello di scheda e i dati di esempio.</span><span class="sxs-lookup"><span data-stu-id="10d92-122">The Extension automatically detects all Adaptive Cards in your working space and lets you easily edit the card template and sample data.</span></span>

[<span data-ttu-id="10d92-123">Leggi altre informazioni e installa l'estensione da Visual Studio Code Marketplace</span><span class="sxs-lookup"><span data-stu-id="10d92-123">Read more and install it from the Visual Studio Code Marketplace</span></span>](https://marketplace.visualstudio.com/items?itemName=madewithcardsio.adaptivecardsstudiobeta)


### <a name="adaptive-card-viewer"></a><span data-ttu-id="10d92-124">**Adaptive Card Viewer**</span><span class="sxs-lookup"><span data-stu-id="10d92-124">**Adaptive Card Viewer**</span></span>

<span data-ttu-id="10d92-125">È stata creata un'estensione di Visual Studio Code che ti consente di visualizzare la scheda che stai modificando in tempo reale all'interno dell'editor.</span><span class="sxs-lookup"><span data-stu-id="10d92-125">We have created a Visual Studio code extension which allows you to visualize the card you are editing in real time inside the editor itself.</span></span> 

![estensione](media/tools/vscode-extension.png)

<span data-ttu-id="10d92-127">Per eseguire l'installazione, apri il Marketplace delle estensioni e cerca **Adaptive Card Viewer**.</span><span class="sxs-lookup"><span data-stu-id="10d92-127">To install, open Extensions Marketplace and search for **Adaptive Card Viewer**.</span></span>

![marketplace](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a><span data-ttu-id="10d92-129">Uso</span><span class="sxs-lookup"><span data-stu-id="10d92-129">Usage</span></span>

<span data-ttu-id="10d92-130">Quando modifichi un file con estensione json con una proprietà `$schema` della scheda adattiva, puoi visualizzare tramite `Ctrl+Shift+V A`.</span><span class="sxs-lookup"><span data-stu-id="10d92-130">When you are editing a .json file with an Adaptive Card `$schema` property you can view by using `Ctrl+Shift+V A`.</span></span>
```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a><span data-ttu-id="10d92-131">Opzioni</span><span class="sxs-lookup"><span data-stu-id="10d92-131">Options</span></span>

<span data-ttu-id="10d92-132">Per Adaptive Card Viewer è disponibile l'impostazione seguente di Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="10d92-132">The following Visual Studio Code setting is available for the AdaptiveCards Viewer.</span></span> <span data-ttu-id="10d92-133">Questa impostazione può essere configurata in Impostazioni utente o in Impostazioni area di lavoro.</span><span class="sxs-lookup"><span data-stu-id="10d92-133">This can be set in User Settings or Workspace Settings.</span></span>

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="10d92-134">Esempio di visualizzatore WPF</span><span class="sxs-lookup"><span data-stu-id="10d92-134">WPF Visualizer Sample</span></span>

<span data-ttu-id="10d92-135">Il [progetto di esempio di visualizzatore WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) ti consente di visualizzare le schede usando WPF/XAML in un computer Windows.</span><span class="sxs-lookup"><span data-stu-id="10d92-135">The [WPF visualizer sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF/Xaml on a Windows machine.</span></span>  <span data-ttu-id="10d92-136">Un editor `hostconfig` è integrato per la modifica e la visualizzazione delle impostazioni di configurazione host.</span><span class="sxs-lookup"><span data-stu-id="10d92-136">A `hostconfig` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="10d92-137">Salva tali impostazioni come JSON per usarle nel rendering all'interno dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="10d92-137">Save these settings as a JSON to use them in rendering in your application.</span></span>

![visualizzatore WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a><span data-ttu-id="10d92-139">Esempio di renderer di immagini WPF</span><span class="sxs-lookup"><span data-stu-id="10d92-139">WPF ImageRender Sample</span></span>

<span data-ttu-id="10d92-140">Il [progetto di esempio di renderer di immagini](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) converte qualsiasi scheda in un file PNG dalla riga di comando tramite WPF.</span><span class="sxs-lookup"><span data-stu-id="10d92-140">The [ImageRender sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) turns any card into a PNG from the command line using WPF.</span></span> 
