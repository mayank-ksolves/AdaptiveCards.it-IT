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
# <a name="extensibility---ios"></a><span data-ttu-id="4fdb3-102">Extensibility - iOS</span><span class="sxs-lookup"><span data-stu-id="4fdb3-102">Extensibility - iOS</span></span>

## <a name="changing-per-element-rendering"></a><span data-ttu-id="4fdb3-103">La modifica per il rendering di elemento</span><span class="sxs-lookup"><span data-stu-id="4fdb3-103">Changing per element rendering</span></span>

<span data-ttu-id="4fdb3-104">Gli sviluppatori possono personalizzare l'aspetto di renderred AdaptiveCards elementi quali controllo TextBlock.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-104">Developers can customize the look of renderred AdaptiveCards elements such as TextBlock.</span></span>
<span data-ttu-id="4fdb3-105">Esempio seguente mostra come sia possibile modificare il colore di sfondo di NumberInput.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-105">Following example shows how one can change background color of NumberInput.</span></span>

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

 ## <a name="additional-property"></a><span data-ttu-id="4fdb3-106">Proprietà aggiuntive</span><span class="sxs-lookup"><span data-stu-id="4fdb3-106">Additional Property</span></span>

 <span data-ttu-id="4fdb3-107">Gli sviluppatori possono anche inviare nella proprietà aggiuntive come parte del payload json.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-107">Developers can also send in additional properties as part of json payload.</span></span>
<span data-ttu-id="4fdb3-108">Oltre a "spaziatura" e "id" del payload json per BaseCardElement, ad esempio, una possibile aggiungere raggio degli angoli di TextBlock al relativo palyload json.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-108">For example, in addition to "spacing" and "id" of json payload for BaseCardElement, one can add radius for corners of TextBlock to its json payload.</span></span>

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
 ## <a name="custom-parsing"></a><span data-ttu-id="4fdb3-109">L'analisi personalizzata</span><span class="sxs-lookup"><span data-stu-id="4fdb3-109">Custom Parsing</span></span>

<span data-ttu-id="4fdb3-110">Gli sviluppatori possono inoltre dispone di analisi personalizzata e di nuovo elemento dell'interfaccia utente viene aggiunto alla scheda adpative come indicatore di stato.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-110">Developers can also have custom parsing and have new UI element added to adpative card such as progress bar.</span></span> <span data-ttu-id="4fdb3-111">Per dettagli, controllare CustomProgressBarRenderer.mm.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-111">Please check CustomProgressBarRenderer.mm for detail.</span></span>
<span data-ttu-id="4fdb3-112">Parser personalizzato deve implementare ACOIBaseCardElementParser protocollo.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-112">Custom parser must implement ACOIBaseCardElementParser protocol.</span></span> <span data-ttu-id="4fdb3-113">metodo deserializeToCustomElement deve analizza dato payload json fornito come NSData e restituire un puntatore all'oggetto UIView che verrà aggiunti all'oggetto AdaptiveCard sottoposto a rendering.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-113">deserializeToCustomElement method should parses given json payload given as NSData and return a pointer to UIView object that will be added to AdaptiveCard rendered object.</span></span>

```objective-c
      CustomProgressBarRenderer *progressBarRenderer = [[CustomProgressBarRenderer alloc] init];
      [registration setCustomElementParser:progressBarRenderer];
```objective-c