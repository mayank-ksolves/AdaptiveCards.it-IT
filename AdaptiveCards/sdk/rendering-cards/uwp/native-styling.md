---
title: Stile nativo-UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 08/15/2018
ms.topic: article
ms.openlocfilehash: da3c7616ce4fe307eda3073f7037842e3e3df81b
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417521"
---
# <a name="native-styling---uwp"></a>Stile nativo-UWP

Sebbene la configurazione host consentirà di ottenere la maggior parte delle piattaforme in ogni piattaforma, è probabile che sarà necessario eseguire alcuni stili nativi su ogni piattaforma. 

UWP semplifica questa operazione consentendo di passare un oggetto ResourceDictionary per lo stile, il comportamento, le animazioni e così via.

| Elemento | Nomi di stile |
|---|---|
| AdaptiveCard | Adaptive. Card| 
| Action.OpenUrl  | Adaptive. Action. OpenUrl  |
| Action.ShowCard | Adaptive. Action. ShowCard |
| Action.Submit  | Adattivo. azione. Invia  |
| Colonna | Adaptive. Column, Adaptive. Action. Tap |
| ColumnSet | Adaptive. ColumnStore, Adaptive. VerticalSeparator |
| Contenitore | Adaptive. container|
| Input. Choices | Adaptive. input. Choices, Adaptive. input. Choices. ComboBox, Adaptive. input. Choicet. CheckBox, Adaptive. input. Choicet. Radio, Adaptive. input. Choices. ComboBoxItem |
| Input. Data | Adaptive. input. Text. date
| Input. Number | Adaptive. input. Text. Number |
| Input. Text | Adaptive. input. Text |
| Input. Time | Adaptive. input. Text. Time |
| Input. interruttore| Adaptive. input. Attiva/Nascondi|
| Immagine  | Adaptive. image |
| ImageSet  | Adaptive. images |
| FactSet | Adaptive. Facts, Adaptive. fact. title, Adaptive. fact. Value |
| TextBlock  | Adaptive. TextBlock |

Questo dizionario risorse XAML di esempio che imposta lo sfondo di tutti i TextBlock su Aqua. È probabile che si desideri qualcosa di più avanzato😁

```xml
<ResourceDictionary
    xmlns="https://schemas.microsoft.com/winfx/2006/xaml/presentation" 
    xmlns:x="https://schemas.microsoft.com/winfx/2006/xaml">
    <Style x:Key="Adaptive.TextBlock" TargetType="TextBlock">
        <Setter Property="Background" Value="Aqua"></Setter>
    </Style>
</ResourceDictionary>
```
```csharp
// Use a ResourceDictionary instance
// DON'T use this property if rendering from a server
renderer.Resources = myResourceDictionary;
```
