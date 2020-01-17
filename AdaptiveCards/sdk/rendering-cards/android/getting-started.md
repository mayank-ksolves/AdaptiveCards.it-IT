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
# <a name="getting-started---android"></a>Guida introduttiva - Android

Questo renderer è destinato ai controlli nativi di Android.

## <a name="install-maven-package"></a>Installare il pacchetto Maven

[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)

Puoi trovare i pacchetti pubblicati ![qui](https://search.maven.org/search?q=g:io.adaptivecards)

Per includere libreria nel progetto, devi includere questa riga nel progetto gradle.build, nella sezione dependencies

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
È necessario modificare il numero di versione a seconda della versione da includere nel progetto

## <a name="add-import"></a>Aggiungere l'importazione

Per includere il modello a oggetti, aggiungi questa importazione

```
 import io.adaptivecards.objectmodel.*;
```

Per includere il renderer, aggiungi questa importazione

```
 import io.adaptivecards.renderer.*;
```

## <a name="next-steps"></a>Passaggi successivi

Per i passaggi successivi, vedi [Eseguire il rendering di una scheda](render-a-card.md).
