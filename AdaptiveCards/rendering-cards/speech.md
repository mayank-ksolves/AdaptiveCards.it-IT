---
title: La gestione di riconoscimento vocale
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 64eeaefbc2ac775b69bd48cc853beb729cb2c37f
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2019
ms.locfileid: "67137994"
---
# <a name="handling-speech"></a><span data-ttu-id="19c78-102">La gestione di riconoscimento vocale</span><span class="sxs-lookup"><span data-stu-id="19c78-102">Handling speech</span></span>

<span data-ttu-id="19c78-103">Supporto vocale ha le schede adattive il `speak` proprietà che contiene informazioni sul modo in cui debba essere letto una scheda a un utente.</span><span class="sxs-lookup"><span data-stu-id="19c78-103">To support speech adaptive Cards has the `speak` property which contains information on how a card should be read aloud to a user.</span></span>

<span data-ttu-id="19c78-104">Il tag di riconoscimento vocale può essere annotato usando [markup SSML](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span><span class="sxs-lookup"><span data-stu-id="19c78-104">The speech tag can be annotated using  [SSML markup](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span></span> <span data-ttu-id="19c78-105">SSML offre un controllo capacità della velocità, segnale acustico, flessione del riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="19c78-105">SSML gives you the ability control the speed, tone, inflection of the speech.</span></span>  <span data-ttu-id="19c78-106">Anche consente un rendering o trasmettere l'audio un flusso audio di sintesi vocale dal tuo servizio, offrendoti una grande quantità di personalizzazione.</span><span class="sxs-lookup"><span data-stu-id="19c78-106">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of customization.</span></span>

<span data-ttu-id="19c78-107">Esistono 2 modelli per parlano di utilizzo della proprietà da un'applicazione host:</span><span class="sxs-lookup"><span data-stu-id="19c78-107">There are 2 patterns for speak property usage by a host application:</span></span>
* <span data-ttu-id="19c78-108">**il contrassegno** : quando una scheda viene recapitata un client può scegliere di leggere la proprietà Speak per la scheda descrivere la scheda nel suo complesso.</span><span class="sxs-lookup"><span data-stu-id="19c78-108">**on delivery** - When a card is delivered a client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="19c78-109">**su richiesta** : per supportare un modello più dettagliato di accessibilità l'oggetto supporta schema un speak tag per ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="19c78-109">**on demand** - In order to support a richer accessibility model the schema supports a speak tag per element.</span></span>  
<span data-ttu-id="19c78-110">In questo modo i client possono leggere ogni elemento ai destinatari con requisiti di accessibilità.</span><span class="sxs-lookup"><span data-stu-id="19c78-110">This allows for clients to read each element to recipients with accessibility requirements.</span></span>

