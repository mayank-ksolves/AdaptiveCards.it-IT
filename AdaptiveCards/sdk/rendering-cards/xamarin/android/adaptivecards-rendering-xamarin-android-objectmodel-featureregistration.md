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
# <a name="feature-registration"></a><span data-ttu-id="807db-102">Registrazione delle funzionalità</span><span class="sxs-lookup"><span data-stu-id="807db-102">Feature Registration</span></span>

```csharp
public class FeatureRegistration : Java.Lang.Object 
```

<span data-ttu-id="807db-103">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="807db-103">**Namespace**</span></span>
```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.ObjectModel
```

## <a name="summary"></a><span data-ttu-id="807db-104">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="807db-104">Summary</span></span>

| <span data-ttu-id="807db-105">Metodi pubblici</span><span class="sxs-lookup"><span data-stu-id="807db-105">Public methods</span></span> | |
| --- | ---- |
| ```void``` | [```AddFeature(string featureName, string featureVersion)```](#addfeature) |
| ```string``` | [```GetFeatureVersion(string featureName)```](#getfeatureversion) |
| ```void``` | [```RemoveFeature (string featureName)```](#removefeature) |

## <a name="public-methods"></a><span data-ttu-id="807db-106">Metodi pubblici</span><span class="sxs-lookup"><span data-stu-id="807db-106">Public Methods</span></span>

---

### <a id="addfeature"></a><span data-ttu-id="807db-107">AddFeature</span><span class="sxs-lookup"><span data-stu-id="807db-107">AddFeature</span></span>
<p style='text-align:right'><span data-ttu-id="807db-108">Aggiunto nella versione 0.1.0</span><span class="sxs-lookup"><span data-stu-id="807db-108">Added in version 0.1.0</span></span></p>

```csharp
public void AddFeature (string featureName, 
                        string featureVersion)
```

<span data-ttu-id="807db-109">Aggiunge una funzionalità contenente il nome e la versione alla registrazione della funzionalità renderer.</span><span class="sxs-lookup"><span data-stu-id="807db-109">Adds a feature containing its name and version to the renderer feature registration.</span></span>

| <span data-ttu-id="807db-110">Parametri</span><span class="sxs-lookup"><span data-stu-id="807db-110">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="807db-111">featureName</span><span class="sxs-lookup"><span data-stu-id="807db-111">featureName</span></span> | ```string``` |
| <span data-ttu-id="807db-112">featureVersion</span><span class="sxs-lookup"><span data-stu-id="807db-112">featureVersion</span></span> | ```string``` |

#### <a name="sample"></a><span data-ttu-id="807db-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="807db-113">Sample</span></span>

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
CardRendererRegistration.Instance.RegisterFeatureRegistration(featureRegistration);
```

---

### <a id="getfeatureversion"></a><span data-ttu-id="807db-114">GetFeatureVersion</span><span class="sxs-lookup"><span data-stu-id="807db-114">GetFeatureVersion</span></span>
<p style='text-align:right'><span data-ttu-id="807db-115">Aggiunto nella versione 0.1.0</span><span class="sxs-lookup"><span data-stu-id="807db-115">Added in version 0.1.0</span></span></p>

```csharp
public string GetFeatureVersion (string featureName)
```

<span data-ttu-id="807db-116">Recupera la versione per una determinata funzionalità.</span><span class="sxs-lookup"><span data-stu-id="807db-116">Retrieves the version for a given feature.</span></span> 

| <span data-ttu-id="807db-117">Parametri</span><span class="sxs-lookup"><span data-stu-id="807db-117">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="807db-118">featureName</span><span class="sxs-lookup"><span data-stu-id="807db-118">featureName</span></span> | ```string``` |

| <span data-ttu-id="807db-119">Returns</span><span class="sxs-lookup"><span data-stu-id="807db-119">Returns</span></span> | |
| --- | --- |
| ```string``` | <span data-ttu-id="807db-120">Versione della funzionalità per la funzionalità specificata</span><span class="sxs-lookup"><span data-stu-id="807db-120">Feature version for the given feature</span></span> |

#### <a name="sample"></a><span data-ttu-id="807db-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="807db-121">Sample</span></span>

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
string featureVersion = featureRegistration.GetFeatureVersion("MyFeature"); // 1.2.0
```

---

### <a id="removefeature"></a><span data-ttu-id="807db-122">RemoveFeature</span><span class="sxs-lookup"><span data-stu-id="807db-122">RemoveFeature</span></span>
<p style='text-align:right'><span data-ttu-id="807db-123">Aggiunto nella versione 0.1.0</span><span class="sxs-lookup"><span data-stu-id="807db-123">Added in version 0.1.0</span></span></p>

```csharp
public void RemoveFeature (string featureName)
```

<span data-ttu-id="807db-124">Rimuove la funzionalità specificata dal dizionario delle funzionalità.</span><span class="sxs-lookup"><span data-stu-id="807db-124">Removes the given feature from the feature dictionary.</span></span>

| <span data-ttu-id="807db-125">Parametri</span><span class="sxs-lookup"><span data-stu-id="807db-125">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="807db-126">featureName</span><span class="sxs-lookup"><span data-stu-id="807db-126">featureName</span></span> | ```string``` |

#### <a name="sample"></a><span data-ttu-id="807db-127">Esempio</span><span class="sxs-lookup"><span data-stu-id="807db-127">Sample</span></span>

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
featureRegistration.RemoveFeature("MyFeature");
```