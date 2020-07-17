---
title: Estendibilità-JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 07/16/2020
ms.topic: article
ms.openlocfilehash: 81c60e200d2fcbc844a3ae3f4fdefa0ddaa399d3
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417537"
---
# <a name="extensibility---javascript"></a>Estendibilità-JavaScript

## <a name="extensibility-with-the-js-sdk-version-20-and-greater"></a>Estendibilità con JS SDK versione 2,0 e successive

### <a name="before-you-start"></a>Prima di iniziare

> **Importante**: la versione 2,0 e successive di JS SDK si avvale di elementi [Decorator typescript](https://www.typescriptlang.org/docs/handbook/decorators.html). Gli elementi Decorator sono ancora una funzionalità sperimentale e devono essere abilitati in modo esplicito nel `tsconfig.js` file:

```json
{
   "compilerOptions": {
       "experimentalDecorators": true
   }
}
```
La versione 2,0 di JS SDK introduce modifiche di rilievo nel modo in cui gli elementi e le azioni personalizzati vengono implementati e registrati. Per un esempio su come implementare e registrare un elemento o un'azione usando le versioni precedenti dell'SDK, vedere [estensibilità con JS SDK prima della versione 2,0](#extensibility-with-the-js-sdk-prior-to-version-20).


### <a name="custom-elements"></a>Elementi personalizzati
I passaggi per la creazione di un tipo di elemento della scheda Adaptive personalizzato sono:
- Crea una nuova classe che deriva da`CardElement`
- Creare lo schema dichiarando le definizioni di proprietà statiche
- Implementare i `getJsonTypeName` metodi, e `internalRender`
- Registrarlo nel registro di sistema globale degli elementi o usare un registro personalizzato per ogni singola scheda


Di seguito è riportato un esempio che consente di implementare un semplice elemento indicatore di stato:
```typescript
export class ProgressBar extends AC.CardElement {
    static readonly JsonTypeName = "ProgressBar";

    //#region Schema

    static readonly titleProperty = new AC.StringProperty(AC.Versions.v1_0, "title", true);
    static readonly valueProperty = new AC.NumProperty(AC.Versions.v1_0, "value");

    @AC.property(ProgressBar.titleProperty)
    get title(): string | undefined {
        return this.getValue(ProgressBar.titleProperty);
    }

    set title(value: string) {
        if (this.title !== value) {
            this.setValue(ProgressBar.titleProperty, value);

            this.updateLayout();
        }
    }

    @AC.property(ProgressBar.valueProperty)
    get value(): number {
        return this.getValue(ProgressBar.valueProperty);
    }

    set value(value: number) {
        let adjustedValue = value;

        if (adjustedValue < 0) {
            adjustedValue = 0;
        }
        else if (adjustedValue > 100) {
            adjustedValue = 100;
        }

        if (this.value !== adjustedValue) {
            this.setValue(ProgressBar.valueProperty, adjustedValue);

            this.updateLayout();
        }
    }

    //#endregion

    private _titleElement: HTMLElement;
    private _leftBarElement: HTMLElement;
    private _rightBarElement: HTMLElement;

    protected internalRender(): HTMLElement {
        let element = document.createElement("div");

        let textBlock = new AC.TextBlock();
        textBlock.setParent(this);
        textBlock.text = this.title;
        textBlock.wrap = true;

        this._titleElement = textBlock.render();
        this._titleElement.style.marginBottom = "6px";

        let progressBarElement = document.createElement("div");
        progressBarElement.style.display = "flex";

        this._leftBarElement = document.createElement("div");
        this._leftBarElement.style.height = "6px";
        this._leftBarElement.style.backgroundColor = AC.stringToCssColor(this.hostConfig.containerStyles.emphasis.foregroundColors.accent.default);

        this._rightBarElement = document.createElement("div");
        this._rightBarElement.style.height = "6px";
        this._rightBarElement.style.backgroundColor = AC.stringToCssColor(this.hostConfig.containerStyles.emphasis.backgroundColor);

        progressBarElement.append(this._leftBarElement, this._rightBarElement);

        element.append(this._titleElement, progressBarElement);

        return element;
    }

    getJsonTypeName(): string {
        return ProgressBar.JsonTypeName;
    }

    updateLayout(processChildren: boolean = true) {
        super.updateLayout(processChildren);

        if (this.renderedElement) {
            if (this.title) {
                this._titleElement.style.display = "none";
            }
            else {
                this._titleElement.style.removeProperty("display");
            }

            this._leftBarElement.style.flex = "1 1 " + this.value + "%";
            this._rightBarElement.style.flex = "1 1 " + (100 - this.value) + "%";
        }
    }
}
```
È tutto. È ora necessario registrare l'elemento ProgressBar per poter essere riconosciuto dall'SDK. È possibile registrarlo a livello globale:

```typescript
AC.GlobalRegistry.elements.register(ProgressBar.JsonTypeName, ProgressBar);
```

In alternativa, è possibile usare un registro per scheda, che consente l'uso di diversi registri per schede diverse nell'applicazione:

```typescript
// Create a custom registry for elements
let elementRegistry = new AC.CardObjectRegistry<AC.CardElement>();

// Populate it with the default set of elements
AC.GlobalRegistry.populateWithDefaultElements(elementRegistry);

// Register the custom ProgressBar element
elementRegistry.register(ProgressBar.JsonTypeName, ProgressBar);

// Parse a card payload using the custom registry
let serializationContext = new AC.SerializationContext();
serializationContext.setElementRegistry(elementRegistry);

let card = new AC.AdaptiveCard();
card.parse(
    {
        type: "AdaptiveCard",
        version: "1.0",
        body: [
            {
                type: "ProgressBar",
                title: "This is a progress bar",
                value: 45
            }
        ]
    },
    serializationContext
);
```

### <a name="custom-actions"></a>Azioni personalizzate
I passaggi per l'implementazione di un'azione personalizzata sono gli stessi di quelli per gli elementi. L'unica differenza è che le azioni vengono registrate nei registri delle azioni e non nei registri di elementi.

```typescript
export class AlertAction extends AC.Action {
    static readonly JsonTypeName = "Action.Alert";

    //#region Schema

    static readonly textProperty = new AC.StringProperty(AC.Versions.v1_0, "text", true);

    @AC.property(AlertAction.textProperty)
    text?: string;

    //#endregion

    getJsonTypeName(): string {
        return AlertAction.JsonTypeName;
    }

    execute() {
        alert(this.text);
    }
}
```

Registrare la nuova azione a livello globale:
```typescript
AC.GlobalRegistry.actions.register(AlertAction.JsonTypeName, AlertAction);
```

In alternativa, usare un registro per scheda:
```typescript
// Create a custom registry for actions
let actionRegistry = new AC.CardObjectRegistry<AC.Action>();

// Populate it with the default set of actions
AC.GlobalRegistry.populateWithDefaultActions(actionRegistry);

// Register the custom AlertAction type
actionRegistry.register(AlertAction.JsonTypeName, AlertAction);

// Parse a card payload using the custom registry
let serializationContext = new AC.SerializationContext();
serializationContext.setActionRegistry(actionRegistry);

let card = new AC.AdaptiveCard();
card.parse(
    {
        type: "AdaptiveCard",
        version: "1.0",
        body: [
            {
                type: "TextBlock",
                text: "This demonstrates the AlertAction action."
            }
        ],
        actions: [
            {
                type: "Action.Alert",
                title: "Click me!",
                text: "Hello World"
            }
        ]
    },
    serializationContext
);
```

## <a name="extensibility-with-the-js-sdk-prior-to-version-20"></a>Estendibilità con JS SDK prima della versione 2,0

### <a name="custom-elements"></a>Elementi personalizzati

I passaggi per la creazione di un tipo di elemento della scheda Adaptive personalizzato sono:
- Crea una nuova classe che deriva da`CardElement`
- Implementare i `getJsonTypeName` relativi `parse` metodi,, `toJSON` `internalRender` e `renderSpeech`
- Registrarlo aggiungendolo al registro elementi del renderer

Di seguito è riportato un esempio che consente di implementare un semplice elemento indicatore di stato:

```typescript
import * as Adaptive from "adaptivecards";

export class ProgressBar extends Adaptive.CardElement {
    private _title: string;
    private _value: number = 0;
    private _titleElement: HTMLElement;
    private _leftBarElement: HTMLElement;
    private _rightBarElement: HTMLElement;

    protected internalRender(): HTMLElement {
        let element = document.createElement("div");

        let textBlock = new Adaptive.TextBlock();
        textBlock.setParent(this);
        textBlock.text = this.title;
        textBlock.wrap = true;

        this._titleElement = textBlock.render();
        this._titleElement.style.marginBottom = "6px";

        let progressBarElement = document.createElement("div");
        progressBarElement.style.display = "flex";

        this._leftBarElement = document.createElement("div");
        this._leftBarElement.style.height = "6px";
        this._leftBarElement.style.backgroundColor = Adaptive.stringToCssColor(this.hostConfig.containerStyles.emphasis.foregroundColors.accent.default);

        this._rightBarElement = document.createElement("div");
        this._rightBarElement.style.height = "6px";
        this._rightBarElement.style.backgroundColor = Adaptive.stringToCssColor(this.hostConfig.containerStyles.emphasis.backgroundColor);

        progressBarElement.append(this._leftBarElement, this._rightBarElement);

        element.append(this._titleElement, progressBarElement);

        return element;
    }

    getJsonTypeName(): string {
        return "ProgressBar";
    }

    toJSON(): any {
        let result = super.toJSON();

        Adaptive.setProperty(result, "title", this.title);
        Adaptive.setProperty(result, "value", this.value);

        return result;
    }

    parse(json: any, errors?: Array<Adaptive.IValidationError>) {
        super.parse(json, errors);

        this.title = Adaptive.getStringValueOrDefault(json["title"], undefined);
        this.value = Adaptive.getValueOrDefault(json["value"], this._value);
    }

    updateLayout(processChildren: boolean = true) {
        super.updateLayout(processChildren);

        if (this.renderedElement) {
            if (Adaptive.isNullOrEmpty(this.title)) {
                this._titleElement.style.display = "none";
            }
            else {
                this._titleElement.style.removeProperty("display");
            }

            this._leftBarElement.style.flex = "1 1 " + this.value + "%";
            this._rightBarElement.style.flex = "1 1 " + (100 - this.value) + "%";
        }
    }

    renderSpeech(): string {
        return (Adaptive.isNullOrEmpty(this.title) ? "Progress" : this.title) + " " + Math.ceil(this.value) + "%";
    }

    get title(): string {
        return this._title;
    }

    set title(value: string) {
        if (this._title !== value) {
            this._title = value;

            this.updateLayout();
        }
    }

    get value(): number {
        return this._value;
    }

    set value(value: number) {
        let adjustedValue = value;

        if (adjustedValue < 0) {
            adjustedValue = 0;
        }
        else if (adjustedValue > 100) {
            adjustedValue = 100;
        }

        if (this._value !== adjustedValue) {
            this._value = adjustedValue;

            this.updateLayout();
        }
    }
}
```

È tutto. A questo punto, registrare la classe indicatore di stato con il renderer:

```typescript
Adaptive.AdaptiveCard.elementTypeRegistry.registerType("ProgressBar", () => { return new ProgressBar(); });
```

## <a name="custom-actions"></a>Azioni personalizzate

La procedura per la creazione di un'azione personalizzata per le schede adattive è essenzialmente identica a quella per gli elementi personalizzati. Ecco un semplice esempio di azione di avviso che visualizza semplicemente una finestra di messaggio con testo configurabile:

```typescript
import * as Adaptive from "adaptivecards";

export class AlertAction extends Adaptive.Action {
    text: string;

    getJsonTypeName(): string {
        return "Action.ALert";
    }

    execute() {
        alert(this.text);
    }

    parse(json: any) {
        super.parse(json);

        this.text = Adaptive.getStringValueOrDefault(json["text"], "Alert!");
    }

    toJSON() {
        let result = super.toJSON();

        Adaptive.setProperty(result, "text", this.text);

        return result;
    }
}
```

Registrare ora la nuova azione:

```typescript
Adaptive.AdaptiveCard.actionTypeRegistry.registerType("Action.Alert", () => { return new AlertAction(); });
```

## <a name="example"></a>Esempio

Ecco una scheda di esempio che usa sia l'elemento ProgressBar che l'azione AlertAction:
```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "size": "Medium",
            "weight": "Bolder",
            "text": "Custom ProgressBar element"
        },
        {
            "type": "ProgressBar",
            "title": "Please wait...",
            "value": 10
        }
    ],
    "actions": [
        {
            "type": "Action.Alert",
            "title": "Click me",
            "text": "Hello world!"
        }
    ]
}
```

Ecco come viene eseguito il rendering: ![ Image](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)
