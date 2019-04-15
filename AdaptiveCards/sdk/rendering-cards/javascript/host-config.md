---
title: Host config - JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 1809a022481e4fb28d2db454cfe90e07d09279ff
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553603"
---
# <a name="host-config---javascript"></a>Configurazione di host - JavaScript

```js
// Create an AdaptiveCard instance
var adaptiveCard = new AdaptiveCards.AdaptiveCard();

// Set its hostConfig property unless you want to use the default Host Config
// Host Config defines the style and behavior of a card
adaptiveCard.hostConfig = new AdaptiveCards.HostConfig({
    fontFamily: "Segoe UI, Helvetica Neue, sans-serif"
    // More host config options
});

// Render the card to an HTML element:
var renderedCard = adaptiveCard.render();
```

## <a name="customization"></a>Personalizzazione

Esistono 3 modi per personalizzare il rendering di scheda adattiva: 
1. Configurazione di host
2. Stile CSS
3. Rendering di elemento personalizzato

### <a name="hostconfig"></a>HostConfig 

Oggetto [Host Config](../../../rendering-cards/host-config.md) è un oggetto di configurazione condivisa che comprendere tutti i renderer. In questo modo è possibile definire stili comuni (ad esempio, famiglia di caratteri, le dimensioni dei caratteri, spaziatura predefinita) e i comportamenti (ad esempio, numero massimo di azioni) che verranno interpretati automaticamente dal renderer ogni piattaforma. 

L'obiettivo è che l'interfaccia utente nativa generato da ogni renderer piattaforma avrà un aspetto molto simile con un intervento minimo da parte dell'utente.

```javascript
var renderOptions = {
    ...
    hostConfig: {
        // Define your host config object here
        // See the HostConfig docs for details
    }
};
```