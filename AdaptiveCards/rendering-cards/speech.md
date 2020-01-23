---
title: Gestione delle funzionalità vocali
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: fb56c97da3cca776da0fc7ea65a9726c8826e910
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145541"
---
# <a name="handling-speech"></a>Gestione delle funzionalità vocali

Per supportare le funzionalità vocali, le schede adattive usano la proprietà `speak`, che contiene informazioni su come deve essere letta una scheda a un utente.

Il tag della funzionalità vocale può essere annotato usando il [markup SSML](https://msdn.microsoft.com/library/office/hh361578(v=office.14).aspx). SSML offre la possibilità di controllare la velocità, il tono e l'inflessione per la funzionalità vocale.  Consente perfino di trasmettere audio in streaming o di eseguire il rendering di flusso audio di sintesi vocale da un tuo servizio, offrendoti notevoli opportunità di personalizzazione.

Esistono due modelli per l'uso della proprietà Speak da parte di un'applicazione host:
* **Al momento del recapito**: quando viene recapitata una scheda, un client può scegliere di leggere la proprietà Speak della scheda per descrivere la scheda nel suo complesso.
* **Su richiesta**: per supportare un modello di accessibilità più avanzato, lo schema supporta un tag Speak per ogni elemento.  
In questo modo i client possono leggere ogni elemento ai destinatari con requisiti di accessibilità.

