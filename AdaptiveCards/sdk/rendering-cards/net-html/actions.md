---
title: Azioni - HTML .NET SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 99bf6121489391c207a71b45264dc68aa2c6116e
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553313"
---
# <a name="actions---net-html"></a><span data-ttu-id="de89c-102">Azioni - .NET HTML</span><span class="sxs-lookup"><span data-stu-id="de89c-102">Actions - .NET HTML</span></span>

<span data-ttu-id="de89c-103">Scheda di livello superiore `actions` verrà eseguito il rendering come HTML `<button>`.</span><span class="sxs-lookup"><span data-stu-id="de89c-103">Top-level card `actions` will render as an HTML `<button>`.</span></span> <span data-ttu-id="de89c-104">Poiché si tratta di una libreria lato server spetta all'utente per collegare i gestori eventi lato client quando vengono premuti i pulsanti.</span><span class="sxs-lookup"><span data-stu-id="de89c-104">Since this is a server-side library it's up to you to wire up client-side event handlers when buttons are pressed.</span></span> <span data-ttu-id="de89c-105">Ogni `<button>` nel codice HTML avrà attributi che è possibile usare consente di associare il comportamento corretto.</span><span class="sxs-lookup"><span data-stu-id="de89c-105">Each `<button>` in the HTML will have attributes that you can use to wire up the proper behavior.</span></span>

<span data-ttu-id="de89c-106">Alcuni elementi hanno un `selectAction` proprietà (immagine del contenitore, le colonne) che li rende richiamabili.</span><span class="sxs-lookup"><span data-stu-id="de89c-106">Some elements have a `selectAction` property (Container, Columns, Image) which makes them invokable.</span></span> <span data-ttu-id="de89c-107">Se un elemento contiene un `selectAction` il renderer verrà aggiunta una classe CSS di `ac-selectable`, insieme a di seguito gli attributi.</span><span class="sxs-lookup"><span data-stu-id="de89c-107">If an element has a `selectAction` the renderer will add a CSS class of `ac-selectable`, along with the below attributes.</span></span>

<span data-ttu-id="de89c-108">Tipo di azione</span><span class="sxs-lookup"><span data-stu-id="de89c-108">Action Type</span></span> | <span data-ttu-id="de89c-109">Classe CSS</span><span class="sxs-lookup"><span data-stu-id="de89c-109">CSS class</span></span> | <span data-ttu-id="de89c-110">Attributi aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="de89c-110">Additional attributes</span></span>
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | <span data-ttu-id="de89c-111">`data-ac-url` (il `url` proprietà dalla smart card)</span><span class="sxs-lookup"><span data-stu-id="de89c-111">`data-ac-url` (the `url` property from the card)</span></span>
`Action.Submit` | `ac-action-submit` | <span data-ttu-id="de89c-112">`data-ac-data` (il `data` proprietà dalla smart card)</span><span class="sxs-lookup"><span data-stu-id="de89c-112">`data-ac-data` (the `data` property from the card)</span></span>
`Action.ShowCard` | `ac-action-showCard` | <span data-ttu-id="de89c-113">`data-ac-showcardid` (il `id` del `<div>` contenente la scheda interna)</span><span class="sxs-lookup"><span data-stu-id="de89c-113">`data-ac-showcardid` (the `id` of the `<div>` containing the inner card)</span></span>