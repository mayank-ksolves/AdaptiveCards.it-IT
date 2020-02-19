---
title: Stile nativo-.NET WPF SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 204845f942be4e7d04e20e9cd64d826daef26e93
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454024"
---
# <a name="native-styling---net-wpf"></a>Stile nativo-WPF .NET

Sebbene la configurazione host consentirà di ottenere la maggior parte delle piattaforme in ogni piattaforma, è probabile che sarà necessario eseguire alcuni stili nativi su ogni piattaforma. 

WPF semplifica questa operazione consentendo di passare un oggetto ResourceDictionary per lo stile, il comportamento, le animazioni e così via.

| Elemento | Nomi di stile |
|---|---|
| AdaptiveCard | Adaptive. Card| 
| Action.OpenUrl  | Adaptive.Action.OpenUrl  |
| Action.ShowCard | Adaptive.Action.ShowCard |
| Action.Submit  | Adattivo. azione. Invia  |
| Column | Adaptive. Column, Adaptive. Action. Tap |
| ColumnSet | Adaptive. ColumnStore, Adaptive. VerticalSeparator |
| Contenitore | Adaptive. container|
| Input.ChoiceSet | Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem |
| Input. Data | Adaptive.Input.Text.Date
| Input. Number | Adaptive.Input.Text.Number |
| Input.Text | Adaptive.Input.Text |
| Input.Time | Adaptive.Input.Text.Time |
| Input.Toggle| Adaptive. input. Attiva/Nascondi|
| Immagine  | Adaptive. image |
| ImageSet  | Adaptive.ImageSet |
| FactSet | Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value |
| TextBlock  | Adaptive.TextBlock |

Questo dizionario risorse XAML di esempio che imposta lo sfondo di tutti i TextBlock su Aqua. È probabile che si desideri una soluzione più avanzata rispetto a questa 😁

```xml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" 
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
    <Style x:Key="Adaptive.TextBlock" TargetType="TextBlock">
        <Setter Property="Background" Value="Aqua"></Setter>
    </Style>
</ResourceDictionary>
```
```csharp
// Use a ResourceDictionary instance
// DON'T use this property if rendering from a server
renderer.Resources = myResourceDictionary;

// ... or load it from a file path
// USE this if rendering from a server
renderer.ResourcesPath = <path-to-my-resource-dictionary.xaml>;
```

> [!IMPORTANT]
> **Nota sulla generazione di immagini lato server** Il renderer WPF fornisce un metodo di `RenderCardToImageAsync` che può essere utilizzato per la generazione di immagini lato server. È necessario utilizzare la proprietà `ResourcesPath` solo se utilizzata in questo ambiente. Per ulteriori informazioni, vedere la documentazione per il [rendering delle immagini](../net-image/getting-started.md)