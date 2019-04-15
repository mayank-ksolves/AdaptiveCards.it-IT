---
title: Extensibility - SDK per iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: c3dcae7ef2347201b5f7ce02baf3204db7ee27d6
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553563"
---
# <a name="extensibility---ios"></a>Extensibility - iOS

## <a name="changing-per-element-rendering"></a>La modifica per il rendering di elemento

Gli sviluppatori possono personalizzare l'aspetto di renderred AdaptiveCards elementi quali controllo TextBlock.
Esempio seguente mostra come sia possibile modificare il colore di sfondo di NumberInput.

```objective-c
ACRRegistration *registration = [ACRRegistration getInstance];
// register custom renderer with registration
// custom renderer must implement ACRIBaseCardElementRenderer protocol
// for more information, please refer to CustomInputNumberRenderer.mm
 [registration setBaseCardElementRenderer:[CustomInputNumberRenderer getInstance] cardElementType:ACRNumberInput];
 ...
/// CustiomInputNumberRenderer.mm
- (UIView *)render:(UIView<ACRIContentHoldingView> *)viewGroup
              rootViewController:(UIViewController *)vc
              inputs:(NSArray *)inputs
     baseCardElement:(ACOBaseCardElement *)acoElem
          hostConfig:(ACOHostConfig *)acoConfig
  {
      ACRInputNumberRenderer *defaultRenderer = [ACRInputNumberRenderer getInstance];
 
      UIView *input = [defaultRenderer render:viewGroup
                           rootViewController:vc
                                       inputs:inputs
                              baseCardElement:acoElem
                                   hostConfig:acoConfig];
      if(input)
      {   
          // customize background color of input
          [input setBackgroundColor: [UIColor colorWithRed:1.0
                                                     green:59.0/255.0
                                                      blue:48.0/255.0
                                                     alpha:1.0]];
      }
      return input;
  }
  ```

 ## <a name="additional-property"></a>Proprietà aggiuntive

 Gli sviluppatori possono anche inviare nella proprietà aggiuntive come parte del payload json.
Oltre a "spaziatura" e "id" del payload json per BaseCardElement, ad esempio, una possibile aggiungere raggio degli angoli di TextBlock al relativo palyload json.

 ```objective-c
 "type":"TextBlock",
 ...
 "radius":20,
 ...
 ```

 ```objective-c
         NSData *additionalProperty = [acoElem additionalProperty];
          if(additionalProperty) {
              NSDictionary *dictionary = [NSJSONSerialization JSONObjectWithData:additionalProperty options:NSJSONReadingMutableLeaves error:nil];
              radiusForMyTextBlock = dictionary[@"radius"];
          ...
```
 ## <a name="custom-parsing"></a>L'analisi personalizzata

Gli sviluppatori possono inoltre dispone di analisi personalizzata e di nuovo elemento dell'interfaccia utente viene aggiunto alla scheda adpative come indicatore di stato. Per dettagli, controllare CustomProgressBarRenderer.mm.
Parser personalizzato deve implementare ACOIBaseCardElementParser protocollo. metodo deserializeToCustomElement deve analizza dato payload json fornito come NSData e restituire un puntatore all'oggetto UIView che verrà aggiunti all'oggetto AdaptiveCard sottoposto a rendering.

```objective-c
      CustomProgressBarRenderer *progressBarRenderer = [[CustomProgressBarRenderer alloc] init];
      [registration setCustomElementParser:progressBarRenderer];
```objective-c