---
title: Stile nativo-.NET WPF SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 204845f942be4e7d04e20e9cd64d826daef26e93
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454024"
---
# <a name="native-styling---net-wpf"></a><span data-ttu-id="9fad7-102">Stile nativo-WPF .NET</span><span class="sxs-lookup"><span data-stu-id="9fad7-102">Native styling - .NET WPF</span></span>

<span data-ttu-id="9fad7-103">Sebbene la configurazione host consentirà di ottenere la maggior parte delle piattaforme in ogni piattaforma, è probabile che sarà necessario eseguire alcuni stili nativi su ogni piattaforma.</span><span class="sxs-lookup"><span data-stu-id="9fad7-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="9fad7-104">WPF semplifica questa operazione consentendo di passare un oggetto ResourceDictionary per lo stile, il comportamento, le animazioni e così via.</span><span class="sxs-lookup"><span data-stu-id="9fad7-104">WPF makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="9fad7-105">Elemento</span><span class="sxs-lookup"><span data-stu-id="9fad7-105">Element</span></span> | <span data-ttu-id="9fad7-106">Nomi di stile</span><span class="sxs-lookup"><span data-stu-id="9fad7-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="9fad7-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="9fad7-107">AdaptiveCard</span></span> | <span data-ttu-id="9fad7-108">Adaptive. Card</span><span class="sxs-lookup"><span data-stu-id="9fad7-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="9fad7-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="9fad7-109">Action.OpenUrl</span></span>  | <span data-ttu-id="9fad7-110">Adaptive.Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="9fad7-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="9fad7-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="9fad7-111">Action.ShowCard</span></span> | <span data-ttu-id="9fad7-112">Adaptive.Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="9fad7-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="9fad7-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="9fad7-113">Action.Submit</span></span>  | <span data-ttu-id="9fad7-114">Adattivo. azione. Invia</span><span class="sxs-lookup"><span data-stu-id="9fad7-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="9fad7-115">Column</span><span class="sxs-lookup"><span data-stu-id="9fad7-115">Column</span></span> | <span data-ttu-id="9fad7-116">Adaptive. Column, Adaptive. Action. Tap</span><span class="sxs-lookup"><span data-stu-id="9fad7-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="9fad7-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="9fad7-117">ColumnSet</span></span> | <span data-ttu-id="9fad7-118">Adaptive. ColumnStore, Adaptive. VerticalSeparator</span><span class="sxs-lookup"><span data-stu-id="9fad7-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="9fad7-119">Contenitore</span><span class="sxs-lookup"><span data-stu-id="9fad7-119">Container</span></span> | <span data-ttu-id="9fad7-120">Adaptive. container</span><span class="sxs-lookup"><span data-stu-id="9fad7-120">Adaptive.Container</span></span>|
| <span data-ttu-id="9fad7-121">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="9fad7-121">Input.ChoiceSet</span></span> | <span data-ttu-id="9fad7-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="9fad7-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="9fad7-123">Input. Data</span><span class="sxs-lookup"><span data-stu-id="9fad7-123">Input.Date</span></span> | <span data-ttu-id="9fad7-124">Adaptive.Input.Text.Date</span><span class="sxs-lookup"><span data-stu-id="9fad7-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="9fad7-125">Input. Number</span><span class="sxs-lookup"><span data-stu-id="9fad7-125">Input.Number</span></span> | <span data-ttu-id="9fad7-126">Adaptive.Input.Text.Number</span><span class="sxs-lookup"><span data-stu-id="9fad7-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="9fad7-127">Input.Text</span><span class="sxs-lookup"><span data-stu-id="9fad7-127">Input.Text</span></span> | <span data-ttu-id="9fad7-128">Adaptive.Input.Text</span><span class="sxs-lookup"><span data-stu-id="9fad7-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="9fad7-129">Input.Time</span><span class="sxs-lookup"><span data-stu-id="9fad7-129">Input.Time</span></span> | <span data-ttu-id="9fad7-130">Adaptive.Input.Text.Time</span><span class="sxs-lookup"><span data-stu-id="9fad7-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="9fad7-131">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="9fad7-131">Input.Toggle</span></span>| <span data-ttu-id="9fad7-132">Adaptive. input. Attiva/Nascondi</span><span class="sxs-lookup"><span data-stu-id="9fad7-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="9fad7-133">Immagine</span><span class="sxs-lookup"><span data-stu-id="9fad7-133">Image</span></span>  | <span data-ttu-id="9fad7-134">Adaptive. image</span><span class="sxs-lookup"><span data-stu-id="9fad7-134">Adaptive.Image</span></span> |
| <span data-ttu-id="9fad7-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="9fad7-135">ImageSet</span></span>  | <span data-ttu-id="9fad7-136">Adaptive.ImageSet</span><span class="sxs-lookup"><span data-stu-id="9fad7-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="9fad7-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="9fad7-137">FactSet</span></span> | <span data-ttu-id="9fad7-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span><span class="sxs-lookup"><span data-stu-id="9fad7-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="9fad7-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="9fad7-139">TextBlock</span></span>  | <span data-ttu-id="9fad7-140">Adaptive.TextBlock</span><span class="sxs-lookup"><span data-stu-id="9fad7-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="9fad7-141">Questo dizionario risorse XAML di esempio che imposta lo sfondo di tutti i TextBlock su Aqua.</span><span class="sxs-lookup"><span data-stu-id="9fad7-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="9fad7-142">È probabile che si desideri una soluzione più avanzata rispetto a questa 😁</span><span class="sxs-lookup"><span data-stu-id="9fad7-142">You will probably want something more advanced than this 😁</span></span>

```xml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" 
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
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
> <span data-ttu-id="9fad7-143">**Nota sulla generazione di immagini lato server** Il renderer WPF fornisce un metodo di `RenderCardToImageAsync` che può essere utilizzato per la generazione di immagini lato server.</span><span class="sxs-lookup"><span data-stu-id="9fad7-143">**A note about server-side image generation** The WPF renderer provides a `RenderCardToImageAsync` method that can be used for server-side image generation.</span></span> <span data-ttu-id="9fad7-144">È necessario utilizzare la proprietà `ResourcesPath` solo se utilizzata in questo ambiente.</span><span class="sxs-lookup"><span data-stu-id="9fad7-144">You must only use the `ResourcesPath` property if used in this environment.</span></span> <span data-ttu-id="9fad7-145">Per ulteriori informazioni, vedere la documentazione per il [rendering delle immagini](../net-image/getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="9fad7-145">See the [Image Rendering](../net-image/getting-started.md) docs for more</span></span>