---
title: HostConfig per le schede adattive
author: paulcam206
ms.author: paulcam
ms.date: 09/18/2018
ms.topic: reference
ms.openlocfilehash: 46ba9987cf162e95ab86dcdafa55e10df29b1121
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552593"
---
# <a name="what-is-hostconfig"></a>Che cos'è HostConfig?
`HostConfig` è un **oggetto di configurazione cross-platform** che specifica la modalità di generazione dell'interfaccia utente in un Renderer scheda adattiva.

In questo modo le proprietà che sono indipendenti dalla piattaforma per la condivisione tra i renderer su diverse piattaforme e dispositivi. Consente inoltre gli strumenti da creare che ti offre un'idea dell'aspetto che scheda sarebbe necessario per un determinato ambiente.

Vedere un campione [HostConfig.json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) per avere una visione del relativo contenuto.

---

   * [`AdaptiveCardConfig`](#schema-adaptivecardconfig) -Le opzioni Toplevel per `AdaptiveCards`
   * [`ActionsConfig`](#schema-actionsconfig) -Opzioni per `Action`s
   * [`ContainerStylesConfig`](#schema-containerstylesconfig) -Applicazione di stili per impostazione predefinita ed enfasi i contenitori di controlli
   * [`FactSetConfig`](#schema-factsetconfig) : Controlla la visualizzazione di `FactSet`s
   * [`FontSizesConfig`](#schema-fontsizesconfig) : Controlla le metriche di dimensioni del carattere per gli stili di testo diversa
   * [`FontWeightsConfig`](#schema-fontweightsconfig) : Controlla la metrica di peso del tipo di carattere
   * [`ForegroundColorsConfig`](#schema-foregroundcolorsconfig) : Controlla i colori dei caratteri diverse
   * [`ImageSetConfig`](#schema-imagesetconfig) : Controlla la modalità `ImageSet`s vengono visualizzati
   * [`ImageSizesConfig`](#schema-imagesizesconfig) : Controlla `Image` dimensioni
   * [`MediaConfig`](#schema-mediaconfig) : Controlla la visualizzazione e il comportamento di `Media` elementi
   * [`SeparatorConfig`](#schema-separatorconfig) : Controlla la modalità di visualizzazione separatore
   * [`ShowCardConfig`](#schema-showcardconfig) : Controlla il comportamento e lo stile delle `Action.ShowCard`
   * [`SpacingsConfig`](#schema-spacingsconfig) : Controlla come devono essere disposti gli elementi
   * [`TextBlockConfig`](#schema-textblockconfig) -I parametri controllo della visualizzazione di testo

# <a name="card-configuration"></a>Configurazione della scheda

<a name="schema-adaptivecardconfig"></a>
## <a name="adaptivecardconfig"></a>AdaptiveCardConfig

Opzioni di livello superiore per `AdaptiveCards`

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**allowCustomStyle**|`boolean`| No, predefinito: `true`|Controlla se è consentita l'applicazione di stili personalizzati|1.0
|**supportsInteractivity**|`boolean`| No, predefinito: `true`|Controllare se interattiva `Action`è consentito da richiamare|1.0
|**imageBaseUrl**|`string`| No|URL di base da utilizzare durante il caricamento delle risorse|1.0
|**fontFamily**|`string`| No, predefinito: `"Calibri"`|Tipo di carattere da utilizzare per il rendering del testo|1.0
|**actions**|`object`| No|Opzioni per `Action`s|1.0
|**adaptiveCard**|`object`| No|Opzioni di livello superiore per `AdaptiveCards`|1.0
|**containerStyles**|`object`| No|Applicazione di stili per impostazione predefinita ed enfasi i contenitori di controlli|1.0
|**imageSizes**|`object`| No|Controlli `Image` dimensioni|1.0
|**imageSet**|`object`| No|Controlli come `ImageSet`s vengono visualizzati|1.0
|**factSet**|`object`| No|Determina la visualizzazione di `FactSet`s|1.0
|**fontSizes**|`object`| No|Consente di controllare le metriche di dimensioni del carattere per gli stili di testo diversa|1.0
|**fontWeights**|`object`| No|Metrica di peso del carattere di controlli|1.0
|**spacing**|`object`| No|Controlla la modalità layout di elementi|1.0
|**separator**|`object`| No|Controlla la modalità di visualizzazione separatore|1.0
|**media**|`object`| No|Consente di controllare la visualizzazione e il comportamento di `Media` elementi|1.1


<a name="schema-actionsconfig"></a>
## <a name="actionsconfig"></a>ActionsConfig

Opzioni per `Action`s

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**actionsOrientation**|`string`| No, predefinito: `"horizontal"`|Consente di controllare la disposizione dei pulsanti|1.0
|**actionAlignment**|`string`| No, predefinito: `"stretch"`|Layout di controllo di pulsanti|1.0
|**buttonSpacing**|`integer`| No, predefinito: `10`|Consente di controllare quanta spaziatura da usare tra pulsanti|1.0
|**maxActions**|`integer`| No, predefinito: `5`|Controlla il numero di azioni consentito in totale|1.0
|**spacing**|`string`| No, predefinito: `"default"`|Controlli spaziatura complessivo dell'elemento action|1.0
|**showCard**|`object`| No|Comportamento di controlli e stili di `Action.ShowCard`|1.0
|**iconPlacement**|`string`| No, predefinito: `"aboveTitle"`|Determina dove posizionare l'icona di azione|1.0
|**iconSize**|`integer`| No, predefinito: `30`|Controlli delle dimensioni dell'icona azione|1.0


<a name="schema-containerstylesconfig"></a>
## <a name="containerstylesconfig"></a>ContainerStylesConfig

Applicazione di stili per impostazione predefinita ed enfasi i contenitori di controlli

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**impostazione predefinita**|`object`| No|Stile contenitore predefinito|1.0
|**emphasis**|`object`| No|Tipo di contenitore da usare per enfasi|1.0


<a name="schema-factsetconfig"></a>
## <a name="factsetconfig"></a>FactSetConfig

Determina la visualizzazione di `FactSet`s

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**title**|`object`| No, predefinito: `{"weight":"bolder","size":"default","color":"default","isSubtle":false,"wrap":true,"maxWidth":150}`|Parametri di controllo della visualizzazione di testo|1.0
|**value**|`object`| No, predefinito: `{"weight":"default","size":"default","color":"default","isSubtle":false,"wrap":true,"maxWidth":0}`|Parametri di controllo della visualizzazione di testo|1.0
|**spacing**|`integer`| No, predefinito: `10`|&nbsp;|1.0


<a name="schema-fontsizesconfig"></a>
## <a name="fontsizesconfig"></a>FontSizesConfig

Consente di controllare le metriche di dimensioni del carattere per gli stili di testo diversa

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**small**|`integer`| No, predefinito: `10`|Dimensione del carattere di piccole dimensioni|1.0
|**impostazione predefinita**|`integer`| No, predefinito: `12`|Dimensioni del carattere predefinite|1.0
|**medium**|`integer`| No, predefinito: `14`|Dimensione media dei caratteri|1.0
|**large**|`integer`| No, predefinito: `17`|Dimensioni del carattere grandi|1.0
|**extraLarge**|`integer`| No, predefinito: `20`|Dimensione del carattere extra large|1.0


<a name="schema-fontweightsconfig"></a>
## <a name="fontweightsconfig"></a>FontWeightsConfig

Metrica di peso del carattere di controlli

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**lighter**|`integer`| No, predefinito: `200`|&nbsp;|1.0
|**impostazione predefinita**|`integer`| No, predefinito: `400`|&nbsp;|1.0
|**bolder**|`integer`| No, predefinito: `800`|&nbsp;|1.0


<a name="schema-foregroundcolorsconfig"></a>
## <a name="foregroundcolorsconfig"></a>ForegroundColorsConfig

Controlla i colori dei caratteri diverse

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**impostazione predefinita**|`object`| No, predefinito: `{"default":"#FF000000","subtle":"#B2000000"}`|&nbsp;|1.0
|**accent**|`object`| No, predefinito: `{"default":"#FF0000FF","subtle":"#B20000FF"}`|&nbsp;|1.0
|**dark**|`object`| No, predefinito: `{"default":"#FF101010","subtle":"#B2101010"}`|&nbsp;|1.0
|**light**|`object`| No, predefinito: `{"default":"#FFFFFFFF","subtle":"#B2FFFFFF"}`|&nbsp;|1.0
|**good**|`object`| No, predefinito: `{"default":"#FF008000","subtle":"#B2008000"}`|&nbsp;|1.0
|**warning**|`object`| No, predefinito: `{"default":"#FFFFD700","subtle":"#B2FFD700"}`|&nbsp;|1.0
|**attention**|`object`| No, predefinito: `{"default":"#FF8B0000","subtle":"#B28B0000"}`|&nbsp;|1.0


<a name="schema-imagesetconfig"></a>
## <a name="imagesetconfig"></a>ImageSetConfig

Controlli come `ImageSet`s vengono visualizzati

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**imageSize**|`string`| No, predefinito: `"auto"`|Ridimensionamento immagine singoli controlli|1.0
|**maxImageHeight**|`integer`| No, predefinito: `100`|Limitare l'altezza dell'immagine a questo valore|1.0


<a name="schema-imagesizesconfig"></a>
## <a name="imagesizesconfig"></a>ImageSizesConfig

Controlli `Image` dimensioni

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**small**|`integer`| No, predefinito: `80`|Valore delle dimensioni dell'immagine piccola|1.0
|**medium**|`integer`| No, predefinito: `120`|Valore di dimensione media dell'immagine|1.0
|**large**|`integer`| No, predefinito: `180`|Valore delle dimensioni immagine di grandi dimensioni|1.0


<a name="schema-mediaconfig"></a>
## <a name="mediaconfig"></a>MediaConfig

Consente di controllare la visualizzazione e il comportamento di `Media` elementi

#### <a name="introduced-in-version-11"></a>Introdotta nella versione 1.1

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**defaultPoster**|`string`| No|URI immagine da visualizzare quando il pulsante di riproduzione non è stato richiamato.|1.1
|**playButton**|`string`| No|Immagine da visualizzare come pulsante Riproduci|1.1
|**allowInlinePlayback**|`boolean`| No, predefinito: `true`|Se si desidera visualizzare supporti inline o richiamare esternamente|1.1


<a name="schema-separatorconfig"></a>
## <a name="separatorconfig"></a>SeparatorConfig

Controlla la modalità di visualizzazione separatore

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**lineThickness**|`integer`| No, predefinito: `1`|Spessore della linea di separazione|1.0
|**lineColor**|`string,null`| No, predefinito: `#B2000000`|Colore da utilizzare quando si disegna una linea di separazione|1.0


<a name="schema-showcardconfig"></a>
## <a name="showcardconfig"></a>ShowCardConfig

Comportamento di controlli e stili di `Action.ShowCard`

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**actionMode**|`string`| No, predefinito: `"inline"`|Determina come appare la scheda|1.0
|**style**|`object`| No, predefinito: `emphasis`|Stile di controlli di un contenitore|1.0
|**inlineTopMargin**|`integer`| No, predefinito: `16`|Quantità di margine da utilizzare durante la visualizzazione scheda|1.0


<a name="schema-spacingsconfig"></a>
## <a name="spacingsconfig"></a>SpacingsConfig

Controlla la modalità layout di elementi

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**small**|`integer`| No, predefinito: `3`|Valore di spaziatura Small|1.0
|**impostazione predefinita**|`integer`| No, predefinito: `8`|Valore di spaziatura predefinito|1.0
|**medium**|`integer`| No, predefinito: `20`|Valore di spaziatura medio|1.0
|**large**|`integer`| No, predefinito: `30`|Valore di spaziatura di grandi dimensioni|1.0
|**extraLarge**|`integer`| No, predefinito: `40`|Valore di spaziatura molto grande|1.0
|**padding**|`integer`| No, predefinito: `20`|Valore di spaziatura interna|1.0


<a name="schema-textblockconfig"></a>
## <a name="textblockconfig"></a>TextBlockConfig

Parametri di controllo della visualizzazione di testo

|Proprietà|Tipo|Obbligatorio|Descrizione|Versione|
|--------|----|--------|-----------|-------|
|**size**|`string`| No, predefinito: `"default"`|Dimensioni del carattere da utilizzare quando una scheda non sia specificata|1.0
|**weight**|`string`| No, predefinito: `"normal"`|Spessore del carattere da utilizzare quando una scheda non sia specificata|1.0
|**color**|`string`| No, predefinito: `"default"`|Colore del carattere da utilizzare quando una scheda non sia specificata|1.0
|**isSubtle**|`boolean`| No, predefinito: `false`|Il testo deve essere meno evidenti se non specifica una scheda|1.0
|**wrap**|`boolean`| No, predefinito: `true`|Dovrebbe testo a capo se non specifica una scheda|1.0
|**maxWidth**|`integer`| No, predefinito: `0`|Larghezza massima da utilizzare se non specifica una scheda|1.0
