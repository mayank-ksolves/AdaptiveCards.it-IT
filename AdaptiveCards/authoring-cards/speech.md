---
title: Funzionalità vocali e personalizzazione avanzata
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 19e77b86da9d163f5fcf6a6074071a4638a8d793
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2019
ms.locfileid: "59552613"
---
# <a name="speech-and-advanced-customization"></a>Funzionalità vocali e personalizzazione avanzata
Viviamo nell'epoca dell'interazione vocale tramite servizi come Cortana.  Le schede adattive sono completamente progettate per supportare le funzionalità vocali, consentendo di realizzare scenari innovativi.

Il tag `speak` consente di recapitare la scheda adattiva in un ambiente in cui la rappresentazione visiva non costituisce l'esperienza primaria, ad esempio il cruscotto di un'auto durante la guida. 

## <a name="speak-property"></a>Proprietà Speak
Per supportare le funzionalità vocali, è disponibile una proprietà `speak` che contiene il testo da pronunciare all'utente. Il testo può essere annotato tramite [SSML](https://msdn.microsoft.com/en-us/library/office/hh361578) (Speech Synthesis Markup Language). SSML consente di controllare la velocità, il tono e l'inflessione della voce.  Consente perfino di trasmettere audio in streaming o di eseguire il rendering di flusso audio di sintesi vocale da un tuo servizio, offrendoti una notevole flessibilità per la personalizzazione.

Esistono due modelli per l'uso della proprietà Speak da parte di un'applicazione host:

* **Al momento del recapito** - Quando viene recapitata una scheda, il client può scegliere di leggere la proprietà Speak per la scheda per descrivere la scheda nel suo complesso.
* **Su richiesta** - Per supportare un modello di accessibilità più avanzato, lo schema supporta un tag Speak per ogni elemento. Il client può leggere una proprietà Speak per ogni elemento nella scheda.

### <a name="examples"></a>Esempi

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## <a name="speech-content-design"></a>Struttura del contenuto vocale

Il contenuto progettato per la voce è diverso da quello progettato per la visualizzazione. Quando progetti una scheda, stai progettando un'intera esperienza visiva per presentare le informazioni a un utente in modo soddisfacente. Durante la progettazione per la voce, devi pensare a come descrivere verbalmente il contenuto in modo soddisfacente per l'utente.  
