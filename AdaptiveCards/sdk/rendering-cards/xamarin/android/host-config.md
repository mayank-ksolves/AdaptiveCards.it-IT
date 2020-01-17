---
title: Configurazione host-Novell. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: 554b32d9d088e82fb0fd48bec4b94340e843abeb
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146125"
---
# <a name="host-config---android"></a>Configurazione host-Android

Per personalizzare il renderer, fornire un'istanza dell'oggetto HostConfig. Per la descrizione completa, vedere [schema di configurazione host](../../../../rendering-cards/host-config.md) .

Per creare un oggetto ```HostConfig``` da una stringa, usare il metodo ```DeserializeFromString```, come indicato di seguito:

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

HostConfig Config = HostConfig.DeserializeFromString(configJson);
```