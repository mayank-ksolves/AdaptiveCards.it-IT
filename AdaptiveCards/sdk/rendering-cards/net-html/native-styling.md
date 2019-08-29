---
title: Stile nativo-.NET HTML SDK
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
# <a name="native-styling---net-html"></a><span data-ttu-id="d162a-102">Stile nativo-HTML .NET</span><span class="sxs-lookup"><span data-stu-id="d162a-102">Native styling - .NET HTML</span></span>

<span data-ttu-id="d162a-103">Sebbene la configurazione host consentirà di ottenere la maggior parte delle piattaforme in ogni piattaforma, è probabile che sarà necessario eseguire alcuni stili nativi su ogni piattaforma.</span><span class="sxs-lookup"><span data-stu-id="d162a-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="d162a-104">HTML semplifica questa operazione aggiungendo classi CSS a ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="d162a-104">HTML makes this easy by adding CSS classes to every element.</span></span>

| <span data-ttu-id="d162a-105">Elemento</span><span class="sxs-lookup"><span data-stu-id="d162a-105">Element</span></span> | <span data-ttu-id="d162a-106">Classe CSS</span><span class="sxs-lookup"><span data-stu-id="d162a-106">CSS class</span></span> |
|---|---|
| <span data-ttu-id="d162a-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="d162a-107">AdaptiveCard</span></span> | <span data-ttu-id="d162a-108">AC-adaptivecard</span><span class="sxs-lookup"><span data-stu-id="d162a-108">ac-adaptivecard</span></span> |
| <span data-ttu-id="d162a-109">Tutte le azioni</span><span class="sxs-lookup"><span data-stu-id="d162a-109">All Actions</span></span> | <span data-ttu-id="d162a-110">ac-pushButton</span><span class="sxs-lookup"><span data-stu-id="d162a-110">ac-pushButton</span></span> | 
| <span data-ttu-id="d162a-111">Seleziona azioni</span><span class="sxs-lookup"><span data-stu-id="d162a-111">Select Actions</span></span> | <span data-ttu-id="d162a-112">AC-selezionabile</span><span class="sxs-lookup"><span data-stu-id="d162a-112">ac-selectable</span></span> |
| <span data-ttu-id="d162a-113">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="d162a-113">Action.OpenUrl</span></span>  | <span data-ttu-id="d162a-114">AC-Action-openUrl</span><span class="sxs-lookup"><span data-stu-id="d162a-114">ac-action-openUrl</span></span> |
| <span data-ttu-id="d162a-115">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="d162a-115">Action.ShowCard</span></span> | <span data-ttu-id="d162a-116">AC-Action-showCard</span><span class="sxs-lookup"><span data-stu-id="d162a-116">ac-action-showCard</span></span> |
| <span data-ttu-id="d162a-117">Azione. Invia</span><span class="sxs-lookup"><span data-stu-id="d162a-117">Action.Submit</span></span>  | <span data-ttu-id="d162a-118">CA-azione-Invia</span><span class="sxs-lookup"><span data-stu-id="d162a-118">ac-action-submit</span></span>  |
| <span data-ttu-id="d162a-119">ActionSet</span><span class="sxs-lookup"><span data-stu-id="d162a-119">ActionSet</span></span> | <span data-ttu-id="d162a-120">AC-actiont</span><span class="sxs-lookup"><span data-stu-id="d162a-120">ac-actionset</span></span> |
| <span data-ttu-id="d162a-121">Colonna</span><span class="sxs-lookup"><span data-stu-id="d162a-121">Column</span></span> | <span data-ttu-id="d162a-122">colonna AC</span><span class="sxs-lookup"><span data-stu-id="d162a-122">ac-column</span></span> |
| <span data-ttu-id="d162a-123">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="d162a-123">ColumnSet</span></span> | <span data-ttu-id="d162a-124">AC-columnstore</span><span class="sxs-lookup"><span data-stu-id="d162a-124">ac-columnset</span></span> |
| <span data-ttu-id="d162a-125">Contenitore</span><span class="sxs-lookup"><span data-stu-id="d162a-125">Container</span></span> | <span data-ttu-id="d162a-126">contenitore AC</span><span class="sxs-lookup"><span data-stu-id="d162a-126">ac-container</span></span> |
| <span data-ttu-id="d162a-127">Tutti gli input</span><span class="sxs-lookup"><span data-stu-id="d162a-127">All Inputs</span></span> | <span data-ttu-id="d162a-128">input AC</span><span class="sxs-lookup"><span data-stu-id="d162a-128">ac-input</span></span> |
| <span data-ttu-id="d162a-129">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="d162a-129">Input.ChoiceSet</span></span> | <span data-ttu-id="d162a-130">AC-multichoiceInput</span><span class="sxs-lookup"><span data-stu-id="d162a-130">ac-multichoiceInput</span></span>  |
| <span data-ttu-id="d162a-131">Input. Data</span><span class="sxs-lookup"><span data-stu-id="d162a-131">Input.Date</span></span> | <span data-ttu-id="d162a-132">AC-dateInput</span><span class="sxs-lookup"><span data-stu-id="d162a-132">ac-dateInput</span></span> |
| <span data-ttu-id="d162a-133">Input. Number</span><span class="sxs-lookup"><span data-stu-id="d162a-133">Input.Number</span></span> | <span data-ttu-id="d162a-134">AC-numberInput</span><span class="sxs-lookup"><span data-stu-id="d162a-134">ac-numberInput</span></span> |
| <span data-ttu-id="d162a-135">Input.Text</span><span class="sxs-lookup"><span data-stu-id="d162a-135">Input.Text</span></span> | <span data-ttu-id="d162a-136">ac-textInput</span><span class="sxs-lookup"><span data-stu-id="d162a-136">ac-textInput</span></span> |
| <span data-ttu-id="d162a-137">Input.Time</span><span class="sxs-lookup"><span data-stu-id="d162a-137">Input.Time</span></span> | <span data-ttu-id="d162a-138">AC-timeInput</span><span class="sxs-lookup"><span data-stu-id="d162a-138">ac-timeInput</span></span> |
| <span data-ttu-id="d162a-139">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="d162a-139">Input.Toggle</span></span>| - |
| <span data-ttu-id="d162a-140">Image</span><span class="sxs-lookup"><span data-stu-id="d162a-140">Image</span></span>  | <span data-ttu-id="d162a-141">AC-image</span><span class="sxs-lookup"><span data-stu-id="d162a-141">ac-image</span></span> |
| <span data-ttu-id="d162a-142">ImageSet</span><span class="sxs-lookup"><span data-stu-id="d162a-142">ImageSet</span></span>  | <span data-ttu-id="d162a-143">AC-imaget</span><span class="sxs-lookup"><span data-stu-id="d162a-143">ac-imageset</span></span> |
| <span data-ttu-id="d162a-144">FactSet</span><span class="sxs-lookup"><span data-stu-id="d162a-144">FactSet</span></span> | <span data-ttu-id="d162a-145">CA-fact</span><span class="sxs-lookup"><span data-stu-id="d162a-145">ac-factset</span></span> |
| <span data-ttu-id="d162a-146">TextBlock</span><span class="sxs-lookup"><span data-stu-id="d162a-146">TextBlock</span></span>  | <span data-ttu-id="d162a-147">AC-TextBlock</span><span class="sxs-lookup"><span data-stu-id="d162a-147">ac-textblock</span></span> |