---
title: Azioni
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 42ba1ca4ba2ecd508bdee2f04061293d48349aab
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553373"
---
# <a name="actions"></a><span data-ttu-id="2d3e6-102">Azioni</span><span class="sxs-lookup"><span data-stu-id="2d3e6-102">Actions</span></span>

<span data-ttu-id="2d3e6-103">Per impostazione predefinita, le azioni verranno sottoposti a rendering come pulsanti della scheda, ma spetta all'App in modo che siano comportarsi come previsto.</span><span class="sxs-lookup"><span data-stu-id="2d3e6-103">By default, the actions will render as buttons on the card, but it's up to your app to make them behave as you expect.</span></span> <span data-ttu-id="2d3e6-104">Ogni SDK include l'equivalente di un `OnAction` eventi che è necessario gestire.</span><span class="sxs-lookup"><span data-stu-id="2d3e6-104">Each SDK has the equivalent of an `OnAction` event that you must handle.</span></span>

* <span data-ttu-id="2d3e6-105">**Action.OpenUrl** -aprire l'oggetto specificato `url`.</span><span class="sxs-lookup"><span data-stu-id="2d3e6-105">**Action.OpenUrl** - open the specified `url`.</span></span>  
* <span data-ttu-id="2d3e6-106">**Action.Submit** : accettare il risultato dell'invio e inviarlo all'origine.</span><span class="sxs-lookup"><span data-stu-id="2d3e6-106">**Action.Submit** - take the result of the submit and send it to the source.</span></span> <span data-ttu-id="2d3e6-107">Come si invia all'origine della scheda è completamente responsabilità dell'utente.</span><span class="sxs-lookup"><span data-stu-id="2d3e6-107">How you send it to the source of the card is entirely up to you.</span></span>
* <span data-ttu-id="2d3e6-108">**Action.ShowCard** : richiama una finestra di dialogo e viene eseguito il rendering scheda secondario in tale finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="2d3e6-108">**Action.ShowCard** - invokes a dialog and renders the sub-card into that dialog.</span></span> <span data-ttu-id="2d3e6-109">Si noti che è solo necessario gestire questa operazione se `ShowCardActionMode` è impostata su `popup`.</span><span class="sxs-lookup"><span data-stu-id="2d3e6-109">Note that you only need to handle this if `ShowCardActionMode` is set to `popup`.</span></span>