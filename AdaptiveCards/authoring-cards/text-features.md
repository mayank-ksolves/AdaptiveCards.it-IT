---
title: Funzioni di testo
author: matthidinger
ms.author: mahiding
ms.date: 11/09/2017
ms.topic: article
ms.openlocfilehash: ac8ec0c48e06377ebd17f1b31abe463c48809fe3
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553613"
---
# <a name="text-features"></a>Funzioni di testo

`TextBlock` offre alcune funzionalità avanzate di formattazione e la localizzazione del testo.

## <a name="markdown"></a>Markdown
Per supportare inline markup, supporta le schede adattive una **subset** della sintassi di Markdown.

_È supportato_

| Stile del testo      | Markdown |
|-----------------|-----|
| **Grassetto**        | ```**Bold**``` |
| _Corsivo_        | ```_Italic_``` |
| Elenco puntato     | ```- Item 1\r- Item 2\r- Item 3``` | 
| Elenco numerato   | ```1. Green\r2. Orange\r3. Blue``` |
| Collegamenti ipertestuali      | ```[Title](url)``` |

_Non è supportato_

* Intestazioni
* Tabelle
* Immagini
* Qualsiasi elemento non nella tabella precedente

### <a name="markdown-example"></a>Esempio di markdown

Il seguente payload visualizzerebbe simile al seguente:

![schermata di markdown](media/text-features/markdown.png)

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

## <a name="datetime-formatting-and-localization"></a>Formattazione di data/ora e la localizzazione

In alcuni casi non è possibile sapere il fuso orario dell'utente che ha ricevuto la scheda, in modo che le schede adattive offre `DATE()` e `TIME()` formattazione funzioni per localizzare automaticamente l'ora nel dispositivo di destinazione.

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

Verrà visualizzata la scheda precedente: 

> **I pacchetto arriveranno Mar, il 14 febbraio 2017 6:00**

### <a name="datetime-function-rules"></a>Data/ora delle regole (funzione)

Sono disponibili alcune regole consentono la corretta interpretazione di funzioni di data/ora in ogni piattaforma. Se le regole non vengono soddisfatti, verrà visualizzata all'utente la stringa non elaborata e nessuno vuole che.

1. **Distinzione maiuscole / MINUSCOLE** (devono essere tutte maiuscole)
1. **SENZA spazi** tra il `{{`, `}}`, parentesi o parentesi
1. **STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) formattazione** (vedere esempi riportati di seguito)
1. **DEVE essere** valido data e ora

### <a name="valid-formats"></a>Formati validi

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a>Date (formattazione) param

Per le date, un parametro facoltativo può essere specificata per formattare l'output.


|       Formato        |            Esempio            |
|---------------------|-------------------------------|
| `COMPACT` (Impostazione predefinita) |          "2/13/2017"          |
|       `SHORT`       |     "Mon 13 febbraio 2017"     |
|       `LONG`        | "Lunedì 13 febbraio 2017" |

