---
title: Roadmap delle schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 05/16/2018
ms.topic: article
ms.openlocfilehash: b11edbedca83bb26d2990d029a220165f68bc1ca
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454894"
---
# <a name="future-work"></a>Lavoro futuro

Anche se è stato realizzato un ottimo lavoro nella definizione delle schede adattive, c'è ancora molto da fare. La speranza è che attraverso community attive di sviluppatori come Botness e partner eccezionali come Slack e Kik, sarà possibile creare un grande ecosistema di schede multipiattaforma.

## <a name="roadmap"></a>Roadmap

Puoi vedere [qui il roadmap corrente (non finale)](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog). Considera che è tutto soggetto a modifiche e che non è una garanzia di distribuzione.

## <a name="future-ideas"></a>Idee future

Di seguito sono riportate alcune idee future che sono ancora in fase di brainstorming. Se sei interessato a una di queste idee, invia un commento.

### <a name="great-looking-cards-from-data"></a>Schede di aspetto perfetto a partire dai dati

È noto come molti autori di schede dispongano già di dati ben definiti alla base delle loro schede. L'obiettivo è di esplorare un modello che consenta di generare schede (lato server o client) in base ai dati e a un repository di modelli ben definiti e personalizzabili.

### <a name="make-cards-responsive"></a>Creare schede reattive

I layout delle schede devono essere reattivi in base allo spazio disponibile. Le schede adattive sono adattabili a dispositivi, stili di esperienza utente e framework di interfaccia utente diversi, ma non sono ancora reattive. Per gli elementi devono essere definite proprietà aggiuntive che consentano ai produttori di schede di fornire i suggerimenti necessari alle librerie di rendering, affinché possano modificare il layout in modo intelligente e mantenere lo scopo della scheda.

### <a name="responsive-exploration"></a>Esplorazione reattiva

* Aggiungi una proprietà di **importanza** per annotare l'importanza del contenuto. In questo modo il contenuto meno importante può essere rimosso per l'adattamento allo spazio disponibile.
* Aggiungi proprietà di **vincoli** e **criteri** per descrivere come reagire se i vincoli non vengono soddisfatti. 
  * Nascondi contenuto o comprimilo riducendo le dimensioni.
  * Aggiungi una soglia che, se superata, trasforma `columnSet` in colonne carousel.

### <a name="new-element-types"></a>Nuovi tipi di elementi

* Mappe? Incorpora una mappa in una scheda con interattività o fallback in bitmap
* *Quali sono gli elementi che vuoi o che sono necessari*?

### <a name="new-rendering-libraries"></a>Nuove librerie di rendering

* React?
* Xamarin?
* *Quali framework vuoi?*
