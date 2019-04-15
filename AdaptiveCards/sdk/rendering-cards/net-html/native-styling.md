---
title: Stile nativo - HTML .NET SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 620940dee873742898d58979c61827320bc3c202
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552563"
---
# <a name="native-styling---net-html"></a><span data-ttu-id="f9640-102">Stile nativo - .NET HTML</span><span class="sxs-lookup"><span data-stu-id="f9640-102">Native styling - .NET HTML</span></span>

<span data-ttu-id="f9640-103">Mentre Host Config consente di iniziare la maggior parte dei casi in ogni piattaforma, è probabile che si dovrà eseguire alcune stile nativo in ogni piattaforma.</span><span class="sxs-lookup"><span data-stu-id="f9640-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="f9640-104">HTML semplifica questa attività mediante l'aggiunta di classi CSS a ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="f9640-104">HTML makes this easy by adding CSS classes to every element.</span></span>

| <span data-ttu-id="f9640-105">Elemento</span><span class="sxs-lookup"><span data-stu-id="f9640-105">Element</span></span> | <span data-ttu-id="f9640-106">Classe CSS</span><span class="sxs-lookup"><span data-stu-id="f9640-106">CSS class</span></span> |
|---|---|
| <span data-ttu-id="f9640-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="f9640-107">AdaptiveCard</span></span> | <span data-ttu-id="f9640-108">ac-adaptivecard</span><span class="sxs-lookup"><span data-stu-id="f9640-108">ac-adaptivecard</span></span> |
| <span data-ttu-id="f9640-109">Tutte le azioni</span><span class="sxs-lookup"><span data-stu-id="f9640-109">All Actions</span></span> | <span data-ttu-id="f9640-110">ac-pushButton</span><span class="sxs-lookup"><span data-stu-id="f9640-110">ac-pushButton</span></span> | 
| <span data-ttu-id="f9640-111">Selezionare le azioni</span><span class="sxs-lookup"><span data-stu-id="f9640-111">Select Actions</span></span> | <span data-ttu-id="f9640-112">AC-selezionabili</span><span class="sxs-lookup"><span data-stu-id="f9640-112">ac-selectable</span></span> |
| <span data-ttu-id="f9640-113">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="f9640-113">Action.OpenUrl</span></span>  | <span data-ttu-id="f9640-114">ac-action-openUrl</span><span class="sxs-lookup"><span data-stu-id="f9640-114">ac-action-openUrl</span></span> |
| <span data-ttu-id="f9640-115">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="f9640-115">Action.ShowCard</span></span> | <span data-ttu-id="f9640-116">ac-action-showCard</span><span class="sxs-lookup"><span data-stu-id="f9640-116">ac-action-showCard</span></span> |
| <span data-ttu-id="f9640-117">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="f9640-117">Action.Submit</span></span>  | <span data-ttu-id="f9640-118">ac-action-submit</span><span class="sxs-lookup"><span data-stu-id="f9640-118">ac-action-submit</span></span>  |
| <span data-ttu-id="f9640-119">ActionSet</span><span class="sxs-lookup"><span data-stu-id="f9640-119">ActionSet</span></span> | <span data-ttu-id="f9640-120">ac-actionset</span><span class="sxs-lookup"><span data-stu-id="f9640-120">ac-actionset</span></span> |
| <span data-ttu-id="f9640-121">Column</span><span class="sxs-lookup"><span data-stu-id="f9640-121">Column</span></span> | <span data-ttu-id="f9640-122">AC-colonna</span><span class="sxs-lookup"><span data-stu-id="f9640-122">ac-column</span></span> |
| <span data-ttu-id="f9640-123">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="f9640-123">ColumnSet</span></span> | <span data-ttu-id="f9640-124">AC-columnset</span><span class="sxs-lookup"><span data-stu-id="f9640-124">ac-columnset</span></span> |
| <span data-ttu-id="f9640-125">Contenitore</span><span class="sxs-lookup"><span data-stu-id="f9640-125">Container</span></span> | <span data-ttu-id="f9640-126">AC-container</span><span class="sxs-lookup"><span data-stu-id="f9640-126">ac-container</span></span> |
| <span data-ttu-id="f9640-127">Tutti gli input</span><span class="sxs-lookup"><span data-stu-id="f9640-127">All Inputs</span></span> | <span data-ttu-id="f9640-128">ac-input</span><span class="sxs-lookup"><span data-stu-id="f9640-128">ac-input</span></span> |
| <span data-ttu-id="f9640-129">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="f9640-129">Input.ChoiceSet</span></span> | <span data-ttu-id="f9640-130">ac-multichoiceInput</span><span class="sxs-lookup"><span data-stu-id="f9640-130">ac-multichoiceInput</span></span>  |
| <span data-ttu-id="f9640-131">Input.Date</span><span class="sxs-lookup"><span data-stu-id="f9640-131">Input.Date</span></span> | <span data-ttu-id="f9640-132">ac-dateInput</span><span class="sxs-lookup"><span data-stu-id="f9640-132">ac-dateInput</span></span> |
| <span data-ttu-id="f9640-133">Input.Number</span><span class="sxs-lookup"><span data-stu-id="f9640-133">Input.Number</span></span> | <span data-ttu-id="f9640-134">ac-numberInput</span><span class="sxs-lookup"><span data-stu-id="f9640-134">ac-numberInput</span></span> |
| <span data-ttu-id="f9640-135">Input.Text</span><span class="sxs-lookup"><span data-stu-id="f9640-135">Input.Text</span></span> | <span data-ttu-id="f9640-136">ac-textInput</span><span class="sxs-lookup"><span data-stu-id="f9640-136">ac-textInput</span></span> |
| <span data-ttu-id="f9640-137">Input.Time</span><span class="sxs-lookup"><span data-stu-id="f9640-137">Input.Time</span></span> | <span data-ttu-id="f9640-138">ac-timeInput</span><span class="sxs-lookup"><span data-stu-id="f9640-138">ac-timeInput</span></span> |
| <span data-ttu-id="f9640-139">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="f9640-139">Input.Toggle</span></span>| - |
| <span data-ttu-id="f9640-140">Image</span><span class="sxs-lookup"><span data-stu-id="f9640-140">Image</span></span>  | <span data-ttu-id="f9640-141">AC-image</span><span class="sxs-lookup"><span data-stu-id="f9640-141">ac-image</span></span> |
| <span data-ttu-id="f9640-142">ImageSet</span><span class="sxs-lookup"><span data-stu-id="f9640-142">ImageSet</span></span>  | <span data-ttu-id="f9640-143">AC-imageset</span><span class="sxs-lookup"><span data-stu-id="f9640-143">ac-imageset</span></span> |
| <span data-ttu-id="f9640-144">FactSet</span><span class="sxs-lookup"><span data-stu-id="f9640-144">FactSet</span></span> | <span data-ttu-id="f9640-145">ac-factset</span><span class="sxs-lookup"><span data-stu-id="f9640-145">ac-factset</span></span> |
| <span data-ttu-id="f9640-146">TextBlock</span><span class="sxs-lookup"><span data-stu-id="f9640-146">TextBlock</span></span>  | <span data-ttu-id="f9640-147">ac-textblock</span><span class="sxs-lookup"><span data-stu-id="f9640-147">ac-textblock</span></span> |