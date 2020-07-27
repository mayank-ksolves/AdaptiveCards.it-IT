---
title: Funzionalità per il testo
author: matthidinger
ms.author: mahiding
ms.date: 06/18/2020
ms.topic: article
ms.openlocfilehash: d685007cb24e7fa8ef15b53ee5547708fba6b490
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417503"
---
# <a name="text-features"></a>Funzionalità per il testo

[TextBlock](https://adaptivecards.io/explorer/TextBlock.html) offre funzionalità avanzate per la formattazione e la localizzazione del testo.

## <a name="markdown-commonmark-subset"></a>Markdown (subset di Commonmark)

Per supportare il markup inline, Schede adattive supporta un **subset** della sintassi Markdown di [Commonmark](https://commonmark.org/help/).

> [!NOTE]
>
> [RichTextBlock](https://adaptivecards.io/explorer/RichTextBlock.html) non supporta Markdown, ma offre un'ampia gamma di opzioni di configurazione del testo direttamente all'interno di [TextRun](https://adaptivecards.io/explorer/TextRun.html)

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
            "text": "Check out [Adaptive Cards](https://adaptivecards.io)"
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
1. **FORMATTAZIONE [RFC 3389](https://tools.ietf.org/html/rfc3339)** (vedi gli esempi riportati di seguito)
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

