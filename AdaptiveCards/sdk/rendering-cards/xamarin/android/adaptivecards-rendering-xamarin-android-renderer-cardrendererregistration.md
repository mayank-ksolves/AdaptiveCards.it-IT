---
title: Classe CardRendererRegistration-Novell. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: 4254c1c3c0f275434fae2a92e20679b6fa136b16
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145985"
---
# <a name="cardrendererregistration"></a>CardRendererRegistration

```csharp
public class CardRendererRegistration : Java.Lang.Object
```

**Namespace**
```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer.Registration
```

### <a name="summary"></a>Riepilogo

| Metodi pubblici | |
| --- | ---- |
| ```void``` | [```RegisterFeatureRegistration (FeatureRegistration featureRegistration)```](#registerfeatureregistration) |

## <a name="public-methods"></a>Metodi pubblici

--- 

### <a id="registerfeatureregistration"></a>RegisterFeatureRegistration
<p style='text-align:right'>Aggiunto nella versione 0.1.0</p>

```csharp
public void RegisterFeatureRegistration (FeatureRegistration featureRegistration)
```

Registra un oggetto [```FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md) per il renderer della scheda da utilizzare.

| Parametri | |
| --- | --- |
| featureRegistration | [```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md) |

#### <a name="sample"></a>Esempio

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
CardRendererRegistration.Instance.RegisterFeatureRegistration(featureRegistration);
```