---
title: Native styling - JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 6f086d268abcaeb7fa159b74708597e89aafaf53
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552893"
---
# <a name="native-styling---javascript"></a><span data-ttu-id="51230-102">Stile nativo - JavaScript</span><span class="sxs-lookup"><span data-stu-id="51230-102">Native styling - JavaScript</span></span>

<span data-ttu-id="51230-103">Usare CSS per lo stile con granularità fine della scheda HTML.</span><span class="sxs-lookup"><span data-stu-id="51230-103">Use CSS for fine-grained styling of the card HTML.</span></span>

<span data-ttu-id="51230-104">Le classi CSS seguenti verranno aggiunti ai vari elementi.</span><span class="sxs-lookup"><span data-stu-id="51230-104">The following CSS classes will be added to various elements.</span></span>

| <span data-ttu-id="51230-105">Classe CSS</span><span class="sxs-lookup"><span data-stu-id="51230-105">CSS class</span></span> | <span data-ttu-id="51230-106">Uso</span><span class="sxs-lookup"><span data-stu-id="51230-106">Usage</span></span> |
|---|---|
| <span data-ttu-id="51230-107">.AC-container</span><span class="sxs-lookup"><span data-stu-id="51230-107">.ac-container</span></span> | <span data-ttu-id="51230-108">Contenitori</span><span class="sxs-lookup"><span data-stu-id="51230-108">containers</span></span> |
| <span data-ttu-id="51230-109">.AC selezionabili</span><span class="sxs-lookup"><span data-stu-id="51230-109">.ac-selectable</span></span>  | <span data-ttu-id="51230-110">elementi con `selectAction`</span><span class="sxs-lookup"><span data-stu-id="51230-110">elements with `selectAction`</span></span> |
| <span data-ttu-id="51230-111">.AC-image</span><span class="sxs-lookup"><span data-stu-id="51230-111">.ac-image</span></span> | <span data-ttu-id="51230-112">image</span><span class="sxs-lookup"><span data-stu-id="51230-112">image</span></span> |
| <span data-ttu-id="51230-113">.ac-pushButton</span><span class="sxs-lookup"><span data-stu-id="51230-113">.ac-pushButton</span></span> | <span data-ttu-id="51230-114">azioni viene eseguito il rendering come pulsanti</span><span class="sxs-lookup"><span data-stu-id="51230-114">actions rendered like buttons</span></span> |
| <span data-ttu-id="51230-115">.ac-linkButton</span><span class="sxs-lookup"><span data-stu-id="51230-115">.ac-linkButton</span></span>  | <span data-ttu-id="51230-116">azioni eseguito il rendering come collegamenti</span><span class="sxs-lookup"><span data-stu-id="51230-116">actions rendered like links</span></span> |
| <span data-ttu-id="51230-117">input di .ac</span><span class="sxs-lookup"><span data-stu-id="51230-117">.ac-input</span></span> | <span data-ttu-id="51230-118">Controlli di input</span><span class="sxs-lookup"><span data-stu-id="51230-118">input controls</span></span>|
| <span data-ttu-id="51230-119">.ac-textInput</span><span class="sxs-lookup"><span data-stu-id="51230-119">.ac-textInput</span></span>| <span data-ttu-id="51230-120">Input di testo</span><span class="sxs-lookup"><span data-stu-id="51230-120">text input</span></span> |
| <span data-ttu-id="51230-121">.AC su più righe</span><span class="sxs-lookup"><span data-stu-id="51230-121">.ac-multiline</span></span> | <span data-ttu-id="51230-122">input di testo su più righe</span><span class="sxs-lookup"><span data-stu-id="51230-122">multiline text input</span></span> |
| <span data-ttu-id="51230-123">.ac-numberInput</span><span class="sxs-lookup"><span data-stu-id="51230-123">.ac-numberInput</span></span> | <span data-ttu-id="51230-124">input numerico</span><span class="sxs-lookup"><span data-stu-id="51230-124">number input</span></span>|
| <span data-ttu-id="51230-125">.ac-dateInput</span><span class="sxs-lookup"><span data-stu-id="51230-125">.ac-dateInput</span></span> | <span data-ttu-id="51230-126">input di date</span><span class="sxs-lookup"><span data-stu-id="51230-126">date input</span></span>|
| <span data-ttu-id="51230-127">.ac-timeInput</span><span class="sxs-lookup"><span data-stu-id="51230-127">.ac-timeInput</span></span> | <span data-ttu-id="51230-128">input della durata</span><span class="sxs-lookup"><span data-stu-id="51230-128">time input</span></span> |
| <span data-ttu-id="51230-129">.ac-multichoiceInput</span><span class="sxs-lookup"><span data-stu-id="51230-129">.ac-multichoiceInput</span></span> | <span data-ttu-id="51230-130">input scelte</span><span class="sxs-lookup"><span data-stu-id="51230-130">multichoice input</span></span>|