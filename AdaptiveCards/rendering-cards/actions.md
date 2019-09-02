---
title: Azioni
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 42ba1ca4ba2ecd508bdee2f04061293d48349aab
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553373"
---
# <a name="actions"></a>Azioni

Per impostazione predefinita, le azioni verranno sottoposte a rendering come pulsanti nella scheda, ma spetta all'app fare in modo che si comportino come previsto. Ogni SDK dispone dell'equivalente di un evento `OnAction` da gestire.

* **Action.OpenURL**: apre l'oggetto `url` specificato.  
* **Action.Submit**: invia all'origine il risultato dell'invio. Spetta a te scegliere come inviarlo all'origine della scheda.
* **Action.ShowCard**: richiama una finestra di dialogo ed esegue il rendering della scheda secondaria in tale finestra. Considera che devi gestire questa operazione solo se l'impostazione di `ShowCardActionMode` è `popup`.