---
title: Classe FeatureRegistration-Novell. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: c1975197996e54626b464abe9181f0b02895ee4d
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146145"
---
# <a name="feature-registration"></a>Registrazione delle funzionalità

```csharp
public class FeatureRegistration : Java.Lang.Object 
```

**Namespace**
```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.ObjectModel
```

## <a name="summary"></a>Riepilogo

| Metodi pubblici | |
| --- | ---- |
| ```void``` | [```AddFeature(string featureName, string featureVersion)```](#addfeature) |
| ```string``` | [```GetFeatureVersion(string featureName)```](#getfeatureversion) |
| ```void``` | [```RemoveFeature (string featureName)```](#removefeature) |

## <a name="public-methods"></a>Metodi pubblici

---

### <a id="addfeature"></a>AddFeature
<p style='text-align:right'>Aggiunto nella versione 0.1.0</p>

```csharp
public void AddFeature (string featureName, 
                        string featureVersion)
```

Aggiunge una funzionalità contenente il nome e la versione alla registrazione della funzionalità renderer.

| Parametri | |
| --- | --- |
| featureName | ```string``` |
| featureVersion | ```string``` |

#### <a name="sample"></a>Esempio

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
CardRendererRegistration.Instance.RegisterFeatureRegistration(featureRegistration);
```

---

### <a id="getfeatureversion"></a>GetFeatureVersion
<p style='text-align:right'>Aggiunto nella versione 0.1.0</p>

```csharp
public string GetFeatureVersion (string featureName)
```

Recupera la versione per una determinata funzionalità. 

| Parametri | |
| --- | --- |
| featureName | ```string``` |

| Returns | |
| --- | --- |
| ```string``` | Versione della funzionalità per la funzionalità specificata |

#### <a name="sample"></a>Esempio

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
string featureVersion = featureRegistration.GetFeatureVersion("MyFeature"); // 1.2.0
```

---

### <a id="removefeature"></a>RemoveFeature
<p style='text-align:right'>Aggiunto nella versione 0.1.0</p>

```csharp
public void RemoveFeature (string featureName)
```

Rimuove la funzionalità specificata dal dizionario delle funzionalità.

| Parametri | |
| --- | --- |
| featureName | ```string``` |

#### <a name="sample"></a>Esempio

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
featureRegistration.RemoveFeature("MyFeature");
```