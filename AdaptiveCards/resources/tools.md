---
title: Strumenti delle schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: 819788313d78b4057fb5d3dc4d5a9be658566642
ms.sourcegitcommit: 996fc604e59f72ba1dd96c29f4b517862a5264e9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/04/2020
ms.locfileid: "87566025"
---
# <a name="tools-and-samples"></a>Strumenti ed esempi

## <a name="card-designer"></a>Strumento di progettazione delle schede 

Ti serve uno strumento per progettare le schede? All'indirizzo [https://adaptivecards.io/designer](https://adaptivecards.io/designer) è disponibile uno strumento basato su browser per la progettazione di schede adattive.

[![screenshot dello strumento di progettazione](media/tools/designer.jpg)](https://adaptivecards.io/designer)

### <a name="embed-the-designer-into-your-app"></a>Incorporare lo strumento di progettazione nell'app

Ma perché dovresti indirizzare gli utenti a tale sito quando puoi **incorporare lo strumento di progettazione delle schede direttamente nell'app Web** usando la libreria JavaScript? 

Per iniziare, vedi il pacchetto [adaptivecards-designer](https://npmjs.com/adaptivecards-designer).

## <a name="schema-validation"></a>Convalida dello schema

La convalida dello schema è un modo efficace per semplificare la creazione e abilitare gli strumenti.

È stato fornito un [file di schema JSON](https://adaptivecards.io/schemas/1.2.0/adaptive-card.json) completo per la modifica e la convalida di schede adattive in JSON. L'URL dello schema è con versione, pertanto le versioni più recenti delle schede adattive avranno un URL corrispondente.

In Visual Studio e Visual Studio Code puoi ottenere IntelliSense automatico includendo un riferimento `$schema`.

![non valido](media/tools/invalidjson1.png)

![completamento automatico](media/tools/autocomplete.png)

## <a name="example"></a>Esempio

```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

## <a name="visual-studio-code-extensions"></a>Estensioni di Visual Studio Code

### <a name="adaptive-cards-studio"></a>**Adaptive Card Studio**

![marketplace](https://madewithcards.blob.core.windows.net/uploads/29bb3d02-2158-40b8-8420-4dd1f15da34c-acstudio.png)

Con Adaptive Card Studio puoi creare e modificare schede direttamente in Visual Studio Code. L'estensione rileva automaticamente tutte le schede adattive nell'area di lavoro e consente di modificare facilmente il modello di scheda e i dati di esempio.

[Leggi altre informazioni e installa l'estensione da Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=madewithcardsio.adaptivecardsstudiobeta)


### <a name="adaptive-card-viewer"></a>**Adaptive Card Viewer**

È stata creata un'estensione di Visual Studio Code che ti consente di visualizzare la scheda che stai modificando in tempo reale all'interno dell'editor. 

![estensione](media/tools/vscode-extension.png)

Per eseguire l'installazione, apri il Marketplace delle estensioni e cerca **Adaptive Card Viewer**.

![marketplace](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a>Uso

Quando modifichi un file con estensione json con una proprietà `$schema` della scheda adattiva, puoi visualizzare tramite `Ctrl+Shift+V A`.
```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a>Opzioni

Per Adaptive Card Viewer è disponibile l'impostazione seguente di Visual Studio Code. Questa impostazione può essere configurata in Impostazioni utente o in Impostazioni area di lavoro.

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a>Esempio di visualizzatore WPF

Il [progetto di esempio di visualizzatore WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) ti consente di visualizzare le schede usando WPF/XAML in un computer Windows.  Un editor `hostconfig` è integrato per la modifica e la visualizzazione delle impostazioni di configurazione host. Salva tali impostazioni come JSON per usarle nel rendering all'interno dell'applicazione.

![visualizzatore WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a>Esempio di renderer di immagini WPF

Il [progetto di esempio di renderer di immagini](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) converte qualsiasi scheda in un file PNG dalla riga di comando tramite WPF. 
