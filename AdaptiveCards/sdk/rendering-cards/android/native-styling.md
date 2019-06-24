---
title: Applicazione di stili nativi - Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: ebb033c68b9aedcaacb1989ffb1bec48707a9026
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134243"
---
# <a name="native-styling---android"></a><span data-ttu-id="deb7d-102">Applicazione di stili nativi - Android</span><span class="sxs-lookup"><span data-stu-id="deb7d-102">Native styling - Android</span></span>

<span data-ttu-id="deb7d-103">L'applicazione di stili nativi non è supportata nel renderer di Android. Nella versione 1.2 è stato introdotto il supporto per gli stili per alcune proprietà:</span><span class="sxs-lookup"><span data-stu-id="deb7d-103">Native styling is not supported on the android renderer, v1.2 introduces the support for styling some properties:</span></span>

## <a name="action-sentiment"></a><span data-ttu-id="deb7d-104">Sentiment dell'azione</span><span class="sxs-lookup"><span data-stu-id="deb7d-104">Action Sentiment</span></span>

<span data-ttu-id="deb7d-105">Il sentiment dell'azione è incluso nella **versione 1.2**. Sebbene supporti meno stili rispetto alle altre versioni, puoi applicare uno stile alle azioni con sentiment *destructive* o *positive*, implementando uno stile valido e aggiungendo la riga seguente in styles.xml per il progetto</span><span class="sxs-lookup"><span data-stu-id="deb7d-105">Action sentiment is included in **v1.2** and while not supporting as many styles as other versions, actions with *destructive* or *positive* sentiment can be styled by implementing a valid style and adding the following line into the styles.xml for your project</span></span>

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## <a name="inline-action"></a><span data-ttu-id="deb7d-106">Azione inline</span><span class="sxs-lookup"><span data-stu-id="deb7d-106">Inline Action</span></span>

<span data-ttu-id="deb7d-107">Gli input di testo con un'azione inline permettono l'applicazione di stili per l'azione di cui viene eseguito il rendering.</span><span class="sxs-lookup"><span data-stu-id="deb7d-107">Text inputs with an inline action allows styling for the action being rendered.</span></span> <span data-ttu-id="deb7d-108">Questo consente di applicare all'azione uno stile come pulsante (adaptiveInlineAction) o come immagine (adaptiveInlineActionImage)</span><span class="sxs-lookup"><span data-stu-id="deb7d-108">This allows styling the action as a button (adaptiveInlineAction) or as an image (adaptiveInlineActionImage)</span></span>

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> <span data-ttu-id="deb7d-109">Tutti i nomi degli elementi devono essere mantenuti come illustrato, dal momento che il renderer cerca esattamente questi nomi</span><span class="sxs-lookup"><span data-stu-id="deb7d-109">All item names must be kept as shown here as the renderer looks for those exact names</span></span>
