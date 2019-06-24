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
# <a name="native-styling---android"></a>Applicazione di stili nativi - Android

L'applicazione di stili nativi non è supportata nel renderer di Android. Nella versione 1.2 è stato introdotto il supporto per gli stili per alcune proprietà:

## <a name="action-sentiment"></a>Sentiment dell'azione

Il sentiment dell'azione è incluso nella **versione 1.2**. Sebbene supporti meno stili rispetto alle altre versioni, puoi applicare uno stile alle azioni con sentiment *destructive* o *positive*, implementando uno stile valido e aggiungendo la riga seguente in styles.xml per il progetto

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## <a name="inline-action"></a>Azione inline

Gli input di testo con un'azione inline permettono l'applicazione di stili per l'azione di cui viene eseguito il rendering. Questo consente di applicare all'azione uno stile come pulsante (adaptiveInlineAction) o come immagine (adaptiveInlineActionImage)

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> Tutti i nomi degli elementi devono essere mantenuti come illustrato, dal momento che il renderer cerca esattamente questi nomi
