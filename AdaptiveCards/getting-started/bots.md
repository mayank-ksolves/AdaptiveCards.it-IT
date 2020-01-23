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
# <a name="adaptive-cards-for-bot-developers"></a><span data-ttu-id="fca24-102">Schede adattive per gli sviluppatori di bot</span><span class="sxs-lookup"><span data-stu-id="fca24-102">Adaptive Cards for Bot Developers</span></span>

<span data-ttu-id="fca24-103">Le schede adattive sono ideali per i bot.</span><span class="sxs-lookup"><span data-stu-id="fca24-103">Adaptive Cards are a great fit for Bots.</span></span> <span data-ttu-id="fca24-104">Ti consentono di creare una scheda a una sola volta e di eseguirne perfettamente il rendering in più app, come Microsoft Teams, il tuo sito Web e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="fca24-104">They let you author a card once and have it render beautifully inside multiple apps, like  Microsoft Teams, your own website, and more.</span></span>

> [!NOTE]
> <span data-ttu-id="fca24-105">Skype non è supportato nell'anteprima corrente.</span><span class="sxs-lookup"><span data-stu-id="fca24-105">Skype is not supported in the current preview.</span></span> <span data-ttu-id="fca24-106">Per le informazioni più recenti, vedi la pagina sullo [stato dei partner](../resources/partners.md).</span><span class="sxs-lookup"><span data-stu-id="fca24-106">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>

## <a name="try-it-out"></a><span data-ttu-id="fca24-107">Provalo</span><span class="sxs-lookup"><span data-stu-id="fca24-107">Try it out</span></span>

