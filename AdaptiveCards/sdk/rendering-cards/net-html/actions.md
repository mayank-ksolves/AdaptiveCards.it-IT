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
# <a name="actions---net-html"></a>Azioni - .NET HTML

Scheda di livello superiore `actions` verrà eseguito il rendering come HTML `<button>`. Poiché si tratta di una libreria lato server spetta all'utente per collegare i gestori eventi lato client quando vengono premuti i pulsanti. Ogni `<button>` nel codice HTML avrà attributi che è possibile usare consente di associare il comportamento corretto.

Alcuni elementi hanno un `selectAction` proprietà (immagine del contenitore, le colonne) che li rende richiamabili. Se un elemento contiene un `selectAction` il renderer verrà aggiunta una classe CSS di `ac-selectable`, insieme a di seguito gli attributi.

Tipo di azione | Classe CSS | Attributi aggiuntivi
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | `data-ac-url` (il `url` proprietà dalla smart card)
`Action.Submit` | `ac-action-submit` | `data-ac-data` (il `data` proprietà dalla smart card)
`Action.ShowCard` | `ac-action-showCard` | `data-ac-showcardid` (il `id` del `<div>` contenente la scheda interna)