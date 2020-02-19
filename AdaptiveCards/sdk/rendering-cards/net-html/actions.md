---
title: Azioni-.NET HTML SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: f577c0bab73e2bd1f75bb22dd7a41a7dbfd63307
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454574"
---
# <a name="actions---net-html"></a><span data-ttu-id="fdfa2-102">Azioni-HTML .NET</span><span class="sxs-lookup"><span data-stu-id="fdfa2-102">Actions - .NET HTML</span></span>

<span data-ttu-id="fdfa2-103">`actions` della scheda di primo livello verrà eseguito il rendering come `<button>`HTML.</span><span class="sxs-lookup"><span data-stu-id="fdfa2-103">Top-level card `actions` will render as an HTML `<button>`.</span></span> <span data-ttu-id="fdfa2-104">Poiché si tratta di una libreria sul lato server, è possibile collegare i gestori eventi sul lato client quando vengono premuti i pulsanti.</span><span class="sxs-lookup"><span data-stu-id="fdfa2-104">Since this is a server-side library it's up to you to wire up client-side event handlers when buttons are pressed.</span></span> <span data-ttu-id="fdfa2-105">Ogni `<button>` nel codice HTML avrà attributi che è possibile usare per collegare il comportamento appropriato.</span><span class="sxs-lookup"><span data-stu-id="fdfa2-105">Each `<button>` in the HTML will have attributes that you can use to wire up the proper behavior.</span></span>

<span data-ttu-id="fdfa2-106">Alcuni elementi hanno una proprietà `selectAction` (contenitore, colonne, immagine) che li rende richiamabili.</span><span class="sxs-lookup"><span data-stu-id="fdfa2-106">Some elements have a `selectAction` property (Container, Columns, Image) which makes them invokable.</span></span> <span data-ttu-id="fdfa2-107">Se un elemento dispone di un `selectAction` il renderer aggiungerà una classe CSS di `ac-selectable`, insieme agli attributi seguenti.</span><span class="sxs-lookup"><span data-stu-id="fdfa2-107">If an element has a `selectAction` the renderer will add a CSS class of `ac-selectable`, along with the below attributes.</span></span>

<span data-ttu-id="fdfa2-108">Tipo di azione</span><span class="sxs-lookup"><span data-stu-id="fdfa2-108">Action Type</span></span> | <span data-ttu-id="fdfa2-109">Classe CSS</span><span class="sxs-lookup"><span data-stu-id="fdfa2-109">CSS class</span></span> | <span data-ttu-id="fdfa2-110">Attributi aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="fdfa2-110">Additional attributes</span></span>
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | <span data-ttu-id="fdfa2-111">`data-ac-url` (la proprietà `url` dalla scheda)</span><span class="sxs-lookup"><span data-stu-id="fdfa2-111">`data-ac-url` (the `url` property from the card)</span></span>
`Action.Submit` | `ac-action-submit` | <span data-ttu-id="fdfa2-112">`data-ac-data` (la proprietà `data` dalla scheda)</span><span class="sxs-lookup"><span data-stu-id="fdfa2-112">`data-ac-data` (the `data` property from the card)</span></span>
`Action.ShowCard` | `ac-action-showCard` | <span data-ttu-id="fdfa2-113">`data-ac-showcardid` (il `id` del `<div>` contenente la scheda interna)</span><span class="sxs-lookup"><span data-stu-id="fdfa2-113">`data-ac-showcardid` (the `id` of the `<div>` containing the inner card)</span></span>