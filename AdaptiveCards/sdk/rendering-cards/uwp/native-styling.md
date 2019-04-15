---
title: Stile nativo - UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 08/15/2018
ms.topic: article
ms.openlocfilehash: da3b95dc53c55c81fbbbbed6ee7605f86eb427a9
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552523"
---
# <a name="native-styling---uwp"></a><span data-ttu-id="dfe0d-102">Stile nativo - UWP</span><span class="sxs-lookup"><span data-stu-id="dfe0d-102">Native styling - UWP</span></span>

<span data-ttu-id="dfe0d-103">Mentre Host Config consente di iniziare la maggior parte dei casi in ogni piattaforma, è probabile che si dovrà eseguire alcune stile nativo in ogni piattaforma.</span><span class="sxs-lookup"><span data-stu-id="dfe0d-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="dfe0d-104">Piattaforma UWP è semplice in quanto consente di passare un oggetto ResourceDictionary per lo stile con granularità fine, il comportamento, animazioni e così via.</span><span class="sxs-lookup"><span data-stu-id="dfe0d-104">UWP makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="dfe0d-105">Elemento</span><span class="sxs-lookup"><span data-stu-id="dfe0d-105">Element</span></span> | <span data-ttu-id="dfe0d-106">Nomi degli stili</span><span class="sxs-lookup"><span data-stu-id="dfe0d-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="dfe0d-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="dfe0d-107">AdaptiveCard</span></span> | <span data-ttu-id="dfe0d-108">Adaptive.Card</span><span class="sxs-lookup"><span data-stu-id="dfe0d-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="dfe0d-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="dfe0d-109">Action.OpenUrl</span></span>  | <span data-ttu-id="dfe0d-110">Adaptive.Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="dfe0d-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="dfe0d-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="dfe0d-111">Action.ShowCard</span></span> | <span data-ttu-id="dfe0d-112">Adaptive.Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="dfe0d-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="dfe0d-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="dfe0d-113">Action.Submit</span></span>  | <span data-ttu-id="dfe0d-114">Adaptive.Action.Submit</span><span class="sxs-lookup"><span data-stu-id="dfe0d-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="dfe0d-115">Column</span><span class="sxs-lookup"><span data-stu-id="dfe0d-115">Column</span></span> | <span data-ttu-id="dfe0d-116">Adaptive.Column, Adaptive.Action.Tap</span><span class="sxs-lookup"><span data-stu-id="dfe0d-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="dfe0d-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="dfe0d-117">ColumnSet</span></span> | <span data-ttu-id="dfe0d-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span><span class="sxs-lookup"><span data-stu-id="dfe0d-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="dfe0d-119">Contenitore</span><span class="sxs-lookup"><span data-stu-id="dfe0d-119">Container</span></span> | <span data-ttu-id="dfe0d-120">Adaptive.Container</span><span class="sxs-lookup"><span data-stu-id="dfe0d-120">Adaptive.Container</span></span>|
| <span data-ttu-id="dfe0d-121">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="dfe0d-121">Input.ChoiceSet</span></span> | <span data-ttu-id="dfe0d-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="dfe0d-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="dfe0d-123">Input.Date</span><span class="sxs-lookup"><span data-stu-id="dfe0d-123">Input.Date</span></span> | <span data-ttu-id="dfe0d-124">Adaptive.Input.Text.Date</span><span class="sxs-lookup"><span data-stu-id="dfe0d-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="dfe0d-125">Input.Number</span><span class="sxs-lookup"><span data-stu-id="dfe0d-125">Input.Number</span></span> | <span data-ttu-id="dfe0d-126">Adaptive.Input.Text.Number</span><span class="sxs-lookup"><span data-stu-id="dfe0d-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="dfe0d-127">Input.Text</span><span class="sxs-lookup"><span data-stu-id="dfe0d-127">Input.Text</span></span> | <span data-ttu-id="dfe0d-128">Adaptive.Input.Text</span><span class="sxs-lookup"><span data-stu-id="dfe0d-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="dfe0d-129">Input.Time</span><span class="sxs-lookup"><span data-stu-id="dfe0d-129">Input.Time</span></span> | <span data-ttu-id="dfe0d-130">Adaptive.Input.Text.Time</span><span class="sxs-lookup"><span data-stu-id="dfe0d-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="dfe0d-131">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="dfe0d-131">Input.Toggle</span></span>| <span data-ttu-id="dfe0d-132">Adaptive.Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="dfe0d-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="dfe0d-133">Image</span><span class="sxs-lookup"><span data-stu-id="dfe0d-133">Image</span></span>  | <span data-ttu-id="dfe0d-134">Adaptive.Image</span><span class="sxs-lookup"><span data-stu-id="dfe0d-134">Adaptive.Image</span></span> |
| <span data-ttu-id="dfe0d-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="dfe0d-135">ImageSet</span></span>  | <span data-ttu-id="dfe0d-136">Adaptive.ImageSet</span><span class="sxs-lookup"><span data-stu-id="dfe0d-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="dfe0d-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="dfe0d-137">FactSet</span></span> | <span data-ttu-id="dfe0d-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span><span class="sxs-lookup"><span data-stu-id="dfe0d-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="dfe0d-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="dfe0d-139">TextBlock</span></span>  | <span data-ttu-id="dfe0d-140">Adaptive.TextBlock</span><span class="sxs-lookup"><span data-stu-id="dfe0d-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="dfe0d-141">Questo dizionario risorse XAML di esempio che imposta lo sfondo del TextBlock tutte su azzurro.</span><span class="sxs-lookup"><span data-stu-id="dfe0d-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="dfe0d-142">Probabilmente si desidererà che qualcosa di più avanzate rispetto a questo 😁</span><span class="sxs-lookup"><span data-stu-id="dfe0d-142">You will probably want something more advanced than this 😁</span></span>

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
