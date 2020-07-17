---
title: Stile nativo-.NET WPF SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: f9243fc6880c926c04f80f74713e91d1e37cf3d5
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417594"
---
# <a name="native-styling---net-wpf"></a><span data-ttu-id="16bb5-102">Stile nativo-WPF .NET</span><span class="sxs-lookup"><span data-stu-id="16bb5-102">Native styling - .NET WPF</span></span>

<span data-ttu-id="16bb5-103">Sebbene la configurazione host consentirà di ottenere la maggior parte delle piattaforme in ogni piattaforma, è probabile che sarà necessario eseguire alcuni stili nativi su ogni piattaforma.</span><span class="sxs-lookup"><span data-stu-id="16bb5-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="16bb5-104">WPF semplifica questa operazione consentendo di passare un oggetto ResourceDictionary per lo stile, il comportamento, le animazioni e così via.</span><span class="sxs-lookup"><span data-stu-id="16bb5-104">WPF makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="16bb5-105">Elemento</span><span class="sxs-lookup"><span data-stu-id="16bb5-105">Element</span></span> | <span data-ttu-id="16bb5-106">Nomi di stile</span><span class="sxs-lookup"><span data-stu-id="16bb5-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="16bb5-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="16bb5-107">AdaptiveCard</span></span> | <span data-ttu-id="16bb5-108">Adaptive. Card</span><span class="sxs-lookup"><span data-stu-id="16bb5-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="16bb5-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="16bb5-109">Action.OpenUrl</span></span>  | <span data-ttu-id="16bb5-110">Adaptive. Action. OpenUrl</span><span class="sxs-lookup"><span data-stu-id="16bb5-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="16bb5-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="16bb5-111">Action.ShowCard</span></span> | <span data-ttu-id="16bb5-112">Adaptive. Action. ShowCard</span><span class="sxs-lookup"><span data-stu-id="16bb5-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="16bb5-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="16bb5-113">Action.Submit</span></span>  | <span data-ttu-id="16bb5-114">Adattivo. azione. Invia</span><span class="sxs-lookup"><span data-stu-id="16bb5-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="16bb5-115">Colonna</span><span class="sxs-lookup"><span data-stu-id="16bb5-115">Column</span></span> | <span data-ttu-id="16bb5-116">Adaptive. Column, Adaptive. Action. Tap</span><span class="sxs-lookup"><span data-stu-id="16bb5-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="16bb5-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="16bb5-117">ColumnSet</span></span> | <span data-ttu-id="16bb5-118">Adaptive. ColumnStore, Adaptive. VerticalSeparator</span><span class="sxs-lookup"><span data-stu-id="16bb5-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="16bb5-119">Contenitore</span><span class="sxs-lookup"><span data-stu-id="16bb5-119">Container</span></span> | <span data-ttu-id="16bb5-120">Adaptive. container</span><span class="sxs-lookup"><span data-stu-id="16bb5-120">Adaptive.Container</span></span>|
| <span data-ttu-id="16bb5-121">Input. Choices</span><span class="sxs-lookup"><span data-stu-id="16bb5-121">Input.ChoiceSet</span></span> | <span data-ttu-id="16bb5-122">Adaptive. input. Choices, Adaptive. input. Choices. ComboBox, Adaptive. input. Choicet. CheckBox, Adaptive. input. Choicet. Radio, Adaptive. input. Choices. ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="16bb5-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="16bb5-123">Input. Data</span><span class="sxs-lookup"><span data-stu-id="16bb5-123">Input.Date</span></span> | <span data-ttu-id="16bb5-124">Adaptive. input. Text. date</span><span class="sxs-lookup"><span data-stu-id="16bb5-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="16bb5-125">Input. Number</span><span class="sxs-lookup"><span data-stu-id="16bb5-125">Input.Number</span></span> | <span data-ttu-id="16bb5-126">Adaptive. input. Text. Number</span><span class="sxs-lookup"><span data-stu-id="16bb5-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="16bb5-127">Input. Text</span><span class="sxs-lookup"><span data-stu-id="16bb5-127">Input.Text</span></span> | <span data-ttu-id="16bb5-128">Adaptive. input. Text</span><span class="sxs-lookup"><span data-stu-id="16bb5-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="16bb5-129">Input. Time</span><span class="sxs-lookup"><span data-stu-id="16bb5-129">Input.Time</span></span> | <span data-ttu-id="16bb5-130">Adaptive. input. Text. Time</span><span class="sxs-lookup"><span data-stu-id="16bb5-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="16bb5-131">Input. interruttore</span><span class="sxs-lookup"><span data-stu-id="16bb5-131">Input.Toggle</span></span>| <span data-ttu-id="16bb5-132">Adaptive. input. Attiva/Nascondi</span><span class="sxs-lookup"><span data-stu-id="16bb5-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="16bb5-133">Immagine</span><span class="sxs-lookup"><span data-stu-id="16bb5-133">Image</span></span>  | <span data-ttu-id="16bb5-134">Adaptive. image</span><span class="sxs-lookup"><span data-stu-id="16bb5-134">Adaptive.Image</span></span> |
| <span data-ttu-id="16bb5-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="16bb5-135">ImageSet</span></span>  | <span data-ttu-id="16bb5-136">Adaptive. images</span><span class="sxs-lookup"><span data-stu-id="16bb5-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="16bb5-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="16bb5-137">FactSet</span></span> | <span data-ttu-id="16bb5-138">Adaptive. Facts, Adaptive. fact. title, Adaptive. fact. Value</span><span class="sxs-lookup"><span data-stu-id="16bb5-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="16bb5-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="16bb5-139">TextBlock</span></span>  | <span data-ttu-id="16bb5-140">Adaptive. TextBlock</span><span class="sxs-lookup"><span data-stu-id="16bb5-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="16bb5-141">Questo dizionario risorse XAML di esempio che imposta lo sfondo di tutti i TextBlock su Aqua.</span><span class="sxs-lookup"><span data-stu-id="16bb5-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="16bb5-142">È probabile che si desideri qualcosa di più avanzato😁</span><span class="sxs-lookup"><span data-stu-id="16bb5-142">You will probably want something more advanced than this 😁</span></span>

