---
title: Stile nativo - WPF .NET SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: ee5bec1a11f39ad69d40e57410c105b50ba45981
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552723"
---
# <a name="native-styling---net-wpf"></a><span data-ttu-id="d1d66-102">Stile nativo - WPF .NET</span><span class="sxs-lookup"><span data-stu-id="d1d66-102">Native styling - .NET WPF</span></span>

<span data-ttu-id="d1d66-103">Mentre Host Config consente di iniziare la maggior parte dei casi in ogni piattaforma, è probabile che si dovrà eseguire alcune stile nativo in ogni piattaforma.</span><span class="sxs-lookup"><span data-stu-id="d1d66-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="d1d66-104">WPF semplifica questa attività, consentendo di passare un oggetto ResourceDictionary per lo stile con granularità fine, il comportamento, animazioni e così via.</span><span class="sxs-lookup"><span data-stu-id="d1d66-104">WPF makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="d1d66-105">Elemento</span><span class="sxs-lookup"><span data-stu-id="d1d66-105">Element</span></span> | <span data-ttu-id="d1d66-106">Nomi degli stili</span><span class="sxs-lookup"><span data-stu-id="d1d66-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="d1d66-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="d1d66-107">AdaptiveCard</span></span> | <span data-ttu-id="d1d66-108">Adaptive.Card</span><span class="sxs-lookup"><span data-stu-id="d1d66-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="d1d66-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="d1d66-109">Action.OpenUrl</span></span>  | <span data-ttu-id="d1d66-110">Adaptive.Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="d1d66-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="d1d66-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="d1d66-111">Action.ShowCard</span></span> | <span data-ttu-id="d1d66-112">Adaptive.Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="d1d66-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="d1d66-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="d1d66-113">Action.Submit</span></span>  | <span data-ttu-id="d1d66-114">Adaptive.Action.Submit</span><span class="sxs-lookup"><span data-stu-id="d1d66-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="d1d66-115">Column</span><span class="sxs-lookup"><span data-stu-id="d1d66-115">Column</span></span> | <span data-ttu-id="d1d66-116">Adaptive.Column, Adaptive.Action.Tap</span><span class="sxs-lookup"><span data-stu-id="d1d66-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="d1d66-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="d1d66-117">ColumnSet</span></span> | <span data-ttu-id="d1d66-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span><span class="sxs-lookup"><span data-stu-id="d1d66-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="d1d66-119">Contenitore</span><span class="sxs-lookup"><span data-stu-id="d1d66-119">Container</span></span> | <span data-ttu-id="d1d66-120">Adaptive.Container</span><span class="sxs-lookup"><span data-stu-id="d1d66-120">Adaptive.Container</span></span>|
| <span data-ttu-id="d1d66-121">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="d1d66-121">Input.ChoiceSet</span></span> | <span data-ttu-id="d1d66-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="d1d66-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="d1d66-123">Input.Date</span><span class="sxs-lookup"><span data-stu-id="d1d66-123">Input.Date</span></span> | <span data-ttu-id="d1d66-124">Adaptive.Input.Text.Date</span><span class="sxs-lookup"><span data-stu-id="d1d66-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="d1d66-125">Input.Number</span><span class="sxs-lookup"><span data-stu-id="d1d66-125">Input.Number</span></span> | <span data-ttu-id="d1d66-126">Adaptive.Input.Text.Number</span><span class="sxs-lookup"><span data-stu-id="d1d66-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="d1d66-127">Input.Text</span><span class="sxs-lookup"><span data-stu-id="d1d66-127">Input.Text</span></span> | <span data-ttu-id="d1d66-128">Adaptive.Input.Text</span><span class="sxs-lookup"><span data-stu-id="d1d66-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="d1d66-129">Input.Time</span><span class="sxs-lookup"><span data-stu-id="d1d66-129">Input.Time</span></span> | <span data-ttu-id="d1d66-130">Adaptive.Input.Text.Time</span><span class="sxs-lookup"><span data-stu-id="d1d66-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="d1d66-131">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="d1d66-131">Input.Toggle</span></span>| <span data-ttu-id="d1d66-132">Adaptive.Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="d1d66-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="d1d66-133">Image</span><span class="sxs-lookup"><span data-stu-id="d1d66-133">Image</span></span>  | <span data-ttu-id="d1d66-134">Adaptive.Image</span><span class="sxs-lookup"><span data-stu-id="d1d66-134">Adaptive.Image</span></span> |
| <span data-ttu-id="d1d66-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="d1d66-135">ImageSet</span></span>  | <span data-ttu-id="d1d66-136">Adaptive.ImageSet</span><span class="sxs-lookup"><span data-stu-id="d1d66-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="d1d66-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="d1d66-137">FactSet</span></span> | <span data-ttu-id="d1d66-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span><span class="sxs-lookup"><span data-stu-id="d1d66-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="d1d66-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="d1d66-139">TextBlock</span></span>  | <span data-ttu-id="d1d66-140">Adaptive.TextBlock</span><span class="sxs-lookup"><span data-stu-id="d1d66-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="d1d66-141">Questo dizionario risorse XAML di esempio che imposta lo sfondo del TextBlock tutte su azzurro.</span><span class="sxs-lookup"><span data-stu-id="d1d66-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="d1d66-142">Probabilmente si desidererà che qualcosa di più avanzate rispetto a questo 😁</span><span class="sxs-lookup"><span data-stu-id="d1d66-142">You will probably want something more advanced than this 😁</span></span>

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
> <span data-ttu-id="d1d66-143">**Nota sulla generazione di immagini server-side** renderer di WPF offre un `RenderCardToImageAsync` metodo che può essere utilizzato per la generazione di immagine sul lato server.</span><span class="sxs-lookup"><span data-stu-id="d1d66-143">**A note about server-side image generation** The WPF renderer provides a `RenderCardToImageAsync` method that can be used for server-side image generation.</span></span> <span data-ttu-id="d1d66-144">È necessario utilizzare solo il `ResourcesPath` proprietà se usati in questo ambiente.</span><span class="sxs-lookup"><span data-stu-id="d1d66-144">You must only use the `ResourcesPath` property if used in this environment.</span></span> <span data-ttu-id="d1d66-145">Vedere le [Rendering di immagini](../net-image/getting-started.md) docs per altre informazioni</span><span class="sxs-lookup"><span data-stu-id="d1d66-145">See the [Image Rendering](../net-image/getting-started.md) docs for more</span></span>