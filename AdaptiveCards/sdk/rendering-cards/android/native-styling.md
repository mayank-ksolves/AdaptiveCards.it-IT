---
title: Applicazione di stili nativi - Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 8d5dd9bbf17800c55aae1d416b7e6d80ac697b25
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417608"
---
# <a name="native-styling---android"></a><span data-ttu-id="bbd34-102">Applicazione di stili nativi - Android</span><span class="sxs-lookup"><span data-stu-id="bbd34-102">Native styling - Android</span></span>

<span data-ttu-id="bbd34-103">L'applicazione di stili nativi non è supportata nel renderer di Android. Nella versione 1.2 è stato introdotto il supporto per gli stili per alcune proprietà:</span><span class="sxs-lookup"><span data-stu-id="bbd34-103">Native styling is not supported on the android renderer, v1.2 introduces the support for styling some properties:</span></span>

## <a name="action-sentiment"></a><span data-ttu-id="bbd34-104">Sentiment dell'azione</span><span class="sxs-lookup"><span data-stu-id="bbd34-104">Action Sentiment</span></span>

<span data-ttu-id="bbd34-105">Il sentiment dell'azione è incluso nella **versione 1.2**. Sebbene supporti meno stili rispetto alle altre versioni, puoi applicare uno stile alle azioni con sentiment *destructive* o *positive*, implementando uno stile valido e aggiungendo la riga seguente in styles.xml per il progetto</span><span class="sxs-lookup"><span data-stu-id="bbd34-105">Action sentiment is included in **v1.2** and while not supporting as many styles as other versions, actions with *destructive* or *positive* sentiment can be styled by implementing a valid style and adding the following line into the styles.xml for your project</span></span>

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## <a name="inline-action"></a><span data-ttu-id="bbd34-106">Azione inline</span><span class="sxs-lookup"><span data-stu-id="bbd34-106">Inline Action</span></span>

<span data-ttu-id="bbd34-107">Gli input di testo con un'azione inline permettono l'applicazione di stili per l'azione di cui viene eseguito il rendering.</span><span class="sxs-lookup"><span data-stu-id="bbd34-107">Text inputs with an inline action allows styling for the action being rendered.</span></span> <span data-ttu-id="bbd34-108">Questo consente di applicare all'azione uno stile come pulsante (adaptiveInlineAction) o come immagine (adaptiveInlineActionImage)</span><span class="sxs-lookup"><span data-stu-id="bbd34-108">This allows styling the action as a button (adaptiveInlineAction) or as an image (adaptiveInlineActionImage)</span></span>

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> <span data-ttu-id="bbd34-109">Tutti i nomi degli elementi devono essere mantenuti come illustrato, dal momento che il renderer cerca esattamente questi nomi</span><span class="sxs-lookup"><span data-stu-id="bbd34-109">All item names must be kept as shown here as the renderer looks for those exact names</span></span>

## <a name="actionshowcard"></a><span data-ttu-id="bbd34-110">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="bbd34-110">Action.ShowCard</span></span>

<span data-ttu-id="bbd34-111">È possibile applicare uno stile a Action. ShowCard aggiungendo stili al tema in styles.xml.</span><span class="sxs-lookup"><span data-stu-id="bbd34-111">Action.ShowCard can be styled by adding styles to your theme in styles.xml.</span></span>

```styles.xml
 <item name="adaptiveShowCardAction">@style/adaptiveShowCardAction</item>
```