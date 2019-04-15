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
# <a name="adaptive-cards-for-bot-developers"></a><span data-ttu-id="e1420-102">Schede adattive per gli sviluppatori di Bot</span><span class="sxs-lookup"><span data-stu-id="e1420-102">Adaptive Cards for Bot Developers</span></span>

<span data-ttu-id="e1420-103">Le schede adattive sono un candidato ideale per i robot.</span><span class="sxs-lookup"><span data-stu-id="e1420-103">Adaptive Cards are a great fit for Bots.</span></span> <span data-ttu-id="e1420-104">Consentono di creare una scheda a una sola volta, che verrà eseguito il rendering incredibilmente più applicazioni, ad esempio Microsoft Teams, proprio sito Web e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="e1420-104">They let you author a card once and have it render beautifully inside multiple apps, like  Microsoft Teams, your own website, and more.</span></span>

> [!NOTE]
> <span data-ttu-id="e1420-105">Skype non è supportata nell'anteprima corrente.</span><span class="sxs-lookup"><span data-stu-id="e1420-105">Skype is not supported in the current preview.</span></span> <span data-ttu-id="e1420-106">Vedere le [Partner stato](../resources/partners.md) pagina per la versione più recente.</span><span class="sxs-lookup"><span data-stu-id="e1420-106">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>

## <a name="try-it-out"></a><span data-ttu-id="e1420-107">Prova</span><span class="sxs-lookup"><span data-stu-id="e1420-107">Try it out</span></span>

