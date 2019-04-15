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
# <a name="actions"></a>Azioni

Per impostazione predefinita, le azioni verranno sottoposti a rendering come pulsanti della scheda, ma spetta all'App in modo che siano comportarsi come previsto. Ogni SDK include l'equivalente di un `OnAction` eventi che è necessario gestire.

* **Action.OpenUrl** -aprire l'oggetto specificato `url`.  
* **Action.Submit** : accettare il risultato dell'invio e inviarlo all'origine. Come si invia all'origine della scheda è completamente responsabilità dell'utente.
* **Action.ShowCard** : richiama una finestra di dialogo e viene eseguito il rendering scheda secondario in tale finestra di dialogo. Si noti che è solo necessario gestire questa operazione se `ShowCardActionMode` è impostata su `popup`.