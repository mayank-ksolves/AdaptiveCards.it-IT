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
# <a name="text-features"></a><span data-ttu-id="0fe2a-102">Funzioni di testo</span><span class="sxs-lookup"><span data-stu-id="0fe2a-102">Text features</span></span>

<span data-ttu-id="0fe2a-103">`TextBlock` offre alcune funzionalità avanzate di formattazione e la localizzazione del testo.</span><span class="sxs-lookup"><span data-stu-id="0fe2a-103">`TextBlock` offers some advanced features for formatting and localizing the text.</span></span>

## <a name="markdown"></a><span data-ttu-id="0fe2a-104">Markdown</span><span class="sxs-lookup"><span data-stu-id="0fe2a-104">Markdown</span></span>
<span data-ttu-id="0fe2a-105">Per supportare inline markup, supporta le schede adattive una **subset** della sintassi di Markdown.</span><span class="sxs-lookup"><span data-stu-id="0fe2a-105">To support inline markup, Adaptive Cards support a **subset** of Markdown syntax.</span></span>

<span data-ttu-id="0fe2a-106">_È supportato_</span><span class="sxs-lookup"><span data-stu-id="0fe2a-106">_Supported_</span></span>

| <span data-ttu-id="0fe2a-107">Stile del testo</span><span class="sxs-lookup"><span data-stu-id="0fe2a-107">Text Style</span></span>      | <span data-ttu-id="0fe2a-108">Markdown</span><span class="sxs-lookup"><span data-stu-id="0fe2a-108">Markdown</span></span> |
|-----------------|-----|
| <span data-ttu-id="0fe2a-109">**Grassetto**</span><span class="sxs-lookup"><span data-stu-id="0fe2a-109">**Bold**</span></span>        | ```**Bold**``` |
| <span data-ttu-id="0fe2a-110">_Corsivo_</span><span class="sxs-lookup"><span data-stu-id="0fe2a-110">_Italic_</span></span>        | ```_Italic_``` |
| <span data-ttu-id="0fe2a-111">Elenco puntato</span><span class="sxs-lookup"><span data-stu-id="0fe2a-111">Bullet list</span></span>     | ```- Item 1\r- Item 2\r- Item 3``` | 
| <span data-ttu-id="0fe2a-112">Elenco numerato</span><span class="sxs-lookup"><span data-stu-id="0fe2a-112">Numbered list</span></span>   | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="0fe2a-113">Collegamenti ipertestuali</span><span class="sxs-lookup"><span data-stu-id="0fe2a-113">Hyperlinks</span></span>      | ```[Title](url)``` |

<span data-ttu-id="0fe2a-114">_Non è supportato_</span><span class="sxs-lookup"><span data-stu-id="0fe2a-114">_Not supported_</span></span>

* <span data-ttu-id="0fe2a-115">Intestazioni</span><span class="sxs-lookup"><span data-stu-id="0fe2a-115">Headers</span></span>
* <span data-ttu-id="0fe2a-116">Tabelle</span><span class="sxs-lookup"><span data-stu-id="0fe2a-116">Tables</span></span>
* <span data-ttu-id="0fe2a-117">Immagini</span><span class="sxs-lookup"><span data-stu-id="0fe2a-117">Images</span></span>
* <span data-ttu-id="0fe2a-118">Qualsiasi elemento non nella tabella precedente</span><span class="sxs-lookup"><span data-stu-id="0fe2a-118">Anything not in the table above</span></span>

### <a name="markdown-example"></a><span data-ttu-id="0fe2a-119">Esempio di markdown</span><span class="sxs-lookup"><span data-stu-id="0fe2a-119">Markdown Example</span></span>

<span data-ttu-id="0fe2a-120">Il seguente payload visualizzerebbe simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="0fe2a-120">The below payload would render something like this:</span></span>

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

## <a name="datetime-formatting-and-localization"></a><span data-ttu-id="0fe2a-122">Formattazione di data/ora e la localizzazione</span><span class="sxs-lookup"><span data-stu-id="0fe2a-122">Date/Time formatting and localization</span></span>

<span data-ttu-id="0fe2a-123">In alcuni casi non è possibile sapere il fuso orario dell'utente che ha ricevuto la scheda, in modo che le schede adattive offre `DATE()` e `TIME()` formattazione funzioni per localizzare automaticamente l'ora nel dispositivo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="0fe2a-123">Sometimes you won't know the timezone of the user receiving the card, so Adaptive Cards offers `DATE()` and `TIME()` formatting functions to automatically localize the time on the target device.</span></span>

