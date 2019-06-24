---
title: Eseguire il rendering di una scheda - Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: a4eeda54a80c959ff9a1246371240954b4c3fb12
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134282"
---
# <a name="render-a-card---android"></a>Eseguire il rendering di una scheda - Android

Ecco come eseguire il rendering di una scheda usando Android SDK.

## <a name="create-adaptive-card-object-instance-from-json-text"></a>Creare l'istanza dell'oggetto della scheda adattiva da testo JSON

```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, elementParserRegistration);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```
> [!IMPORTANT]
> **Modifiche importanti per la versione 1.2**
> 
> 1. Il parametro ElementParserRegistration è stato modificato in ParseContext, che include ElementParserRegistration e un oggetto ActionRegistration
> ```java
> ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
> ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
> ```

## <a name="render-a-card"></a>Eseguire il rendering di una scheda

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
View v = renderedCard.getView();
```
