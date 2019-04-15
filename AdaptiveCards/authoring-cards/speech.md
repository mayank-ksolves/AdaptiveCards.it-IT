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
# <a name="speech-and-advanced-customization"></a>Riconoscimento vocale e la personalizzazione avanzata
Viviamo in un'epoca dell'interazione vocale tramite servizi come Cortana.  Le schede adattive progettate dal primo giorno per supportare il riconoscimento vocale, consentendo ad accesso sporadico nuovi scenari mani-full.

Il `speak` tag abilita la scheda adattiva da recapitare a un ambiente in cui una rappresentazione visiva non primaria esperienza, ad esempio a un dashboard car mentre si Guida. 

## <a name="speak-property"></a>Pronunciare proprietà
Per supportare vocale abbiamo un `speak` proprietà che contiene testo da pronunciare all'utente. Il testo può essere aggiunto usando il linguaggio di markup sintesi vocale ([SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)). SSML controlla la velocità, tono e curvatura del riconoscimento vocale.  Anche consente un rendering o trasmettere l'audio un flusso audio di sintesi vocale dal tuo servizio, offrendoti una notevole flessibilità per la personalizzazione.

Esistono due modelli per parlano di utilizzo della proprietà da un'applicazione host:

* **Il contrassegno** : quando viene recapitata una scheda, il client può scegliere di leggere la proprietà Speak per la scheda descrivere la scheda nel suo complesso.
* **Su richiesta** : per supportare un modello più dettagliato di accessibilità, l'oggetto supporta schema un speak tag per ogni elemento. Il client può leggere una proprietà Speak per ogni elemento nella scheda.

### <a name="examples"></a>Esempi

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## <a name="speech-content-design"></a>Struttura del contenuto vocale

Il contenuto progettato per il riconoscimento vocale è diverso dal contenuto progettato per la visualizzazione. Quando si progetta una scheda, si progetta un'intera esperienza visiva per presentare le informazioni a un utente in modo da delights li. Durante la progettazione per il riconoscimento vocale, dovrebbe pensare come verbalmente descrivere il contenuto in modo da delights all'utente.  
