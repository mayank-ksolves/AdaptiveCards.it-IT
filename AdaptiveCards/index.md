---
title: Panoramica delle schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 27c7d5ac7da3ae182667cbf8efa90d29f110d1d3
ms.sourcegitcommit: ef03c0eff3272a36cfa88daf99c4d57e4bae9599
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/08/2019
ms.locfileid: "72042526"
---
# <a name="adaptive-cards-overview"></a>Panoramica delle schede adattive 

Le schede adattive sono un formato aperto per lo scambio di schede che consente agli sviluppatori di scambiare contenuti dell'interfaccia utente in un modo coerente e comune.

<video controls width="100%" poster="./content/videoposter.png">
    <source src="https://adaptivecardsblob.blob.core.windows.net/assets/AdaptiveCardsOverviewVideo.mp4" type="video/mp4">
</video>

## <a name="how-they-work"></a>Come funzionano

Gli [**autori di schede**](authoring-cards/getting-started.md) descrivono il contenuto come un semplice oggetto JSON. Tale contenuto verrà quindi sottoposto a rendering in modo nativo all'interno un'[**applicazione host**](rendering-cards/getting-started.md), adattandolo automaticamente all'aspetto dell'host.

Ad esempio, Contoso Bot può creare una scheda adattiva tramite Bot Framework. Quando viene recapitata a Skype, avrà l'aspetto di una scheda di Skype. Se lo stesso payload viene inviato a Microsoft Teams, avrà un aspetto coerente con Microsoft Teams. Con la diffusione del supporto delle schede adattive da parte di più app host, lo stesso payload verrà attivato automaticamente all'interno di queste applicazioni, sempre con un aspetto nativo per l'app.

Per gli utenti il vantaggio è che questi elementi hanno un aspetto familiare. Il vantaggio per le app host è la possibilità di controllare l'esperienza utente. Gli autori di schede hanno l'opportunità di ottenere una maggiore copertura per il contenuto senza lavoro aggiuntivo.

## <a name="goals"></a>Obiettivi 

Le schede adattive devono essere:

* **Portabili** - Per qualsiasi app, dispositivo e framework dell'interfaccia utente
* **Aperte** - Librerie e schema sono open source e condivisi
* **Convenienti** - Facili da definire, facili da utilizzare
* **Espressive** - Destinate ai contenuti di ampio spettro che gli sviluppatori desiderano produrre
* **Puramente dichiarative** - Non è necessario o consentito codice
* **Con stile automatico** - In base alle linee guida per marchio ed esperienza utente dell'applicazione host

## <a name="for-card-authors"></a>Per gli autori delle schede
Le schede adattive offrono agli autori i vantaggi seguenti:

* **Un solo schema** - Un singolo formato che offre la possibilità di ridurre al minimo i costi per la creazione di una scheda, massimizzando il numero di posizioni in cui può essere usata.
* **Maggiore libertà di espressione** - Il contenuto può essere allineato al messaggio con maggiore precisione, perché si ha a disposizione una tavolozza più completa.
* **Ampia copertura** - Il contenuto sarà supportato da una più vasta gamma di applicazioni senza dover apprendere nuovi schemi.
* **Controlli di input** - La scheda può includere controlli di input per raccogliere informazioni dall'utente che la sta visualizzando.
* **Migliori strumenti** - Un ecosistema aperto significa strumenti migliori condivisi da tutti.

## <a name="for-experience-owners"></a>Per i proprietari dell'esperienza
Gli sviluppatori di app che vogliono attingere a un ecosistema di contenuti di terze parti apprezzeranno le schede adattive per i motivi seguenti:

* **Esperienza utente coerente** - Si può garantire un'esperienza coerente per gli utenti, perché si è proprietari dello stile della scheda sottoposta a rendering.
* **Prestazioni native** - È possibile ottenere prestazioni native grazie all'utilizzo diretto del framework dell'interfaccia utente.
* **Sicurezza** - Il contenuto viene distribuito in payload sicuri in modo da non dover aprire il framework dell'interfaccia utente a markup non elaborato e script.
* **Facilità di implementazione** - Librerie pronte e facilmente integrabili in qualsiasi piattaforma supportata. 
* **Documentazione gratuita** - Si risparmia tempo perché non è necessario inventare, implementare e documentare uno schema proprietario.
* **Strumenti condivisi** - Si risparmia tempo perché non è necessario creare strumenti personalizzati.

## <a name="core-design-principles"></a>Principi di progettazione di base 

Le schede adattive sono basate su un set di [principi guida](resources/principles.md) che si sono rivelati utili per mantenere sotto controllo la progettazione. 

### <a name="semantic-instead-of-pixel-perfect"></a>Semantica invece di perfezione al pixel
Si è cercato il più possibile di concentrarsi su valori semantici e concetti, piuttosto che sul puro layout perfetto al pixel. Gli esempi di espressione semantica vengono visualizzati in vari colori e dimensioni e in elementi come FactSet e ImageSet. Tutti questi elementi consentono all'applicazione host di prendere decisioni migliori sull'aspetto effettivo.

### <a name="card-authors-own-the-content-host-app-owns-the-look-and-feel"></a>Gli autori delle schede sono i proprietari del contenuto, l'app host è proprietaria dell'aspetto
Gli autori delle schede decidono cosa vogliono dire, ma l'applicazione in cui vengono visualizzate le schede ne determina l'aspetto nel contesto.

### <a name="keep-it-simple-but-expressive"></a>Semplicità ed espressività
Le schede adattive devono essere espressive e generiche, ma l'intenzione non è quella di creare un framework dell'interfaccia utente.  L'obiettivo è realizzare un livello intermedio "sufficientemente espressivo" nello stesso modo in cui Markdown è sufficientemente espressivo per i documenti.

Focalizzando l'attenzione su semplicità ed espressività, con Markdown si è riusciti a creare una descrizione coerente e semplice del contenuto del documento.  Nello stesso modo, Microsoft ritiene che le schede adattive possano diventare uno strumento semplice ed espressivo per descrivere il contenuto della scheda.

### <a name="when-in-doubt-keep-it-out"></a>In caso di dubbi, tralasciare
È più semplice aggiungere in un secondo momento che convivere con una scelta infelice. Se ci si ritrova a discutere se aggiungere o meno un elemento, è consigliabile decidere di ometterlo.  È sempre più semplice aggiungere una proprietà piuttosto che convivere con una proprietà legacy che sarebbe stato preferibile non dover supportare.


## <a name="build-2019-session"></a>Sessione dell'evento Build 2019

La sessione seguente che si è svolta alla conferenza Microsoft Build presenta le schede adattive in diversi casi d'uso. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/wT1yFr_j6IM" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
