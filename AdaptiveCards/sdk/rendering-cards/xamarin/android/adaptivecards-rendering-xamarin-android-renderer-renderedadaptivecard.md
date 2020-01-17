---
title: Classe RenderedAdaptiveCard-Novell. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: 608b28638ce6ed0a218cfc8dbbe73f22de1ab8cb
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145995"
---
# <a name="renderedadaptivecard"></a>RenderedAdaptiveCard

```csharp
public class RenderedAdaptiveCard : Java.Lang.Object
```

**Namespace**

```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer
```

### <a name="summary"></a>Riepilogo

| Attributi | |
| ---- | --- |
| AdaptiveCard | Rappresentazione logica della scheda adattiva sottoposta a rendering. |
| Input | Dizionario di elementi di input e informazioni aggiunte dall'utente. |
| Visualizza | Risultato visivo del processo di rendering. |
| Avvisi | Elenco di avvisi generati dal processo di rendering. |

&nbsp;

| Metodi pubblici | |
| --- | ---- |
| ```void``` | [```AddWarning AdaptiveCards.Rendering.Xamarin.Android.Renderer.AdaptiveWarning warning)```](#addwarning) |

## <a name="public-methods"></a>Metodi pubblici

---

### <a id="addwarning"></a>AddWarning
<p style='text-align:right'>Aggiunto nella versione 0,1</p>

```csharp
public void AddWarning (AdaptiveWarning warning)

```

Aggiunge un avviso all'elenco degli avvisi.

| Parametri | |
| --- | --- |
| avviso | ```AdaptiveCards.Rendering.Xamarin.Android.Renderer.AdaptiveWarning``` |
