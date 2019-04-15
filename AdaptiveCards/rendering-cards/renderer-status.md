---
title: Stato del renderer
author: matthidinger
ms.author: mahiding
ms.date: 10/12/2018
ms.topic: article
ms.openlocfilehash: 303d5675f58bd2c870dcdf5718d508d2e3c78fca
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553353"
---
# <a name="renderer-status"></a>Stato del renderer
Nelle tabelle seguenti indicano lo stato corrente di ogni renderer, in base alle loro versioni pubblicate pubbliche.

### <a name="parsing"></a>L'analisi

|Funzionalità | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Restituire errori di convalida | ✅ | ✅ | ✅ | ✅ | ✅ |
|Analizzare le proprietà sconosciute | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="card-rendering"></a>Rendering di smart card

|Funzionalità | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Controllo per la versione supportata | ✅ | ✅ | ✅ | ✅ | ✅  |
|Eseguire il rendering completo dello schema | ✅ | ✅ | ✅ | ✅ | ✅ |
|Eseguire il rendering sulla barra delle azioni | ✅ | ✅ | ✅ | ✅ | ✅ |
|Ignora gli elementi sconosciuti | ✅ | ✅ | ✅ | ✅ | ✅ |
|Supporto di configurazione di host | ✅ | ✅ | ✅ | ✅ | ✅ |
|Stile di piattaforma nativa | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="element-rendering"></a>Elemento per il Rendering

|Funzionalità | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Spaziatura e il separatore | ✅ | ✅ | ✅ | ✅ | ✅ |
|[TextBlock formattazione della data/ora](../authoring-cards/text-features.md#datetime-formatting-and-localization) | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Supporto di Markdown di TextBlock](../authoring-cards/text-features.md#markdown) | ✅* | ✅ | ✅ | ✅ | ✅ |
|Supporto di Input completo | ✅ | ✅ | ✅ | ✅ | ✅ |

\* Il renderer HTML non include supporto incorporato di Markdown per ridurre al minimo le dimensioni della libreria e per consentire applicazioni costose di usare il processore preferenziale di Markdown. Il renderer HTML userà Markdown It tuttavia automaticamente se è caricato.

### <a name="extensbility"></a>Extensbility

|Funzionalità | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Eseguire l'override del Renderer di elemento | ✅ | ✅ | ✅ | ✅ | ✅ |
|Aggiungi nuovo elemento Renderer | ✅ | ✅ | ✅ | ✅ | ✅ |
|Rimuovi elemento Renderer | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Renderer di azione di sostituzione, aggiungere o rimuovere](https://github.com/Microsoft/AdaptiveCards/issues/1671) | ✅ | ✅ | ❌ | ✅ | ✅ |

### <a name="actions"></a>Azioni

| Funzionalità | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
| Supporto Action.OpenUrl | ✅ | ✅ | ✅ | ✅ | ✅  |
| Supporto Action.ShowCard  | ✅ | ✅ | ✅ | ✅ | ✅ |
| Supporto Action.Submit  | ✅ | ✅ | ✅ | ✅ | ✅  |
| supporto selectAction | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="events"></a>Eventi

|       Funzionalità        | HTML | .NET | UWP | iOS | Android | 
|----------------------------|------|------|-----|-----|---------|
| Visibilità dell'elemento modificata |  ✅   |  ❌   |  ❌  |  ❌  | ❌ |

