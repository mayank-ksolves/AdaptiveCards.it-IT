---
title: Azioni
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 34283b52f0c4902c71ea33634676832c7dfec5c9
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2020
ms.locfileid: "77454944"
---
# <a name="actions"></a><span data-ttu-id="d2424-102">Azioni</span><span class="sxs-lookup"><span data-stu-id="d2424-102">Actions</span></span>

<span data-ttu-id="d2424-103">Per impostazione predefinita, le azioni verranno sottoposte a rendering come pulsanti nella scheda, ma spetta all'app fare in modo che si comportino come previsto.</span><span class="sxs-lookup"><span data-stu-id="d2424-103">By default, the actions will render as buttons on the card, but it's up to your app to make them behave as you expect.</span></span> <span data-ttu-id="d2424-104">Ogni SDK dispone dell'equivalente di un evento `OnAction` da gestire.</span><span class="sxs-lookup"><span data-stu-id="d2424-104">Each SDK has the equivalent of an `OnAction` event that you must handle.</span></span>

* <span data-ttu-id="d2424-105">**Action.OpenURL**: apre l'oggetto `url` specificato.</span><span class="sxs-lookup"><span data-stu-id="d2424-105">**Action.OpenUrl** - open the specified `url`.</span></span>  
* <span data-ttu-id="d2424-106">**Action.Submit**: invia all'origine il risultato dell'invio.</span><span class="sxs-lookup"><span data-stu-id="d2424-106">**Action.Submit** - take the result of the submit and send it to the source.</span></span> <span data-ttu-id="d2424-107">Spetta a te scegliere come inviarlo all'origine della scheda.</span><span class="sxs-lookup"><span data-stu-id="d2424-107">How you send it to the source of the card is entirely up to you.</span></span>
* <span data-ttu-id="d2424-108">**Action.ShowCard**: richiama una finestra di dialogo ed esegue il rendering della scheda secondaria in tale finestra.</span><span class="sxs-lookup"><span data-stu-id="d2424-108">**Action.ShowCard** - invokes a dialog and renders the sub-card into that dialog.</span></span> <span data-ttu-id="d2424-109">Considera che devi gestire questa operazione solo se l'impostazione di `ShowCardActionMode` è `popup`.</span><span class="sxs-lookup"><span data-stu-id="d2424-109">Note that you only need to handle this if `ShowCardActionMode` is set to `popup`.</span></span>