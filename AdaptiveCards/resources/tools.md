---
title: Le schede adattive strumenti
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: 35ce89653a6cf2a313518be0f221a166e1eb7711
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552503"
---
# <a name="card-designer"></a><span data-ttu-id="300e4-102">Finestra di progettazione smart card</span><span class="sxs-lookup"><span data-stu-id="300e4-102">Card Designer</span></span> 

<span data-ttu-id="300e4-103">Necessario per uno strumento per le schede di progettazione?</span><span class="sxs-lookup"><span data-stu-id="300e4-103">Need for a tool to design your cards?</span></span> <span data-ttu-id="300e4-104">Servono solo la finestra di progettazione basata su browser scheda adattiva in [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="300e4-104">Look no further than the browser-based adaptive card designer at [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span></span>

<span data-ttu-id="300e4-105">[![screenshot della finestra di progettazione](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="300e4-105">[![designer screenshot](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span></span>

## <a name="embed-the-designer-into-your-app"></a><span data-ttu-id="300e4-106">Incorporare la finestra di progettazione nell'app</span><span class="sxs-lookup"><span data-stu-id="300e4-106">Embed the designer into your app</span></span>

<span data-ttu-id="300e4-107">Motivo per cui indirizzare gli utenti non esiste, quando possibile, ma **incorporare la finestra di progettazione di smart card direttamente nell'interfaccia web** app usando la libreria JavaScript.</span><span class="sxs-lookup"><span data-stu-id="300e4-107">But why send your users there when you can **embed the card designer directly into your web** app using our JavaScript library.</span></span> 

<span data-ttu-id="300e4-108">Consultare il [adaptivecards-finestra di progettazione](https://npmjs.com/adaptivecards-designer) pacchetto per iniziare.</span><span class="sxs-lookup"><span data-stu-id="300e4-108">Check out the [adaptivecards-designer](https://npmjs.com/adaptivecards-designer) package to get started.</span></span>

# <a name="schema-validation"></a><span data-ttu-id="300e4-109">Convalida dello schema</span><span class="sxs-lookup"><span data-stu-id="300e4-109">Schema validation</span></span>

<span data-ttu-id="300e4-110">Convalida dello schema è un modo potente per rendere più semplice di creazione e l'abilitazione degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="300e4-110">Schema validation is a powerful way of making authoring easier and enabling tooling.</span></span>

## <a name="json-schema"></a><span data-ttu-id="300e4-111">Schema JSON</span><span class="sxs-lookup"><span data-stu-id="300e4-111">JSON Schema</span></span>
<span data-ttu-id="300e4-112">Microsoft ha fornito una completa [file di Schema JSON](http://adaptivecards.io/schemas/adaptive-card.json) per la modifica e convalida le schede adattive in formato json.</span><span class="sxs-lookup"><span data-stu-id="300e4-112">We have provided a complete [JSON Schema file](http://adaptivecards.io/schemas/adaptive-card.json) for editing and validating adaptive cards in json.</span></span>

<span data-ttu-id="300e4-113">In Visual Studio e Visual Studio Code è possibile ottenere Intellisense automatico includendo un `$schema` riferimento.</span><span class="sxs-lookup"><span data-stu-id="300e4-113">In Visual Studio and Visual Studio Code you can get automatic Intellisense by including a `$schema` reference.</span></span>

![non valido](media/tools/invalidjson1.png)

![Completamento automatico](media/tools/autocomplete.png)

### <a name="example"></a><span data-ttu-id="300e4-116">Esempio</span><span class="sxs-lookup"><span data-stu-id="300e4-116">Example</span></span>

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "0.5",
    "body": []
}
```

# <a name="tools-and-samples"></a><span data-ttu-id="300e4-117">Strumenti ed esempi</span><span class="sxs-lookup"><span data-stu-id="300e4-117">Tools and samples</span></span>
<span data-ttu-id="300e4-118">Esistono alcuni strumenti e gli esempi nell'albero di origine che sono riferimenti utili, nonché strumenti utili.</span><span class="sxs-lookup"><span data-stu-id="300e4-118">There are some tools and samples in the source tree which are useful references as well as useful tools.</span></span>

## <a name="visual-studio-code-extension"></a><span data-ttu-id="300e4-119">Estensione Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="300e4-119">Visual Studio Code Extension</span></span>
<span data-ttu-id="300e4-120">È stata creata un'estensione di Visual Studio code che consente di visualizzare la scheda che si sta modificando in tempo reale all'interno dell'editor stesso.</span><span class="sxs-lookup"><span data-stu-id="300e4-120">We have created a Visual Studio code extension which allows you to visualize the card you are editing in real time inside the editor itself.</span></span> 

![Estensione](media/tools/vscode-extension.png)

<span data-ttu-id="300e4-122">Per installare, aprire estensioni del Marketplace e cercare **adattivo scheda Visualizzatore**.</span><span class="sxs-lookup"><span data-stu-id="300e4-122">To install, open Extensions Marketplace and search for **Adaptive Card Viewer**.</span></span>

![Marketplace](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a><span data-ttu-id="300e4-124">Uso</span><span class="sxs-lookup"><span data-stu-id="300e4-124">Usage</span></span>

<span data-ttu-id="300e4-125">Quando si modifica un file con estensione JSON con una scheda adattiva `$schema` è possibile visualizzare utilizzando proprietà `Ctrl+Shift+V A`.</span><span class="sxs-lookup"><span data-stu-id="300e4-125">When you are editing a .json file with an Adaptive Card `$schema` property you can view by using `Ctrl+Shift+V A`.</span></span>
```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a><span data-ttu-id="300e4-126">Opzioni</span><span class="sxs-lookup"><span data-stu-id="300e4-126">Options</span></span>

<span data-ttu-id="300e4-127">La seguente impostazione di Visual Studio Code è disponibile per il Visualizzatore AdaptiveCards.</span><span class="sxs-lookup"><span data-stu-id="300e4-127">The following Visual Studio Code setting is available for the AdaptiveCards Viewer.</span></span> <span data-ttu-id="300e4-128">Può essere impostata in impostazioni utente o dell'area di lavoro.</span><span class="sxs-lookup"><span data-stu-id="300e4-128">This can be set in User Settings or Workspace Settings.</span></span>

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="300e4-129">Esempio di Visualizzatore WPF</span><span class="sxs-lookup"><span data-stu-id="300e4-129">WPF Visualizer Sample</span></span>
<span data-ttu-id="300e4-130">Il [progetto di esempio Visualizzatore WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) consente di visualizzare le schede tramite/Xaml WPF in un computer Windows.</span><span class="sxs-lookup"><span data-stu-id="300e4-130">The [WPF visualizer sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF/Xaml on a Windows machine.</span></span>  <span data-ttu-id="300e4-131">Oggetto `hostconfig` editor è disponibile per la modifica e la visualizzazione delle impostazioni di configurazione host.</span><span class="sxs-lookup"><span data-stu-id="300e4-131">A `hostconfig` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="300e4-132">Salvare queste impostazioni in un formato JSON per utilizzarle nel rendering nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="300e4-132">Save these settings as a JSON to use them in rendering in your application.</span></span>

![Visualizzatore WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a><span data-ttu-id="300e4-134">Esempio di ImageRender WPF</span><span class="sxs-lookup"><span data-stu-id="300e4-134">WPF ImageRender Sample</span></span>
<span data-ttu-id="300e4-135">Il [progetto di esempio ImageRender](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) Trasforma qualsiasi scheda in un file PNG dalla riga di comando utilizzando WPF.</span><span class="sxs-lookup"><span data-stu-id="300e4-135">The [ImageRender sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) turns any card into a PNG from the command line using WPF.</span></span> 
