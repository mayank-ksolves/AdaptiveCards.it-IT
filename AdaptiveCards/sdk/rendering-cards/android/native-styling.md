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

## <a name="actionshowcard"></a>Action.ShowCard

È possibile applicare uno stile a Action. ShowCard aggiungendo stili al tema in styles.xml.

```styles.xml
 <item name="adaptiveShowCardAction">@style/adaptiveShowCardAction</item>
```