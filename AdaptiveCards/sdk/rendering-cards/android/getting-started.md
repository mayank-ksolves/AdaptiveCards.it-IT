---
title: Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: d15e0963427babe045a4db6f93800e09e0d95da9
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145501"
---
# <a name="getting-started---android"></a><span data-ttu-id="24789-102">Guida introduttiva - Android</span><span class="sxs-lookup"><span data-stu-id="24789-102">Getting started - Android</span></span>

<span data-ttu-id="24789-103">Questo renderer è destinato ai controlli nativi di Android.</span><span class="sxs-lookup"><span data-stu-id="24789-103">This is a renderer which targets Android native controls.</span></span>

## <a name="install-maven-package"></a><span data-ttu-id="24789-104">Installare il pacchetto Maven</span><span class="sxs-lookup"><span data-stu-id="24789-104">Install Maven package</span></span>

<span data-ttu-id="24789-105">[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span><span class="sxs-lookup"><span data-stu-id="24789-105">[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span></span>

<span data-ttu-id="24789-106">Puoi trovare i pacchetti pubblicati</span><span class="sxs-lookup"><span data-stu-id="24789-106">You can find the published packages</span></span> ![qui](https://search.maven.org/search?q=g:io.adaptivecards)

<span data-ttu-id="24789-108">Per includere libreria nel progetto, devi includere questa riga nel progetto gradle.build, nella sezione dependencies</span><span class="sxs-lookup"><span data-stu-id="24789-108">To include library to your project you must include this line into your project gradle.build under the dependencies section</span></span>

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
<span data-ttu-id="24789-109">È necessario modificare il numero di versione a seconda della versione da includere nel progetto</span><span class="sxs-lookup"><span data-stu-id="24789-109">You need to change the version number depending on the version you want to include into your project</span></span>

## <a name="add-import"></a><span data-ttu-id="24789-110">Aggiungere l'importazione</span><span class="sxs-lookup"><span data-stu-id="24789-110">Add import</span></span>

<span data-ttu-id="24789-111">Per includere il modello a oggetti, aggiungi questa importazione</span><span class="sxs-lookup"><span data-stu-id="24789-111">To include the object model, add this import</span></span>

```
 import io.adaptivecards.objectmodel.*;
```

<span data-ttu-id="24789-112">Per includere il renderer, aggiungi questa importazione</span><span class="sxs-lookup"><span data-stu-id="24789-112">To include the renderer, add this import</span></span>

```
 import io.adaptivecards.renderer.*;
```

## <a name="next-steps"></a><span data-ttu-id="24789-113">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="24789-113">Next steps</span></span>

<span data-ttu-id="24789-114">Per i passaggi successivi, vedi [Eseguire il rendering di una scheda](render-a-card.md).</span><span class="sxs-lookup"><span data-stu-id="24789-114">See [Render a card](render-a-card.md) for the next steps!</span></span>
