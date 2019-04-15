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
# <a name="render-a-card---ios"></a>Eseguire il rendering di una scheda - iOS

Di seguito viene illustrato come eseguire il rendering di una scheda usando il SDK per iOS.

## <a name="create-a-card-from-a-json-string"></a>Creare una scheda da una stringa JSON

AdaptiveCard viene generato dalla stringa JSON

```objective-c
ACOParseResult *cardParseResult = [ACOAdaptiveCards FromJson:jsonStr];
/// access for parse warnings and errors
NSArray<NSError *> errors = cardParseResult.parseErrors;
NSArray<ACRParseWarning *> warnings = cardPraseResult.parseWarnings;
```

## <a name="render-a-card"></a>Eseguire il rendering di una scheda

Rederer accetta scheda adattiva e configurazione di host. HostConfig può essere null e se null, verrà utilizzato il valore predefinito.

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:nil
                   widthConstraint:300.0];
``` 

### <a name="example"></a>Esempio

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

### <a name="render-a-card-as-uiviewcontroller"></a>Eseguire il rendering di una scheda come UIViewController

Renderer AdaptiveCard può inoltre restituire UIViewController.

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

Restituito che uiview Usa il layout automatico. Larghezza sarà vincolo per il valore impostato da widthConstraint. Se viene usato il valore 0, non verrà associato.
Altezza non è associato e quando restituito avrà l'altezza di somme di tutto il contenuto sottoposto a rendering. Per associare la dimensione di visualizzazione, usare NSLayoutConstraint. La dimensione esatta è accessibile dal contesto di viewDidLayoutSubview di viewcontroller della visualizzazione sovrapposta o il relativo metodo con lo stesso nome se ACRViewController viene usato.


### <a name="compact-style-inputchoiceset"></a>Stile Compact Input.ChoiceSet

Rappresentazione dell'interfaccia utente del Input.ChoiceSet includa UINavigationController e deve essere presentato a una classe UIViewController attualmente attiva per la transizione allo UIView che consente la selezione di utenti.

A tale scopo, implementare didFecthSecondaryView di ACRActionDelegate.

```objective-c
- (void)didFetchSecondaryView:(ACOAdaptiveCard *)card navigationController:(UINavigationController *)navigationController{
    [self presentViewController:navigationController animated:YES completion:nil];
}  
```

Se il delegato non è stato collegato, eseguire questa operazione.

```objective-c
adaptiveView.acrActionDelegate = self
```