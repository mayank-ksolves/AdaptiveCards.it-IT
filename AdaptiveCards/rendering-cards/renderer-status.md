---
title: Stato del renderer
author: matthidinger
ms.author: mahiding
ms.date: 10/12/2018
ms.topic: article
ms.openlocfilehash: bffa49012a8ebe686fc033f98b2438d2e9e959cc
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2019
ms.locfileid: "67138034"
---
# <a name="renderer-status"></a>Stato del renderer
Le tabelle seguenti mostrano lo stato corrente di ogni renderer in base alle rispettive versioni pubbliche che sono pubblicate.

### <a name="parsing"></a>Analisi

|Funzionalità | HTML | .NET | Piattaforma UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Restituzione degli errori di convalida | ✅ | ✅ | ✅ | ✅ | ✅ |
|Analisi di proprietà sconosciute | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="card-rendering"></a>Rendering delle schede

|Funzionalità | HTML | .NET | Piattaforma UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Verifica della versione supportata | ✅ | ✅ | ✅ | ✅ | ✅  |
|Rendering dello schema completo | ✅ | ✅ | ✅ | ✅ | ✅ |
|Rendering della barra delle azioni | ✅ | ✅ | ✅ | ✅ | ✅ |
|Possibilità di ignorare gli elementi sconosciuti | ✅ | ✅ | ✅ | ✅ | ✅ |
|Supporto della configurazione dell'host | ✅ | ✅ | ✅ | ✅ | ✅ |
|Applicazione dello stile della piattaforma nativa | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="element-rendering"></a>Rendering degli elementi

|Funzionalità | HTML | .NET | Piattaforma UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Spaziatura e separatore | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Formattazione di DATE/TIME TextBlock](../authoring-cards/text-features.md#datetime-formatting-and-localization) | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Supporto di Markdown di TextBlock](../authoring-cards/text-features.md#markdown) | ✅* | ✅ | ✅ | ✅ | ✅ |
|Supporto dell'input completo | ✅ | ✅ | ✅ | ✅ | ✅ |

\* Il renderer HTML non include il supporto di Markdown incorporato in modo da ridurre al minimo le dimensioni della libreria e consentire alle applicazioni di usare il processore Markdown preferito. Il renderer HTML tuttavia userà automaticamente Markdown, se caricato.

### <a name="extensibility"></a>Estendibilità

|Funzionalità | HTML | .NET | Piattaforma UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Override del renderer degli elementi | ✅ | ✅ | ✅ | ✅ | ✅ |
|Aggiunta di un nuovo renderer di elementi | ✅ | ✅ | ✅ | ✅ | ✅ |
|Rimozione del renderer degli elementi | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Override/aggiunta/rimozione del renderer delle azioni](https://github.com/Microsoft/AdaptiveCards/issues/1671) | ✅ | ✅ | ❌ | ✅ | ✅ |

### <a name="actions"></a>Azioni

| Funzionalità | HTML | .NET | Piattaforma UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
| Supporto di Action.OpenUrl | ✅ | ✅ | ✅ | ✅ | ✅  |
| Supporto di Action.ShowCard  | ✅ | ✅ | ✅ | ✅ | ✅ |
| Supporto di Action.Submit  | ✅ | ✅ | ✅ | ✅ | ✅  |
| Supporto di selectAction | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="events"></a>Eventi

|       Funzionalità        | HTML | .NET | Piattaforma UWP | iOS | Android | 
|----------------------------|------|------|-----|-----|---------|
| Visibilità degli elementi modificata |  ✅   |  ❌   |  ❌  |  ❌  | ❌ |

