---
title: Stile nativo-UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 08/15/2018
ms.topic: article
ms.openlocfilehash: da3c7616ce4fe307eda3073f7037842e3e3df81b
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417521"
---
# <a name="native-styling---uwp"></a><span data-ttu-id="88df8-102">Stile nativo-UWP</span><span class="sxs-lookup"><span data-stu-id="88df8-102">Native styling - UWP</span></span>

<span data-ttu-id="88df8-103">Sebbene la configurazione host consentirà di ottenere la maggior parte delle piattaforme in ogni piattaforma, è probabile che sarà necessario eseguire alcuni stili nativi su ogni piattaforma.</span><span class="sxs-lookup"><span data-stu-id="88df8-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="88df8-104">UWP semplifica questa operazione consentendo di passare un oggetto ResourceDictionary per lo stile, il comportamento, le animazioni e così via.</span><span class="sxs-lookup"><span data-stu-id="88df8-104">UWP makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="88df8-105">Elemento</span><span class="sxs-lookup"><span data-stu-id="88df8-105">Element</span></span> | <span data-ttu-id="88df8-106">Nomi di stile</span><span class="sxs-lookup"><span data-stu-id="88df8-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="88df8-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="88df8-107">AdaptiveCard</span></span> | <span data-ttu-id="88df8-108">Adaptive. Card</span><span class="sxs-lookup"><span data-stu-id="88df8-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="88df8-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="88df8-109">Action.OpenUrl</span></span>  | <span data-ttu-id="88df8-110">Adaptive. Action. OpenUrl</span><span class="sxs-lookup"><span data-stu-id="88df8-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="88df8-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="88df8-111">Action.ShowCard</span></span> | <span data-ttu-id="88df8-112">Adaptive. Action. ShowCard</span><span class="sxs-lookup"><span data-stu-id="88df8-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="88df8-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="88df8-113">Action.Submit</span></span>  | <span data-ttu-id="88df8-114">Adattivo. azione. Invia</span><span class="sxs-lookup"><span data-stu-id="88df8-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="88df8-115">Colonna</span><span class="sxs-lookup"><span data-stu-id="88df8-115">Column</span></span> | <span data-ttu-id="88df8-116">Adaptive. Column, Adaptive. Action. Tap</span><span class="sxs-lookup"><span data-stu-id="88df8-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="88df8-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="88df8-117">ColumnSet</span></span> | <span data-ttu-id="88df8-118">Adaptive. ColumnStore, Adaptive. VerticalSeparator</span><span class="sxs-lookup"><span data-stu-id="88df8-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="88df8-119">Contenitore</span><span class="sxs-lookup"><span data-stu-id="88df8-119">Container</span></span> | <span data-ttu-id="88df8-120">Adaptive. container</span><span class="sxs-lookup"><span data-stu-id="88df8-120">Adaptive.Container</span></span>|
| <span data-ttu-id="88df8-121">Input. Choices</span><span class="sxs-lookup"><span data-stu-id="88df8-121">Input.ChoiceSet</span></span> | <span data-ttu-id="88df8-122">Adaptive. input. Choices, Adaptive. input. Choices. ComboBox, Adaptive. input. Choicet. CheckBox, Adaptive. input. Choicet. Radio, Adaptive. input. Choices. ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="88df8-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="88df8-123">Input. Data</span><span class="sxs-lookup"><span data-stu-id="88df8-123">Input.Date</span></span> | <span data-ttu-id="88df8-124">Adaptive. input. Text. date</span><span class="sxs-lookup"><span data-stu-id="88df8-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="88df8-125">Input. Number</span><span class="sxs-lookup"><span data-stu-id="88df8-125">Input.Number</span></span> | <span data-ttu-id="88df8-126">Adaptive. input. Text. Number</span><span class="sxs-lookup"><span data-stu-id="88df8-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="88df8-127">Input. Text</span><span class="sxs-lookup"><span data-stu-id="88df8-127">Input.Text</span></span> | <span data-ttu-id="88df8-128">Adaptive. input. Text</span><span class="sxs-lookup"><span data-stu-id="88df8-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="88df8-129">Input. Time</span><span class="sxs-lookup"><span data-stu-id="88df8-129">Input.Time</span></span> | <span data-ttu-id="88df8-130">Adaptive. input. Text. Time</span><span class="sxs-lookup"><span data-stu-id="88df8-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="88df8-131">Input. interruttore</span><span class="sxs-lookup"><span data-stu-id="88df8-131">Input.Toggle</span></span>| <span data-ttu-id="88df8-132">Adaptive. input. Attiva/Nascondi</span><span class="sxs-lookup"><span data-stu-id="88df8-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="88df8-133">Immagine</span><span class="sxs-lookup"><span data-stu-id="88df8-133">Image</span></span>  | <span data-ttu-id="88df8-134">Adaptive. image</span><span class="sxs-lookup"><span data-stu-id="88df8-134">Adaptive.Image</span></span> |
| <span data-ttu-id="88df8-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="88df8-135">ImageSet</span></span>  | <span data-ttu-id="88df8-136">Adaptive. images</span><span class="sxs-lookup"><span data-stu-id="88df8-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="88df8-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="88df8-137">FactSet</span></span> | <span data-ttu-id="88df8-138">Adaptive. Facts, Adaptive. fact. title, Adaptive. fact. Value</span><span class="sxs-lookup"><span data-stu-id="88df8-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="88df8-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="88df8-139">TextBlock</span></span>  | <span data-ttu-id="88df8-140">Adaptive. TextBlock</span><span class="sxs-lookup"><span data-stu-id="88df8-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="88df8-141">Questo dizionario risorse XAML di esempio che imposta lo sfondo di tutti i TextBlock su Aqua.</span><span class="sxs-lookup"><span data-stu-id="88df8-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="88df8-142">È probabile che si desideri qualcosa di più avanzato😁</span><span class="sxs-lookup"><span data-stu-id="88df8-142">You will probably want something more advanced than this 😁</span></span>

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
```
