---
title: Configurazione host-JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: a011ffc43c2990cd8eb568b9f1c449cf541f9a70
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454615"
---
# <a name="host-config---javascript"></a>Configurazione host-JavaScript

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

Sono disponibili tre modi per personalizzare il rendering adattivo della scheda: 
1. Configurazione dell'host
2. Stile CSS
3. Rendering di elementi personalizzati

### <a name="hostconfig"></a>HostConfig 

Una [configurazione dell'host](../../../rendering-cards/host-config.md) è un oggetto di configurazione condiviso che può essere interpretato da tutti i renderer. Questo consente di definire stili comuni (ad esempio, famiglia di caratteri, dimensioni dei caratteri, spaziatura predefinita) e comportamenti (ad esempio, numero massimo di azioni) che verranno interpretati automaticamente dal renderer di ogni piattaforma. 

L'obiettivo è che l'interfaccia utente nativa generata dal renderer di ogni piattaforma abbia un aspetto molto simile, con un intervento minimo da parte dello sviluppatore.

```javascript
var renderOptions = {
    ...
    hostConfig: {
        // Define your host config object here
        // See the HostConfig docs for details
    }
};
```