```xml
<ResourceDictionary
    xmlns="https://schemas.microsoft.com/winfx/2006/xaml/presentation" 
    xmlns:x="https://schemas.microsoft.com/winfx/2006/xaml">
    <Style x:Key="Adaptive.TextBlock" TargetType="TextBlock">
        <Setter Property="Background" Value="Aqua"></Setter>
    </Style>
</ResourceDictionary>
```
```csharp
// Use a ResourceDictionary instance
// DON'T use this property if rendering from a server
renderer.Resources = myResourceDictionary;

// ... or load it from a file path
// USE this if rendering from a server
renderer.ResourcesPath = <path-to-my-resource-dictionary.xaml>;
```

> [!IMPORTANT]
> <span data-ttu-id="16bb5-143">**Nota sulla generazione di immagini lato server** Il renderer WPF fornisce un `RenderCardToImageAsync` metodo che può essere utilizzato per la generazione di immagini sul lato server.</span><span class="sxs-lookup"><span data-stu-id="16bb5-143">**A note about server-side image generation** The WPF renderer provides a `RenderCardToImageAsync` method that can be used for server-side image generation.</span></span> <span data-ttu-id="16bb5-144">È necessario utilizzare la `ResourcesPath` proprietà solo se utilizzata in questo ambiente.</span><span class="sxs-lookup"><span data-stu-id="16bb5-144">You must only use the `ResourcesPath` property if used in this environment.</span></span> <span data-ttu-id="16bb5-145">Per ulteriori informazioni, vedere la documentazione per il [rendering delle immagini](../net-image/getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="16bb5-145">See the [Image Rendering](../net-image/getting-started.md) docs for more</span></span>