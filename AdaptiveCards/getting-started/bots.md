---
title: Schede adattive per gli sviluppatori di bot
author: matthidinger
ms.author: mahiding
ms.date: 05/30/2018
ms.topic: article
ms.openlocfilehash: 1c3ad2a4588244a8bd30011a4b6e25e37062624a
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145381"
---
# <a name="adaptive-cards-for-bot-developers"></a>Schede adattive per gli sviluppatori di bot

Le schede adattive sono ideali per i bot. Ti consentono di creare una scheda a una sola volta e di eseguirne perfettamente il rendering in più app, come Microsoft Teams, il tuo sito Web e altro ancora.

> [!NOTE]
> Skype non è supportato nell'anteprima corrente. Per le informazioni più recenti, vedi la pagina sullo [stato dei partner](../resources/partners.md).

## <a name="try-it-out"></a>Provalo

Fai clic sul collegamento seguente e [parla il bot Scuba](http://contososcubademo.azurewebsites.net/). Prova a dire `I'm looking for scuba` e ti aiuterà a prenotare il viaggio per le immersioni dei tuoi sogni.  

Tutte le risposte del bot vengono create tramite schede adattive.

[![Screenshot della chat Scuba](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)

**Ottieni il codice**: l'intero [codice sorgente del bot Contoso Scuba](https://github.com/matthidinger/ContosoScubaBot
) è disponibile in GitHub.


## <a name="bot-framework-integration"></a>Integrazione di Bot Framework

Con [Bot Framework](https://dev.botframework.com/) è possibile scrivere un singolo bot che è in grado di chattare con utenti in più "canali", ad esempio Skype, Microsoft Teams, Facebook Messenger e così via.

## <a name="walkthrough"></a>scenario

È piuttosto semplice aggiungere una scheda adattiva al tuo bot.

### <a name="step-0-start-with-a-basic-message"></a>Passaggio 0: inizia con un messaggio di base

Ecco un payload `message` standard di Bot Framework che può essere recapitato a qualsiasi canale e visualizzare testo per l'utente.

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a>Passaggio 1: aggiungi un `attachment` di una scheda adattiva

Per aggiungere contenuti avanzati oltre al semplice testo, Bot Framework introduce il concetto di `attachments`. 

Proviamo a collegare una scheda adattiva che visualizza testo personalizzato.

![Scheda adattiva di base](media/bots/hello-adaptivecards.png)

```json
{
  "type": "message",
  "text": "Plain text is ok, but sometimes I long for more...",
  "attachments": [
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "TextBlock",
            "text": "Hello World!",
            "size": "large"
          },
          {
            "type": "TextBlock",
            "text": "*Sincerely yours,*"
          },
          {
            "type": "TextBlock",
            "text": "Adaptive Cards",
            "separation": "none"
          }
        ],
        "actions": [
          {
            "type": "Action.OpenUrl",
            "url": "http://adaptivecards.io",
            "title": "Learn More"
          }
        ]
      }
    }
  ]
}
```

### <a name="step-2-build-even-richer-cards"></a>Passaggio 2: crea schede ancora più avanzate 

Le schede adattive offrono molto più che semplice testo personalizzabile. 

È possibile: 

* Aggiungere `Images` alla scheda
* Organizzare i contenuti con `Containers` e `Columns`
* Aggiungere più tipi di `Actions`
* Raccogliere `Input` dagli utenti
* Usare una scheda per `show another card`
* [Consulta tutte le informazioni in Schema Explorer](http://adaptivecards.io/explorer/). 

## <a name="platform-sdks"></a>SDK delle piattaforme

Se il bot è stato sviluppato usando .NET o NodeJS, sono disponibili librerie per rendere ancora più semplice la creazione di schede adattive.

Piattaforma|Installa|Altre informazioni
--------|-------|----------
.NET | `Install-Package AdaptiveCards -IncludePrerelease` | [Documentazione di Bot Framework per .NET](https://docs.microsoft.com/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
NodeJS | `npm install adaptivecards` | [Documentazione di Bot Framework per NodeJS](https://docs.microsoft.com/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a>Stato del canale

Bot Framework consente di pubblicare i bot in più canali. Stiamo collaborando con vari canali per fornire un supporto completo per le schede adattive. Per le informazioni più recenti, vedi la pagina sullo [stato dei partner](../resources/partners.md).


## <a name="dive-in"></a>Approfondimento

In questa esercitazione è stata fornita solo una presentazione generale. Visita i collegamenti seguenti per altre informazioni su come usare le schede adattive per migliorare i bot.

* [Esamina le schede di esempio](http://adaptivecards.io/samples/) per trovare l'ispirazione
* Usa [Schema Explorer](http://adaptivecards.io/explorer) per informazioni sugli elementi disponibili
* Crea una scheda usando il [visualizzatore interattivo](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)
* [Contattaci](http://adaptivecards.io/connect) per eventuali commenti
