---
title: Schede adattive per gli sviluppatori di Bot
author: matthidinger
ms.author: mahiding
ms.date: 05/30/2018
ms.topic: article
ms.openlocfilehash: 1acc30c0347ea5527de2af1fe74e605c7589cbc6
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553283"
---
# <a name="adaptive-cards-for-bot-developers"></a>Schede adattive per gli sviluppatori di Bot

Le schede adattive sono un candidato ideale per i robot. Consentono di creare una scheda a una sola volta, che verrà eseguito il rendering incredibilmente più applicazioni, ad esempio Microsoft Teams, proprio sito Web e altro ancora.

> [!NOTE]
> Skype non è supportata nell'anteprima corrente. Vedere le [Partner stato](../resources/partners.md) pagina per la versione più recente.

## <a name="try-it-out"></a>Prova

Fare clic sul collegamento seguente e [comunicare con l'apposito Bot immersioni](http://contososcubademo.azurewebsites.net/). Ad esempio `I'm looking for scuba` e ti permetterà di prenotare l'ottimizzazione dei viaggi di immersioni dei tuoi sogni.  

Tutte le risposte del bot vengono create con le schede adattive.

[![Schermata di chat immersioni](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)

**Ottenere il codice**: l'intero [codice sorgente Contoso immersioni Bot](https://github.com/matthidinger/ContosoScubaBot
) sono disponibili su GitHub.


## <a name="bot-framework-integration"></a>Integrazione di Bot Framework

Con il [Bot Framework](https://dev.botframework.com/) è possibile scrivere un bot singolo che è in grado di chat con utenti in più "canali", ad esempio Skype, Microsoft Teams, Facebook Messenger e così via.

## <a name="walkthrough"></a>scenario

È piuttosto semplice per aggiungere una scheda adattiva al tuo bot.

### <a name="step-0-start-with-a-basic-message"></a>Passaggio 0: Iniziare con un messaggio di base

Di seguito è un standard di Bot Framework `message` payload che possono essere recapitate a tutti i canali e testo da visualizzare per l'utente.

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a>Passaggio 1: Aggiungere una scheda adattiva `attachment`

Per aggiungere alcuni ricchezza oltre solo con il testo, Bot Framework è un concetto di `attachments`. 

È possibile collegare una scheda adattiva che visualizza testo personalizzato.

![Scheda adattiva base](media/bots/hello-adaptivecards.png)

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

### <a name="step-2-build-even-richer-cards"></a>Passaggio 2: Creare schede ancora più dettagliate 

Le schede adattive offrono testo personalizzabili molto più che sufficiente. 

È possibile: 

* Aggiungere `Images` sulla carta di
* Organizzare i contenuti con `Containers` e `Columns`
* Aggiungere più tipi di `Actions`
* Raccogliere `Input` da parte degli utenti
* Dispone di una scheda `show another card`
* [Estrazione schema completo explorer](http://adaptivecards.io/explorer/)! 

## <a name="platform-sdks"></a>SDK di piattaforma

Se il bot viene sviluppato usando .NET o NodeJS abbiamo librerie per semplificare la creazione le schede adattive ancora più semplice.

Piattaforma|Installazione|Scopri di più
--------|-------|----------
.NET | `Install-Package AdaptiveCards -IncludePrerelease` | [Documentazione di .NET Framework di BOT](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
NodeJS | `npm install adaptivecards` | [BOT Framework NodeJS Docs](https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a>Stato del canale

Bot Framework consente di pubblicare il bot in più canali. Stiamo collaborando con vari canali per fornire il supporto completo per le schede adattive. Vedere le [Partner stato](../resources/partners.md) pagina per la versione più recente.


## <a name="dive-in"></a>Approfondimento!

È stato solo un assaggio in questa esercitazione, pertanto, consultare i collegamenti seguenti per esplorare altri modi, le schede adattive può migliorare il bot.

* [Individuare le schede di esempio](http://adaptivecards.io/samples/) per trovare l'ispirazione
* Usare la [Schema Explorer](http://adaptivecards.io/explorer) apprendere gli elementi disponibili
* Creare una scheda usando il [Visualizzatore interattivo](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)
* [Contattare il supporto](http://adaptivecards.io/connect) con eventuali commenti
