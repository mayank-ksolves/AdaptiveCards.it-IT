---
title: Funzionalità vocali e personalizzazione avanzata
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 1dfd9b0c45a280905223e3286998b333b0a6ec6a
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2020
ms.locfileid: "76145342"
---
# <a name="speech-and-advanced-customization"></a><span data-ttu-id="3a127-102">Funzionalità vocali e personalizzazione avanzata</span><span class="sxs-lookup"><span data-stu-id="3a127-102">Speech and advanced customization</span></span>
<span data-ttu-id="3a127-103">Viviamo nell'epoca dell'interazione vocale tramite servizi come Cortana.</span><span class="sxs-lookup"><span data-stu-id="3a127-103">We live in an era of speech interaction via services like Cortana.</span></span>  <span data-ttu-id="3a127-104">Le schede adattive sono completamente progettate per supportare le funzionalità vocali, consentendo di realizzare scenari innovativi.</span><span class="sxs-lookup"><span data-stu-id="3a127-104">Adaptive cards are designed from day one to support speech, enabling cool new hands-full scenarios.</span></span>

<span data-ttu-id="3a127-105">Il tag `speak` consente di recapitare la scheda adattiva in un ambiente in cui la rappresentazione visiva non costituisce l'esperienza primaria, ad esempio il cruscotto di un'auto durante la guida.</span><span class="sxs-lookup"><span data-stu-id="3a127-105">The `speak` tag enables the adaptive card to be delivered to an environment where a visual display is not primary experience, such as to a car dashboard while driving.</span></span> 

## <a name="speak-property"></a><span data-ttu-id="3a127-106">Proprietà Speak</span><span class="sxs-lookup"><span data-stu-id="3a127-106">Speak property</span></span>
<span data-ttu-id="3a127-107">Per supportare le funzionalità vocali, è disponibile una proprietà `speak` che contiene il testo da pronunciare all'utente.</span><span class="sxs-lookup"><span data-stu-id="3a127-107">To support speech we have a `speak` property which contains text to say to the user.</span></span> <span data-ttu-id="3a127-108">Il testo può essere annotato tramite [SSML](https://msdn.microsoft.com/library/office/hh361578) (Speech Synthesis Markup Language).</span><span class="sxs-lookup"><span data-stu-id="3a127-108">The text can be annotated using speech synthesis markup language ([SSML](https://msdn.microsoft.com/library/office/hh361578)).</span></span> <span data-ttu-id="3a127-109">SSML consente di controllare la velocità, il tono e l'inflessione della voce.</span><span class="sxs-lookup"><span data-stu-id="3a127-109">SSML controls the speed, tone, and inflection of the speech.</span></span>  <span data-ttu-id="3a127-110">Consente perfino di trasmettere audio in streaming o di eseguire il rendering di flusso audio di sintesi vocale da un tuo servizio, offrendoti una notevole flessibilità per la personalizzazione.</span><span class="sxs-lookup"><span data-stu-id="3a127-110">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of flexibility for customization.</span></span>

<span data-ttu-id="3a127-111">Esistono due modelli per l'uso della proprietà Speak da parte di un'applicazione host:</span><span class="sxs-lookup"><span data-stu-id="3a127-111">There are two patterns for speak property usage by a host application:</span></span>

* <span data-ttu-id="3a127-112">**Al momento del recapito** - Quando viene recapitata una scheda, il client può scegliere di leggere la proprietà Speak per la scheda per descrivere la scheda nel suo complesso.</span><span class="sxs-lookup"><span data-stu-id="3a127-112">**On delivery** - When a card is delivered, the client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="3a127-113">**Su richiesta** - Per supportare un modello di accessibilità più avanzato, lo schema supporta un tag Speak per ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="3a127-113">**On demand** - In order to support a richer accessibility model, the schema supports a speak tag for each element.</span></span> <span data-ttu-id="3a127-114">Il client può leggere una proprietà Speak per ogni elemento nella scheda.</span><span class="sxs-lookup"><span data-stu-id="3a127-114">The client may read a Speak property  for each element in the card.</span></span>

### <a name="examples"></a><span data-ttu-id="3a127-115">Esempi</span><span class="sxs-lookup"><span data-stu-id="3a127-115">Examples</span></span>

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## <a name="speech-content-design"></a><span data-ttu-id="3a127-116">Struttura del contenuto vocale</span><span class="sxs-lookup"><span data-stu-id="3a127-116">Speech content design</span></span>

<span data-ttu-id="3a127-117">Il contenuto progettato per la voce è diverso da quello progettato per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="3a127-117">Content designed for speech is different from content designed for visual display.</span></span> <span data-ttu-id="3a127-118">Quando progetti una scheda, stai progettando un'intera esperienza visiva per presentare le informazioni a un utente in modo soddisfacente.</span><span class="sxs-lookup"><span data-stu-id="3a127-118">When you design a card, you are designing an entire visual experience to present information to a user in a way that delights them.</span></span> <span data-ttu-id="3a127-119">Durante la progettazione per la voce, devi pensare a come descrivere verbalmente il contenuto in modo soddisfacente per l'utente.</span><span class="sxs-lookup"><span data-stu-id="3a127-119">When designing for speech, you should think about how to verbally describe the content in a way that delights the user.</span></span>  
