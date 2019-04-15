---
title: La gestione di riconoscimento vocale
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: daea48607376c84f0e0f0af9450cac7dcdf67c0e
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552483"
---
# <a name="handling-speech"></a><span data-ttu-id="5da17-102">La gestione di riconoscimento vocale</span><span class="sxs-lookup"><span data-stu-id="5da17-102">Handling speech</span></span>

<span data-ttu-id="5da17-103">Supporto vocale ha le schede adattive il `speak` proprietà che contiene informazioni sul modo in cui debba essere letto una scheda a un utente.</span><span class="sxs-lookup"><span data-stu-id="5da17-103">To support speech adaptive Cards has the `speak` property which contains information on how a card shoudl be read aloud to a user.</span></span>

<span data-ttu-id="5da17-104">Il tag di riconoscimento vocale può essere annotato usando [markup SSML](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span><span class="sxs-lookup"><span data-stu-id="5da17-104">The speech tag can be annotated using  [SSML markup](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span></span> <span data-ttu-id="5da17-105">SSML offre un controllo capacità della velocità, segnale acustico, flessione del riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="5da17-105">SSML gives you the ability control the speed, tone, inflection of the speech.</span></span>  <span data-ttu-id="5da17-106">Anche consente un rendering o trasmettere l'audio un flusso audio di sintesi vocale dal tuo servizio, offrendoti una grande quantità di personalizzazione.</span><span class="sxs-lookup"><span data-stu-id="5da17-106">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of customization.</span></span>

<span data-ttu-id="5da17-107">Esistono 2 modelli per parlano di utilizzo della proprietà da un'applicazione host:</span><span class="sxs-lookup"><span data-stu-id="5da17-107">There are 2 patterns for speak property usage by a host application:</span></span>
* <span data-ttu-id="5da17-108">**il contrassegno** : quando una scheda viene recapitata un client può scegliere di leggere la proprietà Speak per la scheda descrivere la scheda nel suo complesso.</span><span class="sxs-lookup"><span data-stu-id="5da17-108">**on delivery** - When a card is delivered a client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="5da17-109">**su richiesta** : per supportare un modello più dettagliato di accessibilità l'oggetto supporta schema un speak tag per ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="5da17-109">**on demand** - In order to support a richer accessibility model the schema supports a speak tag per element.</span></span>  
<span data-ttu-id="5da17-110">In questo modo i client possono leggere ogni elemento ai destinatari con requisiti di accessibilità.</span><span class="sxs-lookup"><span data-stu-id="5da17-110">This allows for clients to read each element to recipients with accessibility requirements.</span></span>

