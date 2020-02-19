---
title: Stile nativo-UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 08/15/2018
ms.topic: article
ms.openlocfilehash: 565c61535adc5b316cb8b1f3ad77e511012e7612
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454044"
---
# <a name="native-styling---uwp"></a><span data-ttu-id="31b25-102">Stile nativo-UWP</span><span class="sxs-lookup"><span data-stu-id="31b25-102">Native styling - UWP</span></span>

<span data-ttu-id="31b25-103">Sebbene la configurazione host consentirà di ottenere la maggior parte delle piattaforme in ogni piattaforma, è probabile che sarà necessario eseguire alcuni stili nativi su ogni piattaforma.</span><span class="sxs-lookup"><span data-stu-id="31b25-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="31b25-104">UWP semplifica questa operazione consentendo di passare un oggetto ResourceDictionary per lo stile, il comportamento, le animazioni e così via.</span><span class="sxs-lookup"><span data-stu-id="31b25-104">UWP makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="31b25-105">Elemento</span><span class="sxs-lookup"><span data-stu-id="31b25-105">Element</span></span> | <span data-ttu-id="31b25-106">Nomi di stile</span><span class="sxs-lookup"><span data-stu-id="31b25-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="31b25-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="31b25-107">AdaptiveCard</span></span> | <span data-ttu-id="31b25-108">Adaptive. Card</span><span class="sxs-lookup"><span data-stu-id="31b25-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="31b25-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="31b25-109">Action.OpenUrl</span></span>  | <span data-ttu-id="31b25-110">Adaptive.Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="31b25-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="31b25-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="31b25-111">Action.ShowCard</span></span> | <span data-ttu-id="31b25-112">Adaptive.Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="31b25-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="31b25-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="31b25-113">Action.Submit</span></span>  | <span data-ttu-id="31b25-114">Adattivo. azione. Invia</span><span class="sxs-lookup"><span data-stu-id="31b25-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="31b25-115">Column</span><span class="sxs-lookup"><span data-stu-id="31b25-115">Column</span></span> | <span data-ttu-id="31b25-116">Adaptive. Column, Adaptive. Action. Tap</span><span class="sxs-lookup"><span data-stu-id="31b25-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="31b25-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="31b25-117">ColumnSet</span></span> | <span data-ttu-id="31b25-118">Adaptive. ColumnStore, Adaptive. VerticalSeparator</span><span class="sxs-lookup"><span data-stu-id="31b25-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="31b25-119">Contenitore</span><span class="sxs-lookup"><span data-stu-id="31b25-119">Container</span></span> | <span data-ttu-id="31b25-120">Adaptive. container</span><span class="sxs-lookup"><span data-stu-id="31b25-120">Adaptive.Container</span></span>|
| <span data-ttu-id="31b25-121">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="31b25-121">Input.ChoiceSet</span></span> | <span data-ttu-id="31b25-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="31b25-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="31b25-123">Input. Data</span><span class="sxs-lookup"><span data-stu-id="31b25-123">Input.Date</span></span> | <span data-ttu-id="31b25-124">Adaptive.Input.Text.Date</span><span class="sxs-lookup"><span data-stu-id="31b25-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="31b25-125">Input. Number</span><span class="sxs-lookup"><span data-stu-id="31b25-125">Input.Number</span></span> | <span data-ttu-id="31b25-126">Adaptive.Input.Text.Number</span><span class="sxs-lookup"><span data-stu-id="31b25-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="31b25-127">Input.Text</span><span class="sxs-lookup"><span data-stu-id="31b25-127">Input.Text</span></span> | <span data-ttu-id="31b25-128">Adaptive.Input.Text</span><span class="sxs-lookup"><span data-stu-id="31b25-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="31b25-129">Input.Time</span><span class="sxs-lookup"><span data-stu-id="31b25-129">Input.Time</span></span> | <span data-ttu-id="31b25-130">Adaptive.Input.Text.Time</span><span class="sxs-lookup"><span data-stu-id="31b25-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="31b25-131">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="31b25-131">Input.Toggle</span></span>| <span data-ttu-id="31b25-132">Adaptive. input. Attiva/Nascondi</span><span class="sxs-lookup"><span data-stu-id="31b25-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="31b25-133">Immagine</span><span class="sxs-lookup"><span data-stu-id="31b25-133">Image</span></span>  | <span data-ttu-id="31b25-134">Adaptive. image</span><span class="sxs-lookup"><span data-stu-id="31b25-134">Adaptive.Image</span></span> |
| <span data-ttu-id="31b25-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="31b25-135">ImageSet</span></span>  | <span data-ttu-id="31b25-136">Adaptive.ImageSet</span><span class="sxs-lookup"><span data-stu-id="31b25-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="31b25-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="31b25-137">FactSet</span></span> | <span data-ttu-id="31b25-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span><span class="sxs-lookup"><span data-stu-id="31b25-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="31b25-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="31b25-139">TextBlock</span></span>  | <span data-ttu-id="31b25-140">Adaptive.TextBlock</span><span class="sxs-lookup"><span data-stu-id="31b25-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="31b25-141">Questo dizionario risorse XAML di esempio che imposta lo sfondo di tutti i TextBlock su Aqua.</span><span class="sxs-lookup"><span data-stu-id="31b25-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="31b25-142">È probabile che si desideri una soluzione più avanzata rispetto a questa 😁</span><span class="sxs-lookup"><span data-stu-id="31b25-142">You will probably want something more advanced than this 😁</span></span>

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
```