<span data-ttu-id="e1420-108">Fare clic sul collegamento seguente e [comunicare con l'apposito Bot immersioni](http://contososcubademo.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="e1420-108">Click the following link and [talk to our Scuba Bot](http://contososcubademo.azurewebsites.net/).</span></span> <span data-ttu-id="e1420-109">Ad esempio `I'm looking for scuba` e ti permetterà di prenotare l'ottimizzazione dei viaggi di immersioni dei tuoi sogni.</span><span class="sxs-lookup"><span data-stu-id="e1420-109">Say `I'm looking for scuba` and it'll help you book the scuba trip of your dreams.</span></span>  

<span data-ttu-id="e1420-110">Tutte le risposte del bot vengono create con le schede adattive.</span><span class="sxs-lookup"><span data-stu-id="e1420-110">All of the bot's responses are created with Adaptive Cards.</span></span>

<span data-ttu-id="e1420-111">[![Schermata di chat immersioni](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span><span class="sxs-lookup"><span data-stu-id="e1420-111">[![Scuba chat screenshot](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span></span>

<span data-ttu-id="e1420-112">**Ottenere il codice**: l'intero [codice sorgente Contoso immersioni Bot](https://github.com/matthidinger/ContosoScubaBot
) sono disponibili su GitHub.</span><span class="sxs-lookup"><span data-stu-id="e1420-112">**Get the code**: the full [Contoso Scuba Bot source code](https://github.com/matthidinger/ContosoScubaBot
) can be found on GitHub.</span></span>


## <a name="bot-framework-integration"></a><span data-ttu-id="e1420-113">Integrazione di Bot Framework</span><span class="sxs-lookup"><span data-stu-id="e1420-113">Bot Framework Integration</span></span>

<span data-ttu-id="e1420-114">Con il [Bot Framework](https://dev.botframework.com/) è possibile scrivere un bot singolo che è in grado di chat con utenti in più "canali", ad esempio Skype, Microsoft Teams, Facebook Messenger e così via.</span><span class="sxs-lookup"><span data-stu-id="e1420-114">With the [Bot Framework](https://dev.botframework.com/) you can write a single bot that is able to chat with users across multiple "channels", like Skype, Microsoft Teams, Facebook Messenger, etc.</span></span>

## <a name="walkthrough"></a><span data-ttu-id="e1420-115">scenario</span><span class="sxs-lookup"><span data-stu-id="e1420-115">Walkthrough</span></span>

<span data-ttu-id="e1420-116">È piuttosto semplice per aggiungere una scheda adattiva al tuo bot.</span><span class="sxs-lookup"><span data-stu-id="e1420-116">It's pretty straight forward to add an Adaptive Card to your bot.</span></span>

### <a name="step-0-start-with-a-basic-message"></a><span data-ttu-id="e1420-117">Passaggio 0: Iniziare con un messaggio di base</span><span class="sxs-lookup"><span data-stu-id="e1420-117">Step 0: Start with a basic message</span></span>

<span data-ttu-id="e1420-118">Di seguito è un standard di Bot Framework `message` payload che possono essere recapitate a tutti i canali e testo da visualizzare per l'utente.</span><span class="sxs-lookup"><span data-stu-id="e1420-118">Here's a standard Bot Framework `message` payload that can be delivered to any channel and display text to the user.</span></span>

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a><span data-ttu-id="e1420-119">Passaggio 1: Aggiungere una scheda adattiva `attachment`</span><span class="sxs-lookup"><span data-stu-id="e1420-119">Step 1: Add an Adaptive Card `attachment`</span></span>

<span data-ttu-id="e1420-120">Per aggiungere alcuni ricchezza oltre solo con il testo, Bot Framework è un concetto di `attachments`.</span><span class="sxs-lookup"><span data-stu-id="e1420-120">To add some richness beyond just text, the Bot Framework has a concept of `attachments`.</span></span> 

<span data-ttu-id="e1420-121">È possibile collegare una scheda adattiva che visualizza testo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="e1420-121">Let's attach an Adaptive Card that displays custom text.</span></span>

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

### <a name="step-2-build-even-richer-cards"></a><span data-ttu-id="e1420-123">Passaggio 2: Creare schede ancora più dettagliate</span><span class="sxs-lookup"><span data-stu-id="e1420-123">Step 2: Build even richer cards</span></span> 

<span data-ttu-id="e1420-124">Le schede adattive offrono testo personalizzabili molto più che sufficiente.</span><span class="sxs-lookup"><span data-stu-id="e1420-124">Adaptive Cards offer much more than just customizable text.</span></span> 

<span data-ttu-id="e1420-125">È possibile:</span><span class="sxs-lookup"><span data-stu-id="e1420-125">You can:</span></span> 

* <span data-ttu-id="e1420-126">Aggiungere `Images` sulla carta di</span><span class="sxs-lookup"><span data-stu-id="e1420-126">Add `Images` to your card</span></span>
* <span data-ttu-id="e1420-127">Organizzare i contenuti con `Containers` e `Columns`</span><span class="sxs-lookup"><span data-stu-id="e1420-127">Organize your content with `Containers` and `Columns`</span></span>
* <span data-ttu-id="e1420-128">Aggiungere più tipi di `Actions`</span><span class="sxs-lookup"><span data-stu-id="e1420-128">Add multiple types of `Actions`</span></span>
* <span data-ttu-id="e1420-129">Raccogliere `Input` da parte degli utenti</span><span class="sxs-lookup"><span data-stu-id="e1420-129">Collect `Input` from your users</span></span>
* <span data-ttu-id="e1420-130">Dispone di una scheda `show another card`</span><span class="sxs-lookup"><span data-stu-id="e1420-130">Have one card `show another card`</span></span>
* <span data-ttu-id="e1420-131">[Estrazione schema completo explorer](http://adaptivecards.io/explorer/)!</span><span class="sxs-lookup"><span data-stu-id="e1420-131">[Check out the full schema explorer](http://adaptivecards.io/explorer/)!</span></span> 

## <a name="platform-sdks"></a><span data-ttu-id="e1420-132">SDK di piattaforma</span><span class="sxs-lookup"><span data-stu-id="e1420-132">Platform SDKs</span></span>

<span data-ttu-id="e1420-133">Se il bot viene sviluppato usando .NET o NodeJS abbiamo librerie per semplificare la creazione le schede adattive ancora più semplice.</span><span class="sxs-lookup"><span data-stu-id="e1420-133">If your bot is developed using .NET or NodeJS we have libraries to make building Adaptive Cards even easier.</span></span>

<span data-ttu-id="e1420-134">Piattaforma</span><span class="sxs-lookup"><span data-stu-id="e1420-134">Platform</span></span>|<span data-ttu-id="e1420-135">Installazione</span><span class="sxs-lookup"><span data-stu-id="e1420-135">Install</span></span>|<span data-ttu-id="e1420-136">Scopri di più</span><span class="sxs-lookup"><span data-stu-id="e1420-136">Learn more</span></span>
--------|-------|----------
<span data-ttu-id="e1420-137">.NET</span><span class="sxs-lookup"><span data-stu-id="e1420-137">.NET</span></span> | `Install-Package AdaptiveCards -IncludePrerelease` | [<span data-ttu-id="e1420-138">Documentazione di .NET Framework di BOT</span><span class="sxs-lookup"><span data-stu-id="e1420-138">Bot Framework .NET Docs</span></span>](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
<span data-ttu-id="e1420-139">NodeJS</span><span class="sxs-lookup"><span data-stu-id="e1420-139">NodeJS</span></span> | `npm install adaptivecards` | [<span data-ttu-id="e1420-140">BOT Framework NodeJS Docs</span><span class="sxs-lookup"><span data-stu-id="e1420-140">Bot Framework NodeJS Docs</span></span>](https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a><span data-ttu-id="e1420-141">Stato del canale</span><span class="sxs-lookup"><span data-stu-id="e1420-141">Channel status</span></span>

<span data-ttu-id="e1420-142">Bot Framework consente di pubblicare il bot in più canali.</span><span class="sxs-lookup"><span data-stu-id="e1420-142">The Bot Framework lets you publish your bot to multiple channels.</span></span> <span data-ttu-id="e1420-143">Stiamo collaborando con vari canali per fornire il supporto completo per le schede adattive.</span><span class="sxs-lookup"><span data-stu-id="e1420-143">We're working with various channels to provide full support for Adaptive Cards.</span></span> <span data-ttu-id="e1420-144">Vedere le [Partner stato](../resources/partners.md) pagina per la versione più recente.</span><span class="sxs-lookup"><span data-stu-id="e1420-144">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>


## <a name="dive-in"></a><span data-ttu-id="e1420-145">Approfondimento!</span><span class="sxs-lookup"><span data-stu-id="e1420-145">Dive in!</span></span>

<span data-ttu-id="e1420-146">È stato solo un assaggio in questa esercitazione, pertanto, consultare i collegamenti seguenti per esplorare altri modi, le schede adattive può migliorare il bot.</span><span class="sxs-lookup"><span data-stu-id="e1420-146">We've just scratched the surface in this tutorial, so please take a look at the links below to explore more ways that Adaptive Cards can enhance your bot.</span></span>

* <span data-ttu-id="e1420-147">[Individuare le schede di esempio](http://adaptivecards.io/samples/) per trovare l'ispirazione</span><span class="sxs-lookup"><span data-stu-id="e1420-147">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="e1420-148">Usare la [Schema Explorer](http://adaptivecards.io/explorer) apprendere gli elementi disponibili</span><span class="sxs-lookup"><span data-stu-id="e1420-148">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="e1420-149">Creare una scheda usando il [Visualizzatore interattivo](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span><span class="sxs-lookup"><span data-stu-id="e1420-149">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="e1420-150">[Contattare il supporto](http://adaptivecards.io/connect) con eventuali commenti</span><span class="sxs-lookup"><span data-stu-id="e1420-150">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
