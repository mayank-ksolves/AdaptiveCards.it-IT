---
title: Estensibilità-iOS SDK
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
# <a name="extensibility---ios"></a>Estensibilità-iOS

## <a name="changing-per-element-rendering"></a>Modifica del rendering per elemento

Gli sviluppatori possono personalizzare l'aspetto degli elementi AdaptiveCards di renderred, ad esempio TextBlock.
Nell'esempio seguente viene illustrato come è possibile modificare il colore di sfondo di NumberInput.

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

 ## <a name="additional-property"></a>Proprietà aggiuntiva

 Gli sviluppatori possono anche inviare proprietà aggiuntive come parte del payload JSON.
Ad esempio, oltre a "spaziatura" e "ID" del payload JSON per BaseCardElement, è possibile aggiungere RADIUS per gli angoli di TextBlock al relativo payload JSON.

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
 ## <a name="custom-parsing"></a>Analisi personalizzata

Gli sviluppatori possono anche avere un'analisi personalizzata e avere aggiunto un nuovo elemento dell'interfaccia utente alla scheda Adpative, ad esempio indicatore di stato. Per informazioni dettagliate, vedere CustomProgressBarRenderer.mm.
Il parser personalizzato deve implementare il protocollo ACOIBaseCardElementParser. il metodo deserializeToCustomElement deve analizzare il payload JSON specificato dato come NSData e restituire un puntatore all'oggetto UIView che verrà aggiunto all'oggetto di cui è stato eseguito il rendering AdaptiveCard.

```objective-c
      CustomProgressBarRenderer *progressBarRenderer = [[CustomProgressBarRenderer alloc] init];
      [registration setCustomElementParser:progressBarRenderer];
```objective-c