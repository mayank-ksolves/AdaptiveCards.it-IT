---
title: Azioni-.NET HTML SDK
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
# <a name="actions---net-html"></a>Azioni-HTML .NET

Il rendering della scheda `actions` di primo livello verrà eseguito `<button>`come HTML. Poiché si tratta di una libreria sul lato server, è possibile collegare i gestori eventi sul lato client quando vengono premuti i pulsanti. Ogni `<button>` nel codice HTML avrà attributi che è possibile usare per collegare il comportamento appropriato.

Alcuni elementi hanno una `selectAction` proprietà (container, Columns, image) che li rende richiamabili. Se un elemento dispone di `selectAction` un oggetto, il renderer aggiungerà una `ac-selectable`classe CSS di, insieme agli attributi seguenti.

Tipo di azione | Classe CSS | Attributi aggiuntivi
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | `data-ac-url``url` (proprietà dalla scheda)
`Action.Submit` | `ac-action-submit` | `data-ac-data``data` (proprietà dalla scheda)
`Action.ShowCard` | `ac-action-showCard` | `data-ac-showcardid`(dell'oggetto che contiene la scheda interna). `<div>` `id`