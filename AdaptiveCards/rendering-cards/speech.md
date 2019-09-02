---
title: Gestione delle funzionalità vocali
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 64eeaefbc2ac775b69bd48cc853beb729cb2c37f
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2019
ms.locfileid: "67137994"
---
# <a name="handling-speech"></a><span data-ttu-id="aba99-102">Gestione delle funzionalità vocali</span><span class="sxs-lookup"><span data-stu-id="aba99-102">Handling speech</span></span>

<span data-ttu-id="aba99-103">Per supportare le funzionalità vocali, le schede adattive usano la proprietà `speak`, che contiene informazioni su come deve essere letta una scheda a un utente.</span><span class="sxs-lookup"><span data-stu-id="aba99-103">To support speech adaptive Cards has the `speak` property which contains information on how a card should be read aloud to a user.</span></span>

<span data-ttu-id="aba99-104">Il tag della funzionalità vocale può essere annotato usando il [markup SSML](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span><span class="sxs-lookup"><span data-stu-id="aba99-104">The speech tag can be annotated using  [SSML markup](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span></span> <span data-ttu-id="aba99-105">SSML offre la possibilità di controllare la velocità, il tono e l'inflessione per la funzionalità vocale.</span><span class="sxs-lookup"><span data-stu-id="aba99-105">SSML gives you the ability control the speed, tone, inflection of the speech.</span></span>  <span data-ttu-id="aba99-106">Consente perfino di trasmettere audio in streaming o di eseguire il rendering di flusso audio di sintesi vocale da un tuo servizio, offrendoti notevoli opportunità di personalizzazione.</span><span class="sxs-lookup"><span data-stu-id="aba99-106">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of customization.</span></span>

<span data-ttu-id="aba99-107">Esistono due modelli per l'uso della proprietà Speak da parte di un'applicazione host:</span><span class="sxs-lookup"><span data-stu-id="aba99-107">There are 2 patterns for speak property usage by a host application:</span></span>
* <span data-ttu-id="aba99-108">**Al momento del recapito**: quando viene recapitata una scheda, un client può scegliere di leggere la proprietà Speak della scheda per descrivere la scheda nel suo complesso.</span><span class="sxs-lookup"><span data-stu-id="aba99-108">**on delivery** - When a card is delivered a client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="aba99-109">**Su richiesta**: per supportare un modello di accessibilità più avanzato, lo schema supporta un tag Speak per ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="aba99-109">**on demand** - In order to support a richer accessibility model the schema supports a speak tag per element.</span></span>  
<span data-ttu-id="aba99-110">In questo modo i client possono leggere ogni elemento ai destinatari con requisiti di accessibilità.</span><span class="sxs-lookup"><span data-stu-id="aba99-110">This allows for clients to read each element to recipients with accessibility requirements.</span></span>

