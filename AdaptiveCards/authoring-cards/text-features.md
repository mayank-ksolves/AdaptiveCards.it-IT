---
title: Funzionalità per il testo
author: matthidinger
ms.author: mahiding
ms.date: 11/09/2017
ms.topic: article
ms.openlocfilehash: ac8ec0c48e06377ebd17f1b31abe463c48809fe3
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2019
ms.locfileid: "59553613"
---
# <a name="text-features"></a>Funzionalità per il testo

`TextBlock` offre alcune funzionalità avanzate per la formattazione e la localizzazione del testo.

## <a name="markdown"></a>Markdown
Per supportare il markup inline, le schede adattive supportano un **subset** della sintassi Markdown.

_Supportato_

| Stile del testo      | Markdown |
|-----------------|-----|
| **Grassetto**        | ```**Bold**``` |
| _Corsivo_        | ```_Italic_``` |
| Elenco puntato     | ```- Item 1\r- Item 2\r- Item 3``` | 
| Elenco numerato   | ```1. Green\r2. Orange\r3. Blue``` |
| Collegamenti ipertestuali      | ```[Title](url)``` |

_Non supportato_

* Intestazioni
* Tabelle
* Immagini
* Qualsiasi elemento non presente nella tabella precedente

### <a name="markdown-example"></a>Esempio di Markdown

Il payload che segue determina un rendering simile al seguente:

![Screenshot di Markdown](media/text-features/markdown.png)

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "This is some **bold** text"
        },
        {
            "type": "TextBlock",
            "text": "This is some _italic_ text"
        },
        {
            "type": "TextBlock",
            "text": "- Bullet \r- List \r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "1. Numbered\r2. List\r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "Check out [Adaptive Cards](http://adaptivecards.io)"
        }
    ]
}
```

## <a name="datetime-formatting-and-localization"></a>Formattazione e localizzazione di data/ora

In alcuni casi non è possibile conoscere il fuso orario dell'utente che riceve la scheda, pertanto le schede adattive offrono le funzioni di formattazione `DATE()` e `TIME()` per localizzare automaticamente l'ora nel dispositivo di destinazione.

### <a name="datetime-example"></a>Esempio di data/ora

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Your package will arrive on {{DATE(2017-02-14T06:00:00Z, SHORT)}} at {{TIME(2017-02-14T06:00:00Z)}}",
            "wrap": true
        }
    ]
}
```

La scheda precedente visualizza quanto segue: 

> **Il pacchetto arriverà Mar, 14 feb 2017 alle 6:00**

### <a name="datetime-function-rules"></a>Regole per le funzioni di data/ora

Alcune regole consentono la corretta interpretazione delle funzioni di data/ora in ogni piattaforma. Se le regole non vengono soddisfatte, verrà visualizzata all'utente la stringa non elaborata.

1. **DISTINZIONE TRA MAIUSCOLE E MINUSCOLE** (tutte le lettere devono essere maiuscole)
1. **NESSUNO SPAZIO** tra `{{`, `}}` o le parentesi
1. **FORMATTAZIONE [RFC 3389](https://tools.ietf.org/html/rfc3339)**  (vedi gli esempi riportati di seguito)
1. Data e ora **DEVONO** essere valide

### <a name="valid-formats"></a>Formati validi

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a>Parametro per la formattazione della data

Per le date, è possibile specificare un parametro facoltativo per formattare l'output.


|       Formato        |            Esempio            |
|---------------------|-------------------------------|
| `COMPACT` (impostazione predefinita) |          "13/2/2017"          |
|       `SHORT`       |     "Lun, 13 feb 2017"     |
|       `LONG`        | "Lunedì, 13 febbraio 2017" |

