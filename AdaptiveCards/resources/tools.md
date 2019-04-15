---
title: Le schede adattive strumenti
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: 35ce89653a6cf2a313518be0f221a166e1eb7711
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552503"
---
# <a name="card-designer"></a>Finestra di progettazione smart card 

Necessario per uno strumento per le schede di progettazione? Servono solo la finestra di progettazione basata su browser scheda adattiva in [https://adaptivecards.io/designer](https://adaptivecards.io/designer)

[![screenshot della finestra di progettazione](media/tools/designer.jpg)](https://adaptivecards.io/designer)

## <a name="embed-the-designer-into-your-app"></a>Incorporare la finestra di progettazione nell'app

Motivo per cui indirizzare gli utenti non esiste, quando possibile, ma **incorporare la finestra di progettazione di smart card direttamente nell'interfaccia web** app usando la libreria JavaScript. 

Consultare il [adaptivecards-finestra di progettazione](https://npmjs.com/adaptivecards-designer) pacchetto per iniziare.

# <a name="schema-validation"></a>Convalida dello schema

Convalida dello schema è un modo potente per rendere più semplice di creazione e l'abilitazione degli strumenti.

## <a name="json-schema"></a>Schema JSON
Microsoft ha fornito una completa [file di Schema JSON](http://adaptivecards.io/schemas/adaptive-card.json) per la modifica e convalida le schede adattive in formato json.

In Visual Studio e Visual Studio Code è possibile ottenere Intellisense automatico includendo un `$schema` riferimento.

![non valido](media/tools/invalidjson1.png)

![Completamento automatico](media/tools/autocomplete.png)

### <a name="example"></a>Esempio

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "0.5",
    "body": []
}
```

# <a name="tools-and-samples"></a>Strumenti ed esempi
Esistono alcuni strumenti e gli esempi nell'albero di origine che sono riferimenti utili, nonché strumenti utili.

## <a name="visual-studio-code-extension"></a>Estensione Visual Studio Code
È stata creata un'estensione di Visual Studio code che consente di visualizzare la scheda che si sta modificando in tempo reale all'interno dell'editor stesso. 

![Estensione](media/tools/vscode-extension.png)

Per installare, aprire estensioni del Marketplace e cercare **adattivo scheda Visualizzatore**.

![Marketplace](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a>Uso

Quando si modifica un file con estensione JSON con una scheda adattiva `$schema` è possibile visualizzare utilizzando proprietà `Ctrl+Shift+V A`.
```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a>Opzioni

La seguente impostazione di Visual Studio Code è disponibile per il Visualizzatore AdaptiveCards. Può essere impostata in impostazioni utente o dell'area di lavoro.

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a>Esempio di Visualizzatore WPF
Il [progetto di esempio Visualizzatore WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) consente di visualizzare le schede tramite/Xaml WPF in un computer Windows.  Oggetto `hostconfig` editor è disponibile per la modifica e la visualizzazione delle impostazioni di configurazione host. Salvare queste impostazioni in un formato JSON per utilizzarle nel rendering nell'applicazione.

![Visualizzatore WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a>Esempio di ImageRender WPF
Il [progetto di esempio ImageRender](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) Trasforma qualsiasi scheda in un file PNG dalla riga di comando utilizzando WPF. 
