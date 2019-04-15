---
title: Eseguire il rendering di una scheda - SDK per iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 625701e38389cc1a54682b72ce2315c14180e576
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552473"
---
# <a name="render-a-card---ios"></a><span data-ttu-id="59e77-102">Eseguire il rendering di una scheda - iOS</span><span class="sxs-lookup"><span data-stu-id="59e77-102">Render a card - iOS</span></span>

<span data-ttu-id="59e77-103">Di seguito viene illustrato come eseguire il rendering di una scheda usando il SDK per iOS.</span><span class="sxs-lookup"><span data-stu-id="59e77-103">Here's how to render a card using the iOS SDK.</span></span>

## <a name="create-a-card-from-a-json-string"></a><span data-ttu-id="59e77-104">Creare una scheda da una stringa JSON</span><span class="sxs-lookup"><span data-stu-id="59e77-104">Create a card from a JSON string</span></span>

<span data-ttu-id="59e77-105">AdaptiveCard viene generato dalla stringa JSON</span><span class="sxs-lookup"><span data-stu-id="59e77-105">AdaptiveCard is generated from JSON string</span></span>

```objective-c
ACOParseResult *cardParseResult = [ACOAdaptiveCards FromJson:jsonStr];
/// access for parse warnings and errors
NSArray<NSError *> errors = cardParseResult.parseErrors;
NSArray<ACRParseWarning *> warnings = cardPraseResult.parseWarnings;
```

## <a name="render-a-card"></a><span data-ttu-id="59e77-106">Eseguire il rendering di una scheda</span><span class="sxs-lookup"><span data-stu-id="59e77-106">Render a Card</span></span>

<span data-ttu-id="59e77-107">Rederer accetta scheda adattiva e configurazione di host. HostConfig può essere null e se null, verrà utilizzato il valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="59e77-107">Rederer takes adaptive card and host config. HostConfig can be nil, and if nil, default value will be used.</span></span>

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:nil
                   widthConstraint:300.0];
``` 

### <a name="example"></a><span data-ttu-id="59e77-108">Esempio</span><span class="sxs-lookup"><span data-stu-id="59e77-108">Example</span></span>

```objective-c
ACRRenderResult *renderResult;
ACOHostConfigParseResult *hostconfigParseResult = [ACOHostConfig FromJson:self.hostconfig];
ACOAdaptiveCardsParseResult *cardParseResult       = [ACOAdaptiveCards FromJson:jsonStr];

// checking parse result
if(hostconfigParseResult.IsValid == YES && cardParseResult.IsValid == YES)
{
    renderResult = [ACRRenderer render:cardParseResult.card
                                config:hostconfigParseResult.config
                       widthConstraint:300.0];
}   
    
if(renderResult.Suceeded == YES)
{
    // access returned UIView object
    ACRView *adaptiveView = renderResult.view;
    [self.view addSubview:adcVc.view];
}
```

### <a name="render-a-card-as-uiviewcontroller"></a><span data-ttu-id="59e77-109">Eseguire il rendering di una scheda come UIViewController</span><span class="sxs-lookup"><span data-stu-id="59e77-109">Render a Card as UIViewController</span></span>

<span data-ttu-id="59e77-110">Renderer AdaptiveCard può inoltre restituire UIViewController.</span><span class="sxs-lookup"><span data-stu-id="59e77-110">AdaptiveCard renderer can also return UIViewController.</span></span>

```objective-c
ACRRenderResult *renderResult = [ACRRenderer renderAsViewController:card config:config frame:frame delegate:acrActionDelegate];

renderResult.viewif(renderResult.Suceeded == YES)
{
    ACRViewController *adaptiveViewController = renderResult.viewcontroller;
    [self addChildViewController:adaptiveViewController];
    [self.view addSubview:adaptiveViewController.view];
    [adaptiveViewController didMoveToParentViewController:self];
    ...
}
```

<span data-ttu-id="59e77-111">Restituito che uiview Usa il layout automatico.</span><span class="sxs-lookup"><span data-stu-id="59e77-111">Returned UIView uses autolayout.</span></span> <span data-ttu-id="59e77-112">Larghezza sarà vincolo per il valore impostato da widthConstraint.</span><span class="sxs-lookup"><span data-stu-id="59e77-112">Width will be constraint to the value set by widthConstraint.</span></span> <span data-ttu-id="59e77-113">Se viene usato il valore 0, non verrà associato.</span><span class="sxs-lookup"><span data-stu-id="59e77-113">If 0 value is used, it won't be bound.</span></span>
<span data-ttu-id="59e77-114">Altezza non è associato e quando restituito avrà l'altezza di somme di tutto il contenuto sottoposto a rendering.</span><span class="sxs-lookup"><span data-stu-id="59e77-114">Height is not bound, and when returned it will have the height of sums of all contents rendered.</span></span> <span data-ttu-id="59e77-115">Per associare la dimensione di visualizzazione, usare NSLayoutConstraint.</span><span class="sxs-lookup"><span data-stu-id="59e77-115">To bound the view dimension, please use NSLayoutConstraint.</span></span> <span data-ttu-id="59e77-116">La dimensione esatta è accessibile dal contesto di viewDidLayoutSubview di viewcontroller della visualizzazione sovrapposta o il relativo metodo con lo stesso nome se ACRViewController viene usato.</span><span class="sxs-lookup"><span data-stu-id="59e77-116">The exact dimension is accessible from the context of viewDidLayoutSubview of its superview's viewcontroller or its method with the same name if ACRViewController is used.</span></span>


### <a name="compact-style-inputchoiceset"></a><span data-ttu-id="59e77-117">Stile Compact Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="59e77-117">Compact Style Input.ChoiceSet</span></span>

<span data-ttu-id="59e77-118">Rappresentazione dell'interfaccia utente del Input.ChoiceSet includa UINavigationController e deve essere presentato a una classe UIViewController attualmente attiva per la transizione allo UIView che consente la selezione di utenti.</span><span class="sxs-lookup"><span data-stu-id="59e77-118">UI representation of Input.ChoiceSet has UINavigationController, and it needs to be presented to a presently active UIViewController to transition into UIView that allows user selection.</span></span>

<span data-ttu-id="59e77-119">A tale scopo, implementare didFecthSecondaryView di ACRActionDelegate.</span><span class="sxs-lookup"><span data-stu-id="59e77-119">To accomplish that, please implement didFecthSecondaryView of ACRActionDelegate.</span></span>

```objective-c
- (void)didFetchSecondaryView:(ACOAdaptiveCard *)card navigationController:(UINavigationController *)navigationController{
    [self presentViewController:navigationController animated:YES completion:nil];
}  
```

<span data-ttu-id="59e77-120">Se il delegato non è stato collegato, eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="59e77-120">If the delgate has not been hooked up, do so.</span></span>

```objective-c
adaptiveView.acrActionDelegate = self
```