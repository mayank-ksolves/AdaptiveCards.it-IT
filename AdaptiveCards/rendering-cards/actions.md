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
# <a name="actions"></a>Azioni

Per impostazione predefinita, le azioni verranno sottoposte a rendering come pulsanti nella scheda, ma spetta all'app fare in modo che si comportino come previsto. Ogni SDK dispone dell'equivalente di un evento `OnAction` da gestire.

* **Action.OpenURL**: apre l'oggetto `url` specificato.  
* **Action.Submit**: invia all'origine il risultato dell'invio. Spetta a te scegliere come inviarlo all'origine della scheda.
* **Action.ShowCard**: richiama una finestra di dialogo ed esegue il rendering della scheda secondaria in tale finestra. Considera che devi gestire questa operazione solo se l'impostazione di `ShowCardActionMode` è `popup`.