<span data-ttu-id="fca24-108">Fai clic sul collegamento seguente e [parla il bot Scuba](http://contososcubademo.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="fca24-108">Click the following link and [talk to our Scuba Bot](http://contososcubademo.azurewebsites.net/).</span></span> <span data-ttu-id="fca24-109">Prova a dire `I'm looking for scuba` e ti aiuterà a prenotare il viaggio per le immersioni dei tuoi sogni.</span><span class="sxs-lookup"><span data-stu-id="fca24-109">Say `I'm looking for scuba` and it'll help you book the scuba trip of your dreams.</span></span>  

<span data-ttu-id="fca24-110">Tutte le risposte del bot vengono create tramite schede adattive.</span><span class="sxs-lookup"><span data-stu-id="fca24-110">All of the bot's responses are created with Adaptive Cards.</span></span>

<span data-ttu-id="fca24-111">[![Screenshot della chat Scuba](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span><span class="sxs-lookup"><span data-stu-id="fca24-111">[![Scuba chat screenshot](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span></span>

<span data-ttu-id="fca24-112">**Ottieni il codice**: l'intero [codice sorgente del bot Contoso Scuba](https://github.com/matthidinger/ContosoScubaBot
) è disponibile in GitHub.</span><span class="sxs-lookup"><span data-stu-id="fca24-112">**Get the code**: the full [Contoso Scuba Bot source code](https://github.com/matthidinger/ContosoScubaBot
) can be found on GitHub.</span></span>


## <a name="bot-framework-integration"></a><span data-ttu-id="fca24-113">Integrazione di Bot Framework</span><span class="sxs-lookup"><span data-stu-id="fca24-113">Bot Framework Integration</span></span>

<span data-ttu-id="fca24-114">Con [Bot Framework](https://dev.botframework.com/) è possibile scrivere un singolo bot che è in grado di chattare con utenti in più "canali", ad esempio Skype, Microsoft Teams, Facebook Messenger e così via.</span><span class="sxs-lookup"><span data-stu-id="fca24-114">With the [Bot Framework](https://dev.botframework.com/) you can write a single bot that is able to chat with users across multiple "channels", like Skype, Microsoft Teams, Facebook Messenger, etc.</span></span>

## <a name="walkthrough"></a><span data-ttu-id="fca24-115">scenario</span><span class="sxs-lookup"><span data-stu-id="fca24-115">Walkthrough</span></span>

<span data-ttu-id="fca24-116">È piuttosto semplice aggiungere una scheda adattiva al tuo bot.</span><span class="sxs-lookup"><span data-stu-id="fca24-116">It's pretty straight forward to add an Adaptive Card to your bot.</span></span>

### <a name="step-0-start-with-a-basic-message"></a><span data-ttu-id="fca24-117">Passaggio 0: inizia con un messaggio di base</span><span class="sxs-lookup"><span data-stu-id="fca24-117">Step 0: Start with a basic message</span></span>

<span data-ttu-id="fca24-118">Ecco un payload `message` standard di Bot Framework che può essere recapitato a qualsiasi canale e visualizzare testo per l'utente.</span><span class="sxs-lookup"><span data-stu-id="fca24-118">Here's a standard Bot Framework `message` payload that can be delivered to any channel and display text to the user.</span></span>

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a><span data-ttu-id="fca24-119">Passaggio 1: aggiungi un `attachment` di una scheda adattiva</span><span class="sxs-lookup"><span data-stu-id="fca24-119">Step 1: Add an Adaptive Card `attachment`</span></span>

<span data-ttu-id="fca24-120">Per aggiungere contenuti avanzati oltre al semplice testo, Bot Framework introduce il concetto di `attachments`.</span><span class="sxs-lookup"><span data-stu-id="fca24-120">To add some richness beyond just text, the Bot Framework has a concept of `attachments`.</span></span> 

<span data-ttu-id="fca24-121">Proviamo a collegare una scheda adattiva che visualizza testo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="fca24-121">Let's attach an Adaptive Card that displays custom text.</span></span>

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

### <a name="step-2-build-even-richer-cards"></a><span data-ttu-id="fca24-123">Passaggio 2: crea schede ancora più avanzate</span><span class="sxs-lookup"><span data-stu-id="fca24-123">Step 2: Build even richer cards</span></span> 

<span data-ttu-id="fca24-124">Le schede adattive offrono molto più che semplice testo personalizzabile.</span><span class="sxs-lookup"><span data-stu-id="fca24-124">Adaptive Cards offer much more than just customizable text.</span></span> 

<span data-ttu-id="fca24-125">È possibile:</span><span class="sxs-lookup"><span data-stu-id="fca24-125">You can:</span></span> 

* <span data-ttu-id="fca24-126">Aggiungere `Images` alla scheda</span><span class="sxs-lookup"><span data-stu-id="fca24-126">Add `Images` to your card</span></span>
* <span data-ttu-id="fca24-127">Organizzare i contenuti con `Containers` e `Columns`</span><span class="sxs-lookup"><span data-stu-id="fca24-127">Organize your content with `Containers` and `Columns`</span></span>
* <span data-ttu-id="fca24-128">Aggiungere più tipi di `Actions`</span><span class="sxs-lookup"><span data-stu-id="fca24-128">Add multiple types of `Actions`</span></span>
* <span data-ttu-id="fca24-129">Raccogliere `Input` dagli utenti</span><span class="sxs-lookup"><span data-stu-id="fca24-129">Collect `Input` from your users</span></span>
* <span data-ttu-id="fca24-130">Usare una scheda per `show another card`</span><span class="sxs-lookup"><span data-stu-id="fca24-130">Have one card `show another card`</span></span>
* <span data-ttu-id="fca24-131">[Consulta tutte le informazioni in Schema Explorer](http://adaptivecards.io/explorer/).</span><span class="sxs-lookup"><span data-stu-id="fca24-131">[Check out the full schema explorer](http://adaptivecards.io/explorer/)!</span></span> 

## <a name="platform-sdks"></a><span data-ttu-id="fca24-132">SDK delle piattaforme</span><span class="sxs-lookup"><span data-stu-id="fca24-132">Platform SDKs</span></span>

<span data-ttu-id="fca24-133">Se il bot è stato sviluppato usando .NET o NodeJS, sono disponibili librerie per rendere ancora più semplice la creazione di schede adattive.</span><span class="sxs-lookup"><span data-stu-id="fca24-133">If your bot is developed using .NET or NodeJS we have libraries to make building Adaptive Cards even easier.</span></span>

<span data-ttu-id="fca24-134">Piattaforma</span><span class="sxs-lookup"><span data-stu-id="fca24-134">Platform</span></span>|<span data-ttu-id="fca24-135">Installa</span><span class="sxs-lookup"><span data-stu-id="fca24-135">Install</span></span>|<span data-ttu-id="fca24-136">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="fca24-136">Learn more</span></span>
--------|-------|----------
<span data-ttu-id="fca24-137">.NET</span><span class="sxs-lookup"><span data-stu-id="fca24-137">.NET</span></span> | `Install-Package AdaptiveCards -IncludePrerelease` | [<span data-ttu-id="fca24-138">Documentazione di Bot Framework per .NET</span><span class="sxs-lookup"><span data-stu-id="fca24-138">Bot Framework .NET Docs</span></span>](https://docs.microsoft.com/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
<span data-ttu-id="fca24-139">NodeJS</span><span class="sxs-lookup"><span data-stu-id="fca24-139">NodeJS</span></span> | `npm install adaptivecards` | [<span data-ttu-id="fca24-140">Documentazione di Bot Framework per NodeJS</span><span class="sxs-lookup"><span data-stu-id="fca24-140">Bot Framework NodeJS Docs</span></span>](https://docs.microsoft.com/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a><span data-ttu-id="fca24-141">Stato del canale</span><span class="sxs-lookup"><span data-stu-id="fca24-141">Channel status</span></span>

<span data-ttu-id="fca24-142">Bot Framework consente di pubblicare i bot in più canali.</span><span class="sxs-lookup"><span data-stu-id="fca24-142">The Bot Framework lets you publish your bot to multiple channels.</span></span> <span data-ttu-id="fca24-143">Stiamo collaborando con vari canali per fornire un supporto completo per le schede adattive.</span><span class="sxs-lookup"><span data-stu-id="fca24-143">We're working with various channels to provide full support for Adaptive Cards.</span></span> <span data-ttu-id="fca24-144">Per le informazioni più recenti, vedi la pagina sullo [stato dei partner](../resources/partners.md).</span><span class="sxs-lookup"><span data-stu-id="fca24-144">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>


## <a name="dive-in"></a><span data-ttu-id="fca24-145">Approfondimento</span><span class="sxs-lookup"><span data-stu-id="fca24-145">Dive in!</span></span>

<span data-ttu-id="fca24-146">In questa esercitazione è stata fornita solo una presentazione generale. Visita i collegamenti seguenti per altre informazioni su come usare le schede adattive per migliorare i bot.</span><span class="sxs-lookup"><span data-stu-id="fca24-146">We've just scratched the surface in this tutorial, so please take a look at the links below to explore more ways that Adaptive Cards can enhance your bot.</span></span>

* <span data-ttu-id="fca24-147">[Esamina le schede di esempio](http://adaptivecards.io/samples/) per trovare l'ispirazione</span><span class="sxs-lookup"><span data-stu-id="fca24-147">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="fca24-148">Usa [Schema Explorer](http://adaptivecards.io/explorer) per informazioni sugli elementi disponibili</span><span class="sxs-lookup"><span data-stu-id="fca24-148">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="fca24-149">Crea una scheda usando il [visualizzatore interattivo](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span><span class="sxs-lookup"><span data-stu-id="fca24-149">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="fca24-150">[Contattaci](http://adaptivecards.io/connect) per eventuali commenti</span><span class="sxs-lookup"><span data-stu-id="fca24-150">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
