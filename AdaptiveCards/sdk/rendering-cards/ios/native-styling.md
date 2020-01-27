---
title: Stile nativo-iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: f9ed839a19ac778381fa36361ad37e95b7ab5e08
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727464"
---
# <a name="native-styling---ios"></a><span data-ttu-id="d4bfc-102">Stile nativo-iOS</span><span class="sxs-lookup"><span data-stu-id="d4bfc-102">Native styling - iOS</span></span>

<span data-ttu-id="d4bfc-103">Usare XIB per lo stile con granularità fine.</span><span class="sxs-lookup"><span data-stu-id="d4bfc-103">Use XIB for fine-grained styling.</span></span>

<span data-ttu-id="d4bfc-104">Esistono i XIB seguenti</span><span class="sxs-lookup"><span data-stu-id="d4bfc-104">The following XIBs exist</span></span>

| <span data-ttu-id="d4bfc-105">XIB</span><span class="sxs-lookup"><span data-stu-id="d4bfc-105">XIB</span></span> | <span data-ttu-id="d4bfc-106">Usage</span><span class="sxs-lookup"><span data-stu-id="d4bfc-106">Usage</span></span> |
|---|---|
| <span data-ttu-id="d4bfc-107">ACRButton. xib</span><span class="sxs-lookup"><span data-stu-id="d4bfc-107">ACRButton.xib</span></span> | <span data-ttu-id="d4bfc-108">pulsanti</span><span class="sxs-lookup"><span data-stu-id="d4bfc-108">buttons</span></span> |
| <span data-ttu-id="d4bfc-109">ACRCellForCompactMode. xib</span><span class="sxs-lookup"><span data-stu-id="d4bfc-109">ACRCellForCompactMode.xib</span></span>   | <span data-ttu-id="d4bfc-110">Modalità compatta di opzioni</span><span class="sxs-lookup"><span data-stu-id="d4bfc-110">ChoiceSet compact mode</span></span>|
| <span data-ttu-id="d4bfc-111">ACRDatePicker. xib</span><span class="sxs-lookup"><span data-stu-id="d4bfc-111">ACRDatePicker.xib</span></span> | <span data-ttu-id="d4bfc-112">DatePicker per input. date</span><span class="sxs-lookup"><span data-stu-id="d4bfc-112">DatePicker for Input.Date</span></span> |
| <span data-ttu-id="d4bfc-113">ACRDateTextField. xib</span><span class="sxs-lookup"><span data-stu-id="d4bfc-113">ACRDateTextField.xib</span></span>  | <span data-ttu-id="d4bfc-114">TextField per input. date</span><span class="sxs-lookup"><span data-stu-id="d4bfc-114">TextField for Input.Date</span></span> |
| <span data-ttu-id="d4bfc-115">ACRInputTableView. xib</span><span class="sxs-lookup"><span data-stu-id="d4bfc-115">ACRInputTableView.xib</span></span>   | <span data-ttu-id="d4bfc-116">Contenitore per gli input</span><span class="sxs-lookup"><span data-stu-id="d4bfc-116">Container for Inputs</span></span> |
| <span data-ttu-id="d4bfc-117">ACRLabelView. xib</span><span class="sxs-lookup"><span data-stu-id="d4bfc-117">ACRLabelView.xib</span></span>  | <span data-ttu-id="d4bfc-118">TextBlock</span><span class="sxs-lookup"><span data-stu-id="d4bfc-118">TextBlock</span></span> |
| <span data-ttu-id="d4bfc-119">ACRPickerView. xib</span><span class="sxs-lookup"><span data-stu-id="d4bfc-119">ACRPickerView.xib</span></span> | <span data-ttu-id="d4bfc-120">Opzioni</span><span class="sxs-lookup"><span data-stu-id="d4bfc-120">ChoiceSet</span></span> |
| <span data-ttu-id="d4bfc-121">ACRQuickActionMultilineView. xib</span><span class="sxs-lookup"><span data-stu-id="d4bfc-121">ACRQuickActionMultilineView.xib</span></span>  | <span data-ttu-id="d4bfc-122">Azioni rapide con più righe</span><span class="sxs-lookup"><span data-stu-id="d4bfc-122">Quick Actions with multilines</span></span> |
| <span data-ttu-id="d4bfc-123">ACRQuickActionView. xib</span><span class="sxs-lookup"><span data-stu-id="d4bfc-123">ACRQuickActionView.xib</span></span> | <span data-ttu-id="d4bfc-124">Azioni rapide</span><span class="sxs-lookup"><span data-stu-id="d4bfc-124">Quick Actions</span></span> |
| <span data-ttu-id="d4bfc-125">ACRTextField. xib</span><span class="sxs-lookup"><span data-stu-id="d4bfc-125">ACRTextField.xib</span></span> | <span data-ttu-id="d4bfc-126">Input</span><span class="sxs-lookup"><span data-stu-id="d4bfc-126">Input</span></span> |

<span data-ttu-id="d4bfc-127">XIB può essere modificato tramite XCode IB.</span><span class="sxs-lookup"><span data-stu-id="d4bfc-127">XIB can be edited through XCode IB.</span></span>
<span data-ttu-id="d4bfc-128">Dopo la modifica di XIB nella specifica.</span><span class="sxs-lookup"><span data-stu-id="d4bfc-128">Once XIBs are edited to the specification.</span></span>
<span data-ttu-id="d4bfc-129">Da un terminale</span><span class="sxs-lookup"><span data-stu-id="d4bfc-129">From a terminal</span></span>
```
ibtool --compile name.nib name.xib 
```

<span data-ttu-id="d4bfc-130">Ad esempio, per applicare uno stile a un pulsante</span><span class="sxs-lookup"><span data-stu-id="d4bfc-130">For example, to style a button</span></span>
```
ibtool --compile ACRButton.nib ACRButton.xib 
```

<span data-ttu-id="d4bfc-131">I file del pennino generati possono essere sostituiti in AdaptiveCards. Framework</span><span class="sxs-lookup"><span data-stu-id="d4bfc-131">The generated nib files can be then replaced at AdaptiveCards.framework</span></span>
