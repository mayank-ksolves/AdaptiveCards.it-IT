---
title: Eseguire il rendering di una scheda - Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: c9fbfa788af0b0c7f16824bf9c369fa59a1b80f5
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145471"
---
# <a name="render-a-card---android"></a><span data-ttu-id="c36f0-102">Eseguire il rendering di una scheda - Android</span><span class="sxs-lookup"><span data-stu-id="c36f0-102">Render a card - Android</span></span>

<span data-ttu-id="c36f0-103">Ecco come eseguire il rendering di una scheda usando Android SDK.</span><span class="sxs-lookup"><span data-stu-id="c36f0-103">Here's how to render a card using the Android SDK.</span></span>

## <a name="create-adaptive-card-object-instance-from-json-text"></a><span data-ttu-id="c36f0-104">Creare l'istanza dell'oggetto della scheda adattiva da testo JSON</span><span class="sxs-lookup"><span data-stu-id="c36f0-104">Create Adaptive Card Object Instance from JSON Text</span></span>

```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, elementParserRegistration);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```
> [!IMPORTANT]
> <span data-ttu-id="c36f0-105">**Modifiche importanti per la versione 1.2**</span><span class="sxs-lookup"><span data-stu-id="c36f0-105">**Breaking changes for v1.2**</span></span>
> 

1. <span data-ttu-id="c36f0-106">Il parametro ElementParserRegistration è stato modificato in ParseContext che include un oggetto ElementParserRegistration e un oggetto ActionParserRegistration</span><span class="sxs-lookup"><span data-stu-id="c36f0-106">ElementParserRegistration parameter changed to ParseContext which includes an ElementParserRegistration and an ActionParserRegistration object</span></span>

```java
ParseContext context = new ParseContext(); // Empty parseContext so only known elements up to v1.2 will be parsed
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

<span data-ttu-id="c36f0-107">o</span><span class="sxs-lookup"><span data-stu-id="c36f0-107">or</span></span>

```java
ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

## <a name="render-a-card"></a><span data-ttu-id="c36f0-108">Eseguire il rendering di una scheda</span><span class="sxs-lookup"><span data-stu-id="c36f0-108">Render a card</span></span>

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
View v = renderedCard.getView();
```
