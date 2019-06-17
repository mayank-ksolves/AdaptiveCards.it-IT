---
title: Guida di orientamento per le schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 05/16/2018
ms.topic: article
ms.openlocfilehash: f879c164b3471347ba8fa058827b3d79b09be4cd
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2019
ms.locfileid: "67138004"
---
# <a name="future-work"></a>Lavoro futuro

Anche se sono stati apportati corso eccellente che definisce le schede adattive, è ancora presente un numero elevato di operazioni da eseguire. La nostra speranza è che tramite le community di sviluppatori attivi, ad esempio botness e i partner ideali come Slack e Kik, possiamo creare un grande ecosistema di schede multipiattaforma.

## <a name="roadmap"></a>Guida di orientamento

È possibile visualizzare nostri [corrente (non finali) Guida di orientamento qui](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog). Si noti che qualsiasi elemento in questa posizione è soggetta a modifiche e non è una garanzia di spedizione.

## <a name="future-ideas"></a>Idee future

Di seguito è riportate alcune idee future è disponibile, che sono semplicemente in fase di definizione. Se è interessati a uno di questi, segnalarlo in un commento.

### <a name="great-looking-cards-from-data"></a>Schede dall'aspetto professionale eccezionali dai dati

Sappiamo che molti autori di smart card già disponibili dati ben definiti dietro le relative schede. È intenzione di Microsoft per esplorare un modello di creazione di modelli che consentirebbe a schede deve essere generato (sul lato server o lato client) in base i dati e un repository dei modelli ben definiti e personalizzabili.

### <a name="make-cards-responsive"></a>Migliorare schede di risposta

Layout delle smart card deve essere reattive allo spazio disponibile. Le schede adattive sono adattabili ai diversi dispositivi, gli stili dell'esperienza utente ed e Framework dell'interfaccia utente, ma non sono reattivi ancora. È necessario definire le proprietà aggiuntive sugli elementi che consentono di producer di smart card fornire i riferimenti necessari per le librerie per il rendering in modo che cambiano in modo intelligente il layout in modo che mantiene la finalità della scheda.

### <a name="responsive-exploration"></a>Esplorazione reattive

* Aggiungere un **importanza** proprietà che Annota l'importanza del contenuto. Contenuto meno importante può essere eliminato in base allo spazio disponibile
* Aggiungere **vincoli** e **criterio** proprietà che descrivono come reagire quando non possono essere soddisfatti i vincoli. 
  * Nascondere il contenuto o comprimere il contenuto a dimensioni inferiori.
  * Aggiunge una soglia che, quando superata, viene modificato `columnSet` alla sequenza di colonne.

### <a name="new-element-types"></a>Nuovi tipi di elementi

* Mappe? -incorporare una mappa in una scheda con funzionalità interattive o di fallback per la mappa di bit
* *Quali elementi è preferibile o necessario*?

### <a name="new-rendering-libraries"></a>Nuove librerie di rendering

* React?
* Xamarin?
* *Quali Framework di eseguire?*
