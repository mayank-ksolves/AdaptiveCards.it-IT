---
title: Stile nativo-.NET HTML SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 5b829d9eefe933f133c8532030856849802c5eb5
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454494"
---
# <a name="native-styling---net-html"></a><span data-ttu-id="4c85f-102">Stile nativo-HTML .NET</span><span class="sxs-lookup"><span data-stu-id="4c85f-102">Native styling - .NET HTML</span></span>

<span data-ttu-id="4c85f-103">Sebbene la configurazione host consentirà di ottenere la maggior parte delle piattaforme in ogni piattaforma, è probabile che sarà necessario eseguire alcuni stili nativi su ogni piattaforma.</span><span class="sxs-lookup"><span data-stu-id="4c85f-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="4c85f-104">HTML semplifica questa operazione aggiungendo classi CSS a ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="4c85f-104">HTML makes this easy by adding CSS classes to every element.</span></span>

| <span data-ttu-id="4c85f-105">Elemento</span><span class="sxs-lookup"><span data-stu-id="4c85f-105">Element</span></span> | <span data-ttu-id="4c85f-106">Classe CSS</span><span class="sxs-lookup"><span data-stu-id="4c85f-106">CSS class</span></span> |
|---|---|
| <span data-ttu-id="4c85f-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="4c85f-107">AdaptiveCard</span></span> | <span data-ttu-id="4c85f-108">AC-adaptivecard</span><span class="sxs-lookup"><span data-stu-id="4c85f-108">ac-adaptivecard</span></span> |
| <span data-ttu-id="4c85f-109">Tutte le azioni</span><span class="sxs-lookup"><span data-stu-id="4c85f-109">All Actions</span></span> | <span data-ttu-id="4c85f-110">ac-pushButton</span><span class="sxs-lookup"><span data-stu-id="4c85f-110">ac-pushButton</span></span> | 
| <span data-ttu-id="4c85f-111">Seleziona azioni</span><span class="sxs-lookup"><span data-stu-id="4c85f-111">Select Actions</span></span> | <span data-ttu-id="4c85f-112">AC-selezionabile</span><span class="sxs-lookup"><span data-stu-id="4c85f-112">ac-selectable</span></span> |
| <span data-ttu-id="4c85f-113">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="4c85f-113">Action.OpenUrl</span></span>  | <span data-ttu-id="4c85f-114">AC-Action-openUrl</span><span class="sxs-lookup"><span data-stu-id="4c85f-114">ac-action-openUrl</span></span> |
| <span data-ttu-id="4c85f-115">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="4c85f-115">Action.ShowCard</span></span> | <span data-ttu-id="4c85f-116">AC-Action-showCard</span><span class="sxs-lookup"><span data-stu-id="4c85f-116">ac-action-showCard</span></span> |
| <span data-ttu-id="4c85f-117">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="4c85f-117">Action.Submit</span></span>  | <span data-ttu-id="4c85f-118">CA-azione-Invia</span><span class="sxs-lookup"><span data-stu-id="4c85f-118">ac-action-submit</span></span>  |
| <span data-ttu-id="4c85f-119">ActionSet</span><span class="sxs-lookup"><span data-stu-id="4c85f-119">ActionSet</span></span> | <span data-ttu-id="4c85f-120">AC-actiont</span><span class="sxs-lookup"><span data-stu-id="4c85f-120">ac-actionset</span></span> |
| <span data-ttu-id="4c85f-121">Column</span><span class="sxs-lookup"><span data-stu-id="4c85f-121">Column</span></span> | <span data-ttu-id="4c85f-122">colonna AC</span><span class="sxs-lookup"><span data-stu-id="4c85f-122">ac-column</span></span> |
| <span data-ttu-id="4c85f-123">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="4c85f-123">ColumnSet</span></span> | <span data-ttu-id="4c85f-124">AC-columnstore</span><span class="sxs-lookup"><span data-stu-id="4c85f-124">ac-columnset</span></span> |
| <span data-ttu-id="4c85f-125">Contenitore</span><span class="sxs-lookup"><span data-stu-id="4c85f-125">Container</span></span> | <span data-ttu-id="4c85f-126">contenitore AC</span><span class="sxs-lookup"><span data-stu-id="4c85f-126">ac-container</span></span> |
| <span data-ttu-id="4c85f-127">Tutti gli input</span><span class="sxs-lookup"><span data-stu-id="4c85f-127">All Inputs</span></span> | <span data-ttu-id="4c85f-128">input AC</span><span class="sxs-lookup"><span data-stu-id="4c85f-128">ac-input</span></span> |
| <span data-ttu-id="4c85f-129">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="4c85f-129">Input.ChoiceSet</span></span> | <span data-ttu-id="4c85f-130">AC-multichoiceInput</span><span class="sxs-lookup"><span data-stu-id="4c85f-130">ac-multichoiceInput</span></span>  |
| <span data-ttu-id="4c85f-131">Input. Data</span><span class="sxs-lookup"><span data-stu-id="4c85f-131">Input.Date</span></span> | <span data-ttu-id="4c85f-132">AC-dateInput</span><span class="sxs-lookup"><span data-stu-id="4c85f-132">ac-dateInput</span></span> |
| <span data-ttu-id="4c85f-133">Input. Number</span><span class="sxs-lookup"><span data-stu-id="4c85f-133">Input.Number</span></span> | <span data-ttu-id="4c85f-134">AC-numberInput</span><span class="sxs-lookup"><span data-stu-id="4c85f-134">ac-numberInput</span></span> |
| <span data-ttu-id="4c85f-135">Input.Text</span><span class="sxs-lookup"><span data-stu-id="4c85f-135">Input.Text</span></span> | <span data-ttu-id="4c85f-136">ac-textInput</span><span class="sxs-lookup"><span data-stu-id="4c85f-136">ac-textInput</span></span> |
| <span data-ttu-id="4c85f-137">Input.Time</span><span class="sxs-lookup"><span data-stu-id="4c85f-137">Input.Time</span></span> | <span data-ttu-id="4c85f-138">AC-timeInput</span><span class="sxs-lookup"><span data-stu-id="4c85f-138">ac-timeInput</span></span> |
| <span data-ttu-id="4c85f-139">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="4c85f-139">Input.Toggle</span></span>| - |
| <span data-ttu-id="4c85f-140">Immagine</span><span class="sxs-lookup"><span data-stu-id="4c85f-140">Image</span></span>  | <span data-ttu-id="4c85f-141">AC-image</span><span class="sxs-lookup"><span data-stu-id="4c85f-141">ac-image</span></span> |
| <span data-ttu-id="4c85f-142">ImageSet</span><span class="sxs-lookup"><span data-stu-id="4c85f-142">ImageSet</span></span>  | <span data-ttu-id="4c85f-143">AC-imaget</span><span class="sxs-lookup"><span data-stu-id="4c85f-143">ac-imageset</span></span> |
| <span data-ttu-id="4c85f-144">FactSet</span><span class="sxs-lookup"><span data-stu-id="4c85f-144">FactSet</span></span> | <span data-ttu-id="4c85f-145">CA-fact</span><span class="sxs-lookup"><span data-stu-id="4c85f-145">ac-factset</span></span> |
| <span data-ttu-id="4c85f-146">TextBlock</span><span class="sxs-lookup"><span data-stu-id="4c85f-146">TextBlock</span></span>  | <span data-ttu-id="4c85f-147">AC-TextBlock</span><span class="sxs-lookup"><span data-stu-id="4c85f-147">ac-textblock</span></span> |