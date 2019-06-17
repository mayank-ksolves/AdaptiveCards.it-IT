---
title: Le schede adattive strumenti
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: ad520693224509deaf0ea1c2cd6a837089dbf2d5
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2019
ms.locfileid: "67137984"
---
# <a name="tools-and-samples"></a><span data-ttu-id="8eaaa-102">Strumenti ed esempi</span><span class="sxs-lookup"><span data-stu-id="8eaaa-102">Tools and Samples</span></span>

## <a name="card-designer"></a><span data-ttu-id="8eaaa-103">Finestra di progettazione smart card</span><span class="sxs-lookup"><span data-stu-id="8eaaa-103">Card Designer</span></span> 

<span data-ttu-id="8eaaa-104">Necessario per uno strumento per le schede di progettazione?</span><span class="sxs-lookup"><span data-stu-id="8eaaa-104">Need for a tool to design your cards?</span></span> <span data-ttu-id="8eaaa-105">Servono solo la finestra di progettazione basata su browser scheda adattiva in [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="8eaaa-105">Look no further than the browser-based adaptive card designer at [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span></span>

<span data-ttu-id="8eaaa-106">[![screenshot della finestra di progettazione](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="8eaaa-106">[![designer screenshot](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span></span>

### <a name="embed-the-designer-into-your-app"></a><span data-ttu-id="8eaaa-107">Incorporare la finestra di progettazione nell'app</span><span class="sxs-lookup"><span data-stu-id="8eaaa-107">Embed the designer into your app</span></span>

<span data-ttu-id="8eaaa-108">Motivo per cui indirizzare gli utenti non esiste, quando possibile, ma **incorporare la finestra di progettazione di smart card direttamente nell'interfaccia web** app usando la libreria JavaScript.</span><span class="sxs-lookup"><span data-stu-id="8eaaa-108">But why send your users there when you can **embed the card designer directly into your web** app using our JavaScript library.</span></span> 

<span data-ttu-id="8eaaa-109">Consultare il [adaptivecards-finestra di progettazione](https://npmjs.com/adaptivecards-designer) pacchetto per iniziare.</span><span class="sxs-lookup"><span data-stu-id="8eaaa-109">Check out the [adaptivecards-designer](https://npmjs.com/adaptivecards-designer) package to get started.</span></span>

## <a name="schema-validation"></a><span data-ttu-id="8eaaa-110">Convalida dello schema</span><span class="sxs-lookup"><span data-stu-id="8eaaa-110">Schema validation</span></span>

<span data-ttu-id="8eaaa-111">Convalida dello schema è un modo potente per rendere più semplice di creazione e l'abilitazione degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="8eaaa-111">Schema validation is a powerful way of making authoring easier and enabling tooling.</span></span>

<span data-ttu-id="8eaaa-112">Microsoft ha fornito una completa [file di Schema JSON](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json) per la modifica e convalida le schede adattive in formato json.</span><span class="sxs-lookup"><span data-stu-id="8eaaa-112">We have provided a complete [JSON Schema file](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json) for editing and validating adaptive cards in json.</span></span> <span data-ttu-id="8eaaa-113">Si noti che l'URL dello schema è con controllo delle versioni, le versioni più recenti delle schede adattive avrà un URL corrispondente.</span><span class="sxs-lookup"><span data-stu-id="8eaaa-113">Note that the schema URL is versioned, newer versions of Adaptive Cards will have a corresponding URL.</span></span>

<span data-ttu-id="8eaaa-114">In Visual Studio e Visual Studio Code è possibile ottenere Intellisense automatico includendo un `$schema` riferimento.</span><span class="sxs-lookup"><span data-stu-id="8eaaa-114">In Visual Studio and Visual Studio Code you can get automatic Intellisense by including a `$schema` reference.</span></span>

![non valido](media/tools/invalidjson1.png)

![Completamento automatico](media/tools/autocomplete.png)

## <a name="example"></a><span data-ttu-id="8eaaa-117">Esempio</span><span class="sxs-lookup"><span data-stu-id="8eaaa-117">Example</span></span>

```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

## <a name="visual-studio-code-extension"></a><span data-ttu-id="8eaaa-118">Estensione Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8eaaa-118">Visual Studio Code Extension</span></span>

<span data-ttu-id="8eaaa-119">È stata creata un'estensione di Visual Studio code che consente di visualizzare la scheda che si sta modificando in tempo reale all'interno dell'editor stesso.</span><span class="sxs-lookup"><span data-stu-id="8eaaa-119">We have created a Visual Studio code extension which allows you to visualize the card you are editing in real time inside the editor itself.</span></span> 

![Estensione](media/tools/vscode-extension.png)

<span data-ttu-id="8eaaa-121">Per installare, aprire estensioni del Marketplace e cercare **adattivo scheda Visualizzatore**.</span><span class="sxs-lookup"><span data-stu-id="8eaaa-121">To install, open Extensions Marketplace and search for **Adaptive Card Viewer**.</span></span>

![Marketplace](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a><span data-ttu-id="8eaaa-123">Uso</span><span class="sxs-lookup"><span data-stu-id="8eaaa-123">Usage</span></span>

<span data-ttu-id="8eaaa-124">Quando si modifica un file con estensione JSON con una scheda adattiva `$schema` è possibile visualizzare utilizzando proprietà `Ctrl+Shift+V A`.</span><span class="sxs-lookup"><span data-stu-id="8eaaa-124">When you are editing a .json file with an Adaptive Card `$schema` property you can view by using `Ctrl+Shift+V A`.</span></span>
```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a><span data-ttu-id="8eaaa-125">Opzioni</span><span class="sxs-lookup"><span data-stu-id="8eaaa-125">Options</span></span>

<span data-ttu-id="8eaaa-126">La seguente impostazione di Visual Studio Code è disponibile per il Visualizzatore AdaptiveCards.</span><span class="sxs-lookup"><span data-stu-id="8eaaa-126">The following Visual Studio Code setting is available for the AdaptiveCards Viewer.</span></span> <span data-ttu-id="8eaaa-127">Può essere impostata in impostazioni utente o dell'area di lavoro.</span><span class="sxs-lookup"><span data-stu-id="8eaaa-127">This can be set in User Settings or Workspace Settings.</span></span>

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="8eaaa-128">Esempio di Visualizzatore WPF</span><span class="sxs-lookup"><span data-stu-id="8eaaa-128">WPF Visualizer Sample</span></span>

<span data-ttu-id="8eaaa-129">Il [progetto di esempio Visualizzatore WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) consente di visualizzare le schede tramite/Xaml WPF in un computer Windows.</span><span class="sxs-lookup"><span data-stu-id="8eaaa-129">The [WPF visualizer sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF/Xaml on a Windows machine.</span></span>  <span data-ttu-id="8eaaa-130">Oggetto `hostconfig` editor è disponibile per la modifica e la visualizzazione delle impostazioni di configurazione host.</span><span class="sxs-lookup"><span data-stu-id="8eaaa-130">A `hostconfig` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="8eaaa-131">Salvare queste impostazioni in un formato JSON per utilizzarle nel rendering nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="8eaaa-131">Save these settings as a JSON to use them in rendering in your application.</span></span>

![Visualizzatore WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a><span data-ttu-id="8eaaa-133">Esempio di ImageRender WPF</span><span class="sxs-lookup"><span data-stu-id="8eaaa-133">WPF ImageRender Sample</span></span>

<span data-ttu-id="8eaaa-134">Il [progetto di esempio ImageRender](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) Trasforma qualsiasi scheda in un file PNG dalla riga di comando utilizzando WPF.</span><span class="sxs-lookup"><span data-stu-id="8eaaa-134">The [ImageRender sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) turns any card into a PNG from the command line using WPF.</span></span> 
