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
# <a name="actions---net-html"></a>Azioni-HTML .NET

`actions` della scheda di primo livello verrà eseguito il rendering come `<button>`HTML. Poiché si tratta di una libreria sul lato server, è possibile collegare i gestori eventi sul lato client quando vengono premuti i pulsanti. Ogni `<button>` nel codice HTML avrà attributi che è possibile usare per collegare il comportamento appropriato.

Alcuni elementi hanno una proprietà `selectAction` (contenitore, colonne, immagine) che li rende richiamabili. Se un elemento dispone di un `selectAction` il renderer aggiungerà una classe CSS di `ac-selectable`, insieme agli attributi seguenti.

Tipo di azione | Classe CSS | Attributi aggiuntivi
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | `data-ac-url` (la proprietà `url` dalla scheda)
`Action.Submit` | `ac-action-submit` | `data-ac-data` (la proprietà `data` dalla scheda)
`Action.ShowCard` | `ac-action-showCard` | `data-ac-showcardid` (il `id` del `<div>` contenente la scheda interna)