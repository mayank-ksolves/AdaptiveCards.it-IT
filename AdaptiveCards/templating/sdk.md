---
title: SDK per modelli
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 5f60a458af99f1b88e8ee428a8f29f1849be9b62
ms.sourcegitcommit: a16f53ba10a8607deacde5c8cc78927cac58657c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68878878"
---
# <a name="adaptive-card-templating-sdks"></a><span data-ttu-id="ae8d2-102">SDK per modelli di schede adattive</span><span class="sxs-lookup"><span data-stu-id="ae8d2-102">Adaptive Card Templating SDKs</span></span>

<span data-ttu-id="ae8d2-103">Gli SDK per modelli di schede adattive semplificano la compilazione di un [modello di scheda](language.md) con dati reali su qualsiasi piattaforma supportata.</span><span class="sxs-lookup"><span data-stu-id="ae8d2-103">The Adaptive Card Templating SDKs make it easy to populate a [card template](language.md) with real data on any supported platform.</span></span>

> <span data-ttu-id="ae8d2-104">Per una [Panoramica del modello di scheda adattivo](index.md) , vedere.</span><span class="sxs-lookup"><span data-stu-id="ae8d2-104">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="ae8d2-105">Queste funzionalità sono **in anteprima e sono soggette a modifiche**.</span><span class="sxs-lookup"><span data-stu-id="ae8d2-105">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="ae8d2-106">Il feedback non è solo Benvenuto, ma è fondamentale per garantire la fornitura delle funzionalità necessarie.</span><span class="sxs-lookup"><span data-stu-id="ae8d2-106">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>
> 
> <span data-ttu-id="ae8d2-107">Durante l'anteprima iniziale è disponibile solo JavaScript SDK, ma a breve arriverà un SDK .NET.</span><span class="sxs-lookup"><span data-stu-id="ae8d2-107">During the initial preview only the JavaScript SDK is available, but a .NET SDK should arrive shortly.</span></span>

## <a name="javascript"></a><span data-ttu-id="ae8d2-108">JavaScript</span><span class="sxs-lookup"><span data-stu-id="ae8d2-108">JavaScript</span></span>

<span data-ttu-id="ae8d2-109">La libreria [adaptivecards-template](https://www.npmjs.com/package/adaptivecards-templating) è disponibile in NPM e tramite la rete CDN.</span><span class="sxs-lookup"><span data-stu-id="ae8d2-109">The [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) library is available on npm and via CDN.</span></span> <span data-ttu-id="ae8d2-110">Per la documentazione completa, vedere il collegamento al pacchetto.</span><span class="sxs-lookup"><span data-stu-id="ae8d2-110">See the package link for full documentation.</span></span>

### <a name="npm"></a><span data-ttu-id="ae8d2-111">NPM</span><span class="sxs-lookup"><span data-stu-id="ae8d2-111">npm</span></span>

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a><span data-ttu-id="ae8d2-112">RETE CDN</span><span class="sxs-lookup"><span data-stu-id="ae8d2-112">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 

### <a name="usage"></a><span data-ttu-id="ae8d2-113">Uso</span><span class="sxs-lookup"><span data-stu-id="ae8d2-113">Usage</span></span>

<span data-ttu-id="ae8d2-114">Nell'esempio seguente si presuppone che sia stata installata anche la libreria [adaptivecards](https://www.npmjs.com/package/adaptivecards) per eseguire il rendering della scheda.</span><span class="sxs-lookup"><span data-stu-id="ae8d2-114">The sample below assumes you've also installed the [adaptivecards](https://www.npmjs.com/package/adaptivecards) library in order to render the card.</span></span> 

<span data-ttu-id="ae8d2-115">Se non si prevede di eseguire il rendering della scheda, è possibile `parse` rimuovere `render` il codice e.</span><span class="sxs-lookup"><span data-stu-id="ae8d2-115">If you don't plan on rendering the card then you can remove the `parse` and `render` code.</span></span> 

```js
import * as ACData from "adaptivecards-templating";
import * as AdaptiveCards from "adaptivecards";
 
// Define a template payload
var templatePayload = {
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hello {name}!"
        }
    ]
};
 
// Create a Template instamce from the template payload
var template = new ACData.Template(templatePayload);
 
// Create a data binding context, and set its $root property to the
// data object to bind the template to
var context = new ACData.EvaluationContext();
context.$root = {
    "name": "Mickey Mouse"
};
 
// "Expand" the template - this generates the final Adaptive Card,
// ready to render
var card = template.expand(context);
 
// Render the card
var adaptiveCard = new AdaptiveCards.AdaptiveCard();
adaptiveCard.parse(card);
 
var htmlElement = adaptiveCard.render();
```

## <a name="net-coming-soon"></a><span data-ttu-id="ae8d2-116">.NET (*presto disponibile*)</span><span class="sxs-lookup"><span data-stu-id="ae8d2-116">.NET (*coming soon*)</span></span>

<span data-ttu-id="ae8d2-117">NON FUNZIONA ANCORA:</span><span class="sxs-lookup"><span data-stu-id="ae8d2-117">NOT WORKING YET:</span></span> 

```console
nuget install AdaptiveCards.Templating
```
