---
title: Panoramica della creazione di modelli
author: matthidinger
ms.author: mahiding
ms.date: 05/18/2020
ms.topic: article
ms.openlocfilehash: 41eb972603b1688a1f1857cec83208b9b55b02c3
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417622"
---
# <a name="adaptive-cards-templating"></a>Creazione di modelli di Schede adattive

Siamo lieti di condividere un'anteprima dei nuovi strumenti che ti aiuteranno a **creare**, **,riutilizzare** e **condividere** Schede adattive. 

> [!IMPORTANT] 
> 
> **Modifiche importanti** apportate alla **versione finale candidata di maggio 2020**
>
> La versione finale candidata della creazione di modelli include alcune importanti modifiche che devi conoscere se stai usando i pacchetti meno recenti. Per informazioni dettagliate, vedi di seguito.


## <a name="breaking-changes-as-of-may-2020"></a>Modifiche importanti della versione di maggio 2020

1. La sintassi di binding è cambiata da `{...}` a `${...}`. 
    * Ad esempio, `"text": "Hello {name}"` diventa `"text": "Hello ${name}"`
2. L'API JavaScript non contiene più un oggetto `EvaluationContext`. Passa semplicemente i dati alla funzione `expand`. Per informazioni dettagliate, vedi la [pagina dell'SDK](sdk.md).
3. L'API .NET è stata riprogettata in modo da corrispondere più strettamente all'API JavaScript. Per informazioni dettagliate, vedi la [pagina dell'SDK](sdk.md).

## <a name="how-can-templating-help-you"></a>Vantaggi della creazione di modelli

La creazione di modelli consente di separare i **dati** dal **layout** in una scheda adattiva. 

### <a name="it-helps-design-a-card-once-and-then-populate-it-with-real-data"></a>Permette di progettare una scheda una sola volta e quindi di popolarla con dati reali

Oggi non è possibile creare una scheda tramite [Designer di Schede adattive](https://adaptivecards.io/designer) e usare questo codice JSON per popolare il payload con **contenuto dinamico**. Per ottenere questo risultato, è necessario scrivere codice personalizzato per compilare una stringa JSON oppure usare gli SDK del modello a oggetti per creare un modello a oggetti che rappresenta la scheda, quindi serializzarlo in JSON. In entrambi i casi, Designer offre un'operazione unidirezionale da eseguire una sola volta e non semplifica la modifica della progettazione della scheda in un secondo momento dopo la conversione in codice.

### <a name="it-makes-transmissions-over-the-wire-smaller"></a>Riduce le dimensioni delle trasmissioni in rete

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
                            "url": "${photo}",
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
                            "text": "Hi ${name}!",
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
            "text": "Your manager is: **${manager.name}**"
        },
        {
            "type": "TextBlock",
            "text": "Your peers are:"
        },
        {
            "type": "FactSet",
            "facts": [
                {
                    "$data": "${peers}",
                    "title": "${name}",
                    "value": "${title}"
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
> Al momento, gli SDK per la creazione di modelli sono disponibili per .NET e NodeJS. Nel tempo gli SDK per la creazione di modelli verranno rilasciati per tutte le rimanenti piattaforme di Schede adattive, ad esempio iOS, Android, UWP e così via.

Piattaforma | Pacchetto | Installa | Documentazione
--- | --- | --- | ---
JavaScript | [![Installazione di NPM](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating) | `npm install adaptivecards-templating` | [Documentazione](https://www.npmjs.com/package/adaptivecards-templating)
.NET | [![Installazione di Nuget](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating) | `dotnet add package AdaptiveCards.Templating` | [Documentazione](https://docs.microsoft.com/adaptive-cards/templating/sdk#net)

### <a name="javascript-example"></a>Esempio di JavaScript

Il codice JavaScript seguente illustra il criterio generale che verrà usato per popolare un modello con dati.

```js
var template = new ACData.Template({ 
    // Card Template JSON
});

var card = template.expand({
    $root: {
        // Data Fields
    }
});

// Now you have an AdaptiveCard ready to render!
```

### <a name="c-example"></a>Esempio di C#

Il codice C# seguente illustra il criterio generale che verrà usato per popolare un modello con dati.

```csharp
var template = new AdaptiveCards.Templating.AdaptiveCardTemplate(cardJson);
   
var card = template.Expand(new {Key="Value"});

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

La creazione di modelli e la separazione della presentazione dai dati ci avvicinano di molto alla nostra mission: "un ecosistema standardizzato per lo scambio di contenuti tra app e servizi". In quest'area sono disponibili molte informazioni, quindi continua a seguire la pagina e condividi con noi la tua esperienza con [GitHub](https://github.com/Microsoft/AdaptiveCards/issues).
