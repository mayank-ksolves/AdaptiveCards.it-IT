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
# <a name="text-features"></a><span data-ttu-id="78c38-102">Funzionalità per il testo</span><span class="sxs-lookup"><span data-stu-id="78c38-102">Text features</span></span>

<span data-ttu-id="78c38-103">[TextBlock](https://adaptivecards.io/explorer/TextBlock.html) offre funzionalità avanzate per la formattazione e la localizzazione del testo.</span><span class="sxs-lookup"><span data-stu-id="78c38-103">[TextBlock](https://adaptivecards.io/explorer/TextBlock.html) offers advanced features for formatting and localizing the text.</span></span>

## <a name="markdown-commonmark-subset"></a><span data-ttu-id="78c38-104">Markdown (subset di Commonmark)</span><span class="sxs-lookup"><span data-stu-id="78c38-104">Markdown (Commonmark subset)</span></span>

<span data-ttu-id="78c38-105">Per supportare il markup inline, Schede adattive supporta un **subset** della sintassi Markdown di [Commonmark](https://commonmark.org/help/).</span><span class="sxs-lookup"><span data-stu-id="78c38-105">To support inline markup, Adaptive Cards support a **subset** of the [Commonmark](https://commonmark.org/help/) Markdown syntax.</span></span>

> [!NOTE]
>
> <span data-ttu-id="78c38-106">[RichTextBlock](https://adaptivecards.io/explorer/RichTextBlock.html) non supporta Markdown, ma offre un'ampia gamma di opzioni di configurazione del testo direttamente all'interno di [TextRun](https://adaptivecards.io/explorer/TextRun.html)</span><span class="sxs-lookup"><span data-stu-id="78c38-106">[RichTextBlock](https://adaptivecards.io/explorer/RichTextBlock.html) does not support markdown, but offers a wide array of text configuration options directly within the the [TextRun](https://adaptivecards.io/explorer/TextRun.html)</span></span>

<span data-ttu-id="78c38-107">_Supportato_</span><span class="sxs-lookup"><span data-stu-id="78c38-107">_Supported_</span></span>

| <span data-ttu-id="78c38-108">Stile del testo</span><span class="sxs-lookup"><span data-stu-id="78c38-108">Text Style</span></span>      | <span data-ttu-id="78c38-109">Markdown</span><span class="sxs-lookup"><span data-stu-id="78c38-109">Markdown</span></span> |
|-----------------|-----|
| <span data-ttu-id="78c38-110">**Grassetto**</span><span class="sxs-lookup"><span data-stu-id="78c38-110">**Bold**</span></span>        | ```**Bold**``` |
| <span data-ttu-id="78c38-111">_Corsivo_</span><span class="sxs-lookup"><span data-stu-id="78c38-111">_Italic_</span></span>        | ```_Italic_``` |
| <span data-ttu-id="78c38-112">Elenco puntato</span><span class="sxs-lookup"><span data-stu-id="78c38-112">Bullet list</span></span>     | ```- Item 1\r- Item 2\r- Item 3``` | 
| <span data-ttu-id="78c38-113">Elenco numerato</span><span class="sxs-lookup"><span data-stu-id="78c38-113">Numbered list</span></span>   | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="78c38-114">Collegamenti ipertestuali</span><span class="sxs-lookup"><span data-stu-id="78c38-114">Hyperlinks</span></span>      | ```[Title](url)``` |

<span data-ttu-id="78c38-115">_Non supportato_</span><span class="sxs-lookup"><span data-stu-id="78c38-115">_Not supported_</span></span>

* <span data-ttu-id="78c38-116">Intestazioni</span><span class="sxs-lookup"><span data-stu-id="78c38-116">Headers</span></span>
* <span data-ttu-id="78c38-117">Tabelle</span><span class="sxs-lookup"><span data-stu-id="78c38-117">Tables</span></span>
* <span data-ttu-id="78c38-118">Immagini</span><span class="sxs-lookup"><span data-stu-id="78c38-118">Images</span></span>
* <span data-ttu-id="78c38-119">Qualsiasi elemento non presente nella tabella precedente</span><span class="sxs-lookup"><span data-stu-id="78c38-119">Anything not in the table above</span></span>

### <a name="markdown-example"></a><span data-ttu-id="78c38-120">Esempio di Markdown</span><span class="sxs-lookup"><span data-stu-id="78c38-120">Markdown Example</span></span>

<span data-ttu-id="78c38-121">Il payload che segue determina un rendering simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="78c38-121">The below payload would render something like this:</span></span>

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

## <a name="datetime-formatting-and-localization"></a><span data-ttu-id="78c38-123">Formattazione e localizzazione di data/ora</span><span class="sxs-lookup"><span data-stu-id="78c38-123">Date/Time formatting and localization</span></span>

<span data-ttu-id="78c38-124">In alcuni casi non è possibile conoscere il fuso orario dell'utente che riceve la scheda, pertanto le schede adattive offrono le funzioni di formattazione `DATE()` e `TIME()` per localizzare automaticamente l'ora nel dispositivo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="78c38-124">Sometimes you won't know the timezone of the user receiving the card, so Adaptive Cards offers `DATE()` and `TIME()` formatting functions to automatically localize the time on the target device.</span></span>

### <a name="datetime-example"></a><span data-ttu-id="78c38-125">Esempio di data/ora</span><span class="sxs-lookup"><span data-stu-id="78c38-125">Date/Time Example</span></span>

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

<span data-ttu-id="78c38-126">La scheda precedente visualizza quanto segue:</span><span class="sxs-lookup"><span data-stu-id="78c38-126">The above card will display:</span></span> 

> <span data-ttu-id="78c38-127">**Il pacchetto arriverà Mar, 14 feb 2017 alle 6:00**</span><span class="sxs-lookup"><span data-stu-id="78c38-127">**Your package will arrive on Tue, Feb 14th, 2017 at 6:00 AM**</span></span>

### <a name="datetime-function-rules"></a><span data-ttu-id="78c38-128">Regole per le funzioni di data/ora</span><span class="sxs-lookup"><span data-stu-id="78c38-128">Date/Time function rules</span></span>

<span data-ttu-id="78c38-129">Alcune regole consentono la corretta interpretazione delle funzioni di data/ora in ogni piattaforma.</span><span class="sxs-lookup"><span data-stu-id="78c38-129">There are some rules to properly interpret the the date/time functions on every platform.</span></span> <span data-ttu-id="78c38-130">Se le regole non vengono soddisfatte, verrà visualizzata all'utente la stringa non elaborata.</span><span class="sxs-lookup"><span data-stu-id="78c38-130">If the rules aren't met then the raw string will be displayed to the user, and no one wants that.</span></span>

1. <span data-ttu-id="78c38-131">**DISTINZIONE TRA MAIUSCOLE E MINUSCOLE** (tutte le lettere devono essere maiuscole)</span><span class="sxs-lookup"><span data-stu-id="78c38-131">**CASE SENSITIVE** (must be all caps)</span></span>
1. <span data-ttu-id="78c38-132">**NESSUNO SPAZIO** tra `{{`, `}}` o le parentesi</span><span class="sxs-lookup"><span data-stu-id="78c38-132">**NO SPACES** between the `{{`, `}}`, or parentheses</span></span>
1. <span data-ttu-id="78c38-133">**FORMATTAZIONE [RFC 3389](https://tools.ietf.org/html/rfc3339)** (vedi gli esempi riportati di seguito)</span><span class="sxs-lookup"><span data-stu-id="78c38-133">**STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) FORMATTING** (See examples below)</span></span>
1. <span data-ttu-id="78c38-134">Data e ora **DEVONO** essere valide</span><span class="sxs-lookup"><span data-stu-id="78c38-134">**MUST BE** a valid date and time</span></span>

### <a name="valid-formats"></a><span data-ttu-id="78c38-135">Formati validi</span><span class="sxs-lookup"><span data-stu-id="78c38-135">Valid formats</span></span>

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a><span data-ttu-id="78c38-136">Parametro per la formattazione della data</span><span class="sxs-lookup"><span data-stu-id="78c38-136">Date formatting param</span></span>

<span data-ttu-id="78c38-137">Per le date, è possibile specificare un parametro facoltativo per formattare l'output.</span><span class="sxs-lookup"><span data-stu-id="78c38-137">For dates, an optional param may be specified to format the output.</span></span>


|       <span data-ttu-id="78c38-138">Formato</span><span class="sxs-lookup"><span data-stu-id="78c38-138">Format</span></span>        |            <span data-ttu-id="78c38-139">Esempio</span><span class="sxs-lookup"><span data-stu-id="78c38-139">Example</span></span>            |
|---------------------|-------------------------------|
| <span data-ttu-id="78c38-140">`COMPACT` (impostazione predefinita)</span><span class="sxs-lookup"><span data-stu-id="78c38-140">`COMPACT` (Default)</span></span> |          <span data-ttu-id="78c38-141">"13/2/2017"</span><span class="sxs-lookup"><span data-stu-id="78c38-141">"2/13/2017"</span></span>          |
|       `SHORT`       |     <span data-ttu-id="78c38-142">"Lun, 13 feb 2017"</span><span class="sxs-lookup"><span data-stu-id="78c38-142">"Mon, Feb 13th, 2017"</span></span>     |
|       `LONG`        | <span data-ttu-id="78c38-143">"Lunedì, 13 febbraio 2017"</span><span class="sxs-lookup"><span data-stu-id="78c38-143">"Monday, February 13th, 2017"</span></span> |

