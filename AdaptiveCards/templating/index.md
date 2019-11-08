---
title: Panoramica della creazione di modelli
author: matthidinger
ms.author: mahiding
ms.date: 07/29/2019
ms.topic: article
ms.openlocfilehash: 11ade4c2a41111f372873ea9a0677fe823c5b0ab
ms.sourcegitcommit: 16a274ce5596001a1c5ab252d9d2a3db6a5a9a0d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73750418"
---
# <a name="adaptive-cards-templating-preview"></a>Creazione di modelli di Schede adattive (anteprima)

Siamo lieti di condividere un'anteprima dei nuovi strumenti che ti aiuteranno a **creare**, **,riutilizzare** e **condividere** Schede adattive. 

> [!IMPORTANT] 
> 
> Queste funzionalità sono disponibili **in anteprima e sono soggette a modifiche**. Il tuo feedback non solo è apprezzato, ma è anche fondamentale per aiutarci a offrire le funzionalità di cui **tu** hai bisogno.

## <a name="how-can-templating-help-you"></a>Quali sono i vantaggi della creazione di modelli?

La creazione di modelli consente di separare i **dati** dal **layout** in una scheda adattiva. 

### <a name="it-helps-design-a-card-once-and-then-populate-it-with-real-data"></a>Permette di progettare una scheda una sola volta e quindi di popolarla con dati reali

