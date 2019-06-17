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
# <a name="handling-speech"></a>La gestione di riconoscimento vocale

Supporto vocale ha le schede adattive il `speak` proprietà che contiene informazioni sul modo in cui debba essere letto una scheda a un utente.

Il tag di riconoscimento vocale può essere annotato usando [markup SSML](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx). SSML offre un controllo capacità della velocità, segnale acustico, flessione del riconoscimento vocale.  Anche consente un rendering o trasmettere l'audio un flusso audio di sintesi vocale dal tuo servizio, offrendoti una grande quantità di personalizzazione.

Esistono 2 modelli per parlano di utilizzo della proprietà da un'applicazione host:
* **il contrassegno** : quando una scheda viene recapitata un client può scegliere di leggere la proprietà Speak per la scheda descrivere la scheda nel suo complesso.
* **su richiesta** : per supportare un modello più dettagliato di accessibilità l'oggetto supporta schema un speak tag per ogni elemento.  
In questo modo i client possono leggere ogni elemento ai destinatari con requisiti di accessibilità.

