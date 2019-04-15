---
title: Riconoscimento vocale e la personalizzazione avanzata
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 19e77b86da9d163f5fcf6a6074071a4638a8d793
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552613"
---
# <a name="speech-and-advanced-customization"></a><span data-ttu-id="ea9e6-102">Riconoscimento vocale e la personalizzazione avanzata</span><span class="sxs-lookup"><span data-stu-id="ea9e6-102">Speech and advanced customization</span></span>
<span data-ttu-id="ea9e6-103">Viviamo in un'epoca dell'interazione vocale tramite servizi come Cortana.</span><span class="sxs-lookup"><span data-stu-id="ea9e6-103">We live in an era of speech interaction via services like Cortana.</span></span>  <span data-ttu-id="ea9e6-104">Le schede adattive progettate dal primo giorno per supportare il riconoscimento vocale, consentendo ad accesso sporadico nuovi scenari mani-full.</span><span class="sxs-lookup"><span data-stu-id="ea9e6-104">Adaptive cards are designed from day one to support speech, enabling cool new hands-full scenarios.</span></span>

<span data-ttu-id="ea9e6-105">Il `speak` tag abilita la scheda adattiva da recapitare a un ambiente in cui una rappresentazione visiva non primaria esperienza, ad esempio a un dashboard car mentre si Guida.</span><span class="sxs-lookup"><span data-stu-id="ea9e6-105">The `speak` tag enables the adaptive card to be delivered to an environment where a visual display is not primary experience, such as to a car dashboard while driving.</span></span> 

## <a name="speak-property"></a><span data-ttu-id="ea9e6-106">Pronunciare proprietà</span><span class="sxs-lookup"><span data-stu-id="ea9e6-106">Speak property</span></span>
<span data-ttu-id="ea9e6-107">Per supportare vocale abbiamo un `speak` proprietà che contiene testo da pronunciare all'utente.</span><span class="sxs-lookup"><span data-stu-id="ea9e6-107">To support speech we have a `speak` property which contains text to say to the user.</span></span> <span data-ttu-id="ea9e6-108">Il testo può essere aggiunto usando il linguaggio di markup sintesi vocale ([SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)).</span><span class="sxs-lookup"><span data-stu-id="ea9e6-108">The text can be annotated using speech synthesis markup language ([SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)).</span></span> <span data-ttu-id="ea9e6-109">SSML controlla la velocità, tono e curvatura del riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="ea9e6-109">SSML controls the speed, tone, and inflection of the speech.</span></span>  <span data-ttu-id="ea9e6-110">Anche consente un rendering o trasmettere l'audio un flusso audio di sintesi vocale dal tuo servizio, offrendoti una notevole flessibilità per la personalizzazione.</span><span class="sxs-lookup"><span data-stu-id="ea9e6-110">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of flexibility for customization.</span></span>

<span data-ttu-id="ea9e6-111">Esistono due modelli per parlano di utilizzo della proprietà da un'applicazione host:</span><span class="sxs-lookup"><span data-stu-id="ea9e6-111">There are two patterns for speak property usage by a host application:</span></span>

* <span data-ttu-id="ea9e6-112">**Il contrassegno** : quando viene recapitata una scheda, il client può scegliere di leggere la proprietà Speak per la scheda descrivere la scheda nel suo complesso.</span><span class="sxs-lookup"><span data-stu-id="ea9e6-112">**On delivery** - When a card is delivered, the client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="ea9e6-113">**Su richiesta** : per supportare un modello più dettagliato di accessibilità, l'oggetto supporta schema un speak tag per ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="ea9e6-113">**On demand** - In order to support a richer accessibility model, the schema supports a speak tag for each element.</span></span> <span data-ttu-id="ea9e6-114">Il client può leggere una proprietà Speak per ogni elemento nella scheda.</span><span class="sxs-lookup"><span data-stu-id="ea9e6-114">The client may read a Speak property  for each element in the card.</span></span>

### <a name="examples"></a><span data-ttu-id="ea9e6-115">Esempi</span><span class="sxs-lookup"><span data-stu-id="ea9e6-115">Examples</span></span>

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## <a name="speech-content-design"></a><span data-ttu-id="ea9e6-116">Struttura del contenuto vocale</span><span class="sxs-lookup"><span data-stu-id="ea9e6-116">Speech content design</span></span>

<span data-ttu-id="ea9e6-117">Il contenuto progettato per il riconoscimento vocale è diverso dal contenuto progettato per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ea9e6-117">Content designed for speech is different from content designed for visual display.</span></span> <span data-ttu-id="ea9e6-118">Quando si progetta una scheda, si progetta un'intera esperienza visiva per presentare le informazioni a un utente in modo da delights li.</span><span class="sxs-lookup"><span data-stu-id="ea9e6-118">When you design a card, you are designing an entire visual experience to present information to a user in a way that delights them.</span></span> <span data-ttu-id="ea9e6-119">Durante la progettazione per il riconoscimento vocale, dovrebbe pensare come verbalmente descrivere il contenuto in modo da delights all'utente.</span><span class="sxs-lookup"><span data-stu-id="ea9e6-119">When designing for speech, you should think about how to verbally describe the content in a way that delights the user.</span></span>  