Oggi non è possibile creare una scheda tramite [Designer di Schede adattive](https://adaptivecards.io/designer) e usare questo codice JSON per popolare il payload con **contenuto dinamico**. Per ottenere questo risultato, è necessario scrivere codice personalizzato per compilare una stringa JSON oppure usare gli SDK del modello a oggetti per creare un modello a oggetti che rappresenta la scheda, quindi serializzarlo in JSON. In entrambi i casi, Designer offre un'operazione unidirezionale da eseguire una sola volta e non semplifica la modifica della progettazione della scheda in un secondo momento dopo la conversione in codice.

### <a name="it-makes-tranmissions-over-the-wire-smaller"></a>Riduce le dimensioni delle trasmissioni in rete

Immagina un mondo in cui sia possibile combinare un modello e i dati **direttamente nel client**. Significa che se usi lo stesso modello più volte, oppure vuoi aggiornarlo con nuovi dati, è sufficiente inviare i nuovi dati al dispositivo e quindi riutilizzare lo stesso modello più volte.

### <a name="it-helps-you-create-a-great-looking-card-from-just-the-data-you-provide"></a>Consente di creare una scheda dall'aspetto accattivante solo dai dati forniti

Le schede adattive sono fantastiche, ma se fosse possibile evitare di scriverne una per ogni contenuto da visualizzare agli utenti? Con un servizio di modelli (descritto di seguito) possiamo creare un mondo in cui tutti possono contribuire, scoprire e condividere modelli per qualsiasi tipo di dati. 

Condividi all'interno dei progetti, nell'organizzazione o con l'intera rete Internet.

### <a name="ai-and-other-services-could-improve-user-experiences"></a>L'intelligenza artificiale e altri servizi potrebbero migliorare l'esperienza utente

Separando i dati dal contenuto, l'intelligenza artificiale e altri servizi possono "ragionare" sui dati nelle schede che vediamo e migliorare la produttività degli utenti o aiutarci a trovare quello che cerchiamo.

## <a name="what-is-adaptive-cards-templating"></a>Cos'è la creazione di modelli di Schede adattive?

È costituita da tre componenti principali:

1. Il **[linguaggio del modello](language.md)** è la sintassi usata per la creazione di un modello. Designer consente anche di visualizzare in anteprima i modelli in fase di progettazione includendo "dati di esempio".
2. Gli **[SDK di creazione modelli](sdk.md)** esistono in tutte le piattaforma di Schede adattive supportate. Questi SDK consentono di popolare un modello con dati reali, nel back-end o direttamente nel client. 
3. Il **[servizio modelli](service.md)** è un modello di verifica che consente a chiunque di trovare, contribuire e condividere un set di modelli ben noti.

## <a name="template-language"></a>Linguaggio del modello

Il linguaggio del modello è la sintassi usata per creare un modello di scheda adattiva. 

> [!NOTE]
> 
> Segui l'esempio riportato di seguito aprendo una nuova scheda all'indirizzo
>
> **https://adaptivecards.io/designer**
> 
> Fai clic sul pulsante **Preview Mode** (Modalità di anteprima) per alternare tra la modalità di progettazione e la modalità di anteprima.

![Screenshot di Designer](content/2019-08-01-13-58-27.png)

Il componente Designer appena aggiornato aggiunge il supporto per la creazione di modelli e fornisce **dati di esempio** per visualizzare l'anteprima della scheda in fase di progettazione.

Incolla l'esempio seguente nel riquadro **Card Payload Editor** (Editor payload scheda): 

**EmployeeCardTemplate.json**

```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "ColumnSet",
            "style": "accent",
            "bleed": true,
            "columns": [
                {
                    "type": "Column",
                    "width": "auto",
                    "items": [
                        {
                            "type": "Image",
                            "url": "{photo}",
                            "altText": "Profile picture",
                            "size": "Small",
                            "style": "Person"
                        }
                    ]
                },
                {
                    "type": "Column",
                    "width": "stretch",
                    "items": [
                        {
                            "type": "TextBlock",
                            "text": "Hi {name}!",
                            "size": "Medium"
                        },
                        {
                            "type": "TextBlock",
                            "text": "Here's a bit about your org...",
                            "spacing": "None"
                        }
                    ]
                }
            ]
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: **{manager.name}**"
        },
        {
            "type": "TextBlock",
            "text": "Your peers are:"
        },
        {
            "type": "FactSet",
            "facts": [
                {
                    "$data": "{peers}",
                    "title": "{name}",
                    "value": "{title}"
                }
            ]
        }
    ]
}
```

Quindi incolla i dati JSON seguenti in **Sample Data Editor** (Editor dati di esempio). 

I **dati di esempio** ti consentono di vedere esattamente come verrà visualizzata la scheda in fase di esecuzione quando verranno passati i dati effettivi.

**EmployeeData**

```json
{
    "name": "Matt",
    "photo": "https://pbs.twimg.com/profile_images/3647943215/d7f12830b3c17a5a9e4afcc370e3a37e_400x400.jpeg",
    "manager": {
        "name": "Thomas",
        "title": "PM Lead"
    },
    "peers": [
        {
            "name": "Lei",
            "title": "Sr Program Manager"
        },
        {
            "name": "Andrew",
            "title": "Program Manager II"
        },
        {
            "name": "Mary Anne",
            "title": "Program Manager"
        }
    ]
}
```

Fai clic sul pulsante **Preview Mode** (Modalità di anteprima). Dovrebbe essere eseguito il rendering della scheda in base ai dati di esempio forniti prima. Apporta qualsiasi modifica ai dati di esempio. Come puoi vedere, la scheda viene aggiornata in tempo reale.

**Congratulazioni**, hai appena creato il tuo primo modello di scheda adattiva. Vediamo ora come popolare il modello con dati reali.

> Scopri di più sul [linguaggio del modello](language.md)

## <a name="sdk-support"></a>SDK supportati

Gli SDK di creazione modelli rendono possibile popolare un modello con dati reali.

> [!NOTE]
>
> Durante l'anteprima iniziale è disponibile solo un set limitato di SDK. Al momento del rilascio, ci saranno librerie di modelli per ogni piattaforma di Schede adattive supportate.

Piattaforma | Installazione | Documentazione
--- | --- | ---
JavaScript | `npm install adaptivecards-templating` | [Documentazione](https://www.npmjs.com/package/adaptivecards-templating)
.NET | `nuget install AdaptiveCards.Templating` | [Documentazione](https://docs.microsoft.com/en-us/adaptive-cards/templating/sdk#net)

### <a name="javascript-example"></a>Esempio di JavaScript

Il codice JavaScript seguente illustra il criterio generale che verrà usato per popolare un modello con dati.

```js
var template = new ACData.Template({ 
    // EmployeeCardTemplate goes here
});

var dataContext = new ACData.EvaluationContext();
dataContext.$root = {
    // Data goes here
};

var card = template.expand(dataContext);
// Now you have an AdaptiveCard ready to render!
```

> Scopri di più sugli [SDK di creazione modelli](sdk.md)

## <a name="template-service"></a>Servizio modelli

Il servizio modelli di Schede adattive è un modello di verifica che consente a chiunque di trovare, contribuire e condividere un set di modelli ben noti.

È utile se vuoi visualizzare alcuni dati, ma senza scrivere appositamente una scheda adattiva personalizzata.

L'API per ottenere un modello è abbastanza semplice, ma il servizio in realtà offre molto di più, inclusa la possibilità di analizzare i dati e trovare un modello che potrebbe funzionare per specifiche esigenze.

`HTTP GET https://templates.adaptivecards.io/graph.microsoft.com/Profile.json`

Tutti i modelli sono file JSON flat archiviati in un repository di GitHub in modo che chiunque possa contribuirvi come per qualsiasi altro codice open source.

> Scopri di più sul [servizio modelli](service.md)

## <a name="whats-next-and-sending-feedback"></a>Passaggi successivi e invio di feedback

La creazione di modelli e la separazione della presentazione dai dati ci avvicinano di molto alla nostra mission: "un ecosistema per lo scambio di contenuti di schede in modo comune e coerente".

Condivideremo altre informazioni non appena possibile. Nel frattempo, invia il tuo feedback qui, [GitHub](https://github.com/microsoft/AdaptiveCards) o Twitter **[@MattHidinger](https://twitter.com/matthidinger)** / **#AdaptiveCards**. 
