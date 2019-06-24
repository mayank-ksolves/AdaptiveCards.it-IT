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
# <a name="render-a-card---android"></a><span data-ttu-id="9794e-102">Eseguire il rendering di una scheda - Android</span><span class="sxs-lookup"><span data-stu-id="9794e-102">Render a card - Android</span></span>

<span data-ttu-id="9794e-103">Ecco come eseguire il rendering di una scheda usando Android SDK.</span><span class="sxs-lookup"><span data-stu-id="9794e-103">Here's how to render a card using the Android SDK.</span></span>

## <a name="create-adaptive-card-object-instance-from-json-text"></a><span data-ttu-id="9794e-104">Creare l'istanza dell'oggetto della scheda adattiva da testo JSON</span><span class="sxs-lookup"><span data-stu-id="9794e-104">Create Adaptive Card Object Instance from JSON Text</span></span>

```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, elementParserRegistration);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```
> [!IMPORTANT]
> <span data-ttu-id="9794e-105">**Modifiche importanti per la versione 1.2**</span><span class="sxs-lookup"><span data-stu-id="9794e-105">**Breaking changes for v1.2**</span></span>
> 
> 1. <span data-ttu-id="9794e-106">Il parametro ElementParserRegistration è stato modificato in ParseContext, che include ElementParserRegistration e un oggetto ActionRegistration</span><span class="sxs-lookup"><span data-stu-id="9794e-106">ElementParserRegistration parameter changed to ParseContext which includes an ElementParserRegistration and an ActionRegistration object</span></span>
> ```java
> ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
> ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
> ```

## <a name="render-a-card"></a><span data-ttu-id="9794e-107">Eseguire il rendering di una scheda</span><span class="sxs-lookup"><span data-stu-id="9794e-107">Render a card</span></span>

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
View v = renderedCard.getView();
```
