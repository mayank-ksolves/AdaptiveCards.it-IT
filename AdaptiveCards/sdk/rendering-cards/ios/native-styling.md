---
title: Stile nativo-iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: f9ed839a19ac778381fa36361ad37e95b7ab5e08
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727464"
---
# <a name="native-styling---ios"></a>Stile nativo-iOS

Usare XIB per lo stile con granularità fine.

Esistono i XIB seguenti

| XIB | Utilizzo |
|---|---|
| ACRButton. xib | pulsanti |
| ACRCellForCompactMode. xib   | Modalità compatta di opzioni|
| ACRDatePicker. xib | DatePicker per input. date |
| ACRDateTextField. xib  | TextField per input. date |
| ACRInputTableView. xib   | Contenitore per gli input |
| ACRLabelView. xib  | TextBlock |
| ACRPickerView. xib | Opzioni |
| ACRQuickActionMultilineView. xib  | Azioni rapide con più righe |
| ACRQuickActionView. xib | Azioni rapide |
| ACRTextField. xib | Input |

XIB può essere modificato tramite XCode IB.
Dopo la modifica di XIB nella specifica.
Da un terminale
```
ibtool --compile name.nib name.xib 
```

Ad esempio, per applicare uno stile a un pulsante
```
ibtool --compile ACRButton.nib ACRButton.xib 
```

I file del pennino generati possono essere sostituiti in AdaptiveCards. Framework
