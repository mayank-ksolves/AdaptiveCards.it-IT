---
title: Estensibilità-iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 13245ced3f4f657e13793bfdf1d212e44d2b6a41
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454764"
---
# <a name="extensibility---ios"></a><span data-ttu-id="a54e5-102">Estensibilità-iOS</span><span class="sxs-lookup"><span data-stu-id="a54e5-102">Extensibility - iOS</span></span>

## <a name="changing-per-element-rendering"></a><span data-ttu-id="a54e5-103">Modifica del rendering per elemento</span><span class="sxs-lookup"><span data-stu-id="a54e5-103">Changing per element rendering</span></span>

<span data-ttu-id="a54e5-104">Gli sviluppatori possono personalizzare l'aspetto degli elementi AdaptiveCards di renderred, ad esempio TextBlock.</span><span class="sxs-lookup"><span data-stu-id="a54e5-104">Developers can customize the look of renderred AdaptiveCards elements such as TextBlock.</span></span>
<span data-ttu-id="a54e5-105">Nell'esempio seguente viene illustrato come è possibile modificare il colore di sfondo di NumberInput.</span><span class="sxs-lookup"><span data-stu-id="a54e5-105">Following example shows how one can change background color of NumberInput.</span></span>

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

 ## <a name="additional-property"></a><span data-ttu-id="a54e5-106">Proprietà aggiuntiva</span><span class="sxs-lookup"><span data-stu-id="a54e5-106">Additional Property</span></span>

 <span data-ttu-id="a54e5-107">Gli sviluppatori possono anche inviare proprietà aggiuntive come parte del payload JSON.</span><span class="sxs-lookup"><span data-stu-id="a54e5-107">Developers can also send in additional properties as part of json payload.</span></span>
<span data-ttu-id="a54e5-108">Ad esempio, oltre a "spaziatura" e "ID" del payload JSON per BaseCardElement, è possibile aggiungere RADIUS per gli angoli di TextBlock al relativo payload JSON.</span><span class="sxs-lookup"><span data-stu-id="a54e5-108">For example, in addition to "spacing" and "id" of json payload for BaseCardElement, one can add radius for corners of TextBlock to its json payload.</span></span>

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
 ## <a name="custom-parsing"></a><span data-ttu-id="a54e5-109">Analisi personalizzata</span><span class="sxs-lookup"><span data-stu-id="a54e5-109">Custom Parsing</span></span>

<span data-ttu-id="a54e5-110">Gli sviluppatori possono anche avere un'analisi personalizzata e avere aggiunto un nuovo elemento dell'interfaccia utente alla scheda Adpative, ad esempio indicatore di stato.</span><span class="sxs-lookup"><span data-stu-id="a54e5-110">Developers can also have custom parsing and have new UI element added to adpative card such as progress bar.</span></span> <span data-ttu-id="a54e5-111">Per informazioni dettagliate, vedere CustomProgressBarRenderer.mm.</span><span class="sxs-lookup"><span data-stu-id="a54e5-111">Please check CustomProgressBarRenderer.mm for detail.</span></span>
<span data-ttu-id="a54e5-112">Il parser personalizzato deve implementare il protocollo ACOIBaseCardElementParser.</span><span class="sxs-lookup"><span data-stu-id="a54e5-112">Custom parser must implement ACOIBaseCardElementParser protocol.</span></span> <span data-ttu-id="a54e5-113">il metodo deserializeToCustomElement deve analizzare il payload JSON specificato dato come NSData e restituire un puntatore all'oggetto UIView che verrà aggiunto all'oggetto di cui è stato eseguito il rendering AdaptiveCard.</span><span class="sxs-lookup"><span data-stu-id="a54e5-113">deserializeToCustomElement method should parses given json payload given as NSData and return a pointer to UIView object that will be added to AdaptiveCard rendered object.</span></span>

```objective-c
      CustomProgressBarRenderer *progressBarRenderer = [[CustomProgressBarRenderer alloc] init];
      [registration setCustomElementParser:progressBarRenderer];
```objective-c