### <a name="datetime-example"></a><span data-ttu-id="0fe2a-124">Esempio di data/ora</span><span class="sxs-lookup"><span data-stu-id="0fe2a-124">Date/Time Example</span></span>

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

<span data-ttu-id="0fe2a-125">Verrà visualizzata la scheda precedente:</span><span class="sxs-lookup"><span data-stu-id="0fe2a-125">The above card will display:</span></span> 

> <span data-ttu-id="0fe2a-126">**I pacchetto arriveranno Mar, il 14 febbraio 2017 6:00**</span><span class="sxs-lookup"><span data-stu-id="0fe2a-126">**Your package will arrive on Tue, Feb 14th, 2017 at 6:00 AM**</span></span>

### <a name="datetime-function-rules"></a><span data-ttu-id="0fe2a-127">Data/ora delle regole (funzione)</span><span class="sxs-lookup"><span data-stu-id="0fe2a-127">Date/Time function rules</span></span>

<span data-ttu-id="0fe2a-128">Sono disponibili alcune regole consentono la corretta interpretazione di funzioni di data/ora in ogni piattaforma.</span><span class="sxs-lookup"><span data-stu-id="0fe2a-128">There are some rules to properly interpret the the date/time functions on every platform.</span></span> <span data-ttu-id="0fe2a-129">Se le regole non vengono soddisfatti, verrà visualizzata all'utente la stringa non elaborata e nessuno vuole che.</span><span class="sxs-lookup"><span data-stu-id="0fe2a-129">If the rules aren't met then the raw string will be displayed to the user, and no one wants that.</span></span>

1. <span data-ttu-id="0fe2a-130">**Distinzione maiuscole / MINUSCOLE** (devono essere tutte maiuscole)</span><span class="sxs-lookup"><span data-stu-id="0fe2a-130">**CASE SENSITIVE** (must be all caps)</span></span>
1. <span data-ttu-id="0fe2a-131">**SENZA spazi** tra il `{{`, `}}`, parentesi o parentesi</span><span class="sxs-lookup"><span data-stu-id="0fe2a-131">**NO SPACES** between the `{{`, `}}`, or parentheses</span></span>
1. <span data-ttu-id="0fe2a-132">**STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) formattazione** (vedere esempi riportati di seguito)</span><span class="sxs-lookup"><span data-stu-id="0fe2a-132">**STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) FORMATTING** (See examples below)</span></span>
1. <span data-ttu-id="0fe2a-133">**DEVE essere** valido data e ora</span><span class="sxs-lookup"><span data-stu-id="0fe2a-133">**MUST BE** a valid date and time</span></span>

### <a name="valid-formats"></a><span data-ttu-id="0fe2a-134">Formati validi</span><span class="sxs-lookup"><span data-stu-id="0fe2a-134">Valid formats</span></span>

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a><span data-ttu-id="0fe2a-135">Date (formattazione) param</span><span class="sxs-lookup"><span data-stu-id="0fe2a-135">Date formatting param</span></span>

<span data-ttu-id="0fe2a-136">Per le date, un parametro facoltativo può essere specificata per formattare l'output.</span><span class="sxs-lookup"><span data-stu-id="0fe2a-136">For dates, an optional param may be specified to format the output.</span></span>


|       <span data-ttu-id="0fe2a-137">Formato</span><span class="sxs-lookup"><span data-stu-id="0fe2a-137">Format</span></span>        |            <span data-ttu-id="0fe2a-138">Esempio</span><span class="sxs-lookup"><span data-stu-id="0fe2a-138">Example</span></span>            |
|---------------------|-------------------------------|
| <span data-ttu-id="0fe2a-139">`COMPACT` (Impostazione predefinita)</span><span class="sxs-lookup"><span data-stu-id="0fe2a-139">`COMPACT` (Default)</span></span> |          <span data-ttu-id="0fe2a-140">"2/13/2017"</span><span class="sxs-lookup"><span data-stu-id="0fe2a-140">"2/13/2017"</span></span>          |
|       `SHORT`       |     <span data-ttu-id="0fe2a-141">"Mon 13 febbraio 2017"</span><span class="sxs-lookup"><span data-stu-id="0fe2a-141">"Mon, Feb 13th, 2017"</span></span>     |
|       `LONG`        | <span data-ttu-id="0fe2a-142">"Lunedì 13 febbraio 2017"</span><span class="sxs-lookup"><span data-stu-id="0fe2a-142">"Monday, February 13th, 2017"</span></span> |

