---
title: Eseguire il rendering di una scheda - Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 55e0fa828abf3b9af857d1deb7ecd3744b5a7280
ms.sourcegitcommit: 8c8067206f283d97a5aa4ec65ba23d3fe18962f1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299529"
---
# <a name="render-a-card---android"></a><span data-ttu-id="9c7fc-102">Eseguire il rendering di una scheda - Android</span><span class="sxs-lookup"><span data-stu-id="9c7fc-102">Render a card - Android</span></span>

<span data-ttu-id="9c7fc-103">Ecco come eseguire il rendering di una scheda usando Android SDK.</span><span class="sxs-lookup"><span data-stu-id="9c7fc-103">Here's how to render a card using the Android SDK.</span></span>

## <a name="create-adaptive-card-object-instance-from-json-text"></a><span data-ttu-id="9c7fc-104">Creare l'istanza dell'oggetto della scheda adattiva da testo JSON</span><span class="sxs-lookup"><span data-stu-id="9c7fc-104">Create Adaptive Card Object Instance from JSON Text</span></span>

```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, elementParserRegistration);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```
> [!IMPORTANT]
> <span data-ttu-id="9c7fc-105">**Modifiche importanti per la versione 1.2**</span><span class="sxs-lookup"><span data-stu-id="9c7fc-105">**Breaking changes for v1.2**</span></span>
> 

1. <span data-ttu-id="9c7fc-106">Il parametro ElementParserRegistration è stato modificato in ParseContext che include un oggetto ElementParserRegistration e un oggetto ActionParserRegistration</span><span class="sxs-lookup"><span data-stu-id="9c7fc-106">ElementParserRegistration parameter changed to ParseContext which includes an ElementParserRegistration and an ActionParserRegistration object</span></span>

```java
ParseContext context = new ParseContext(); // Empty parseContext so only known elements up to v1.2 will be parsed
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

<span data-ttu-id="9c7fc-107">oppure</span><span class="sxs-lookup"><span data-stu-id="9c7fc-107">or</span></span>

```java
ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

## <a name="render-a-card"></a><span data-ttu-id="9c7fc-108">Eseguire il rendering di una scheda</span><span class="sxs-lookup"><span data-stu-id="9c7fc-108">Render a card</span></span>

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
View v = renderedCard.getView();
```
