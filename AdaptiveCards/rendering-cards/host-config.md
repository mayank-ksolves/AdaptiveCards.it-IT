---
title: HostConfig per schede adattive
author: paulcam206
ms.author: paulcam
ms.date: 09/18/2018
ms.topic: reference
ms.openlocfilehash: d7fda209e6c470659d2fb2b66ac982e9c7183367
ms.sourcegitcommit: eb71aebe40a592649461e468a87993a10cbe6187
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/03/2020
ms.locfileid: "84318201"
---
# <a name="what-is-hostconfig"></a>Che cos'è HostConfig?
`HostConfig` è un **oggetto di configurazione tra piattaforme** che specifica il modo in cui un renderer di schede adattive genera l'interfaccia utente.

Ciò consente di condividere le proprietà indipendenti dalla piattaforma tra i renderer in piattaforme e dispositivi diversi. Consente inoltre di creare strumenti che danno un'idea dell'aspetto che avrebbe la scheda per un determinato ambiente.

Vedi un file [HostConfig.json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) di esempio per comprenderne a grandi linee il contenuto.

---

   * [`AdaptiveCardConfig`](#schema-adaptivecardconfig) - Opzioni di livello principale per `AdaptiveCards`
   * [`ActionsConfig`](#schema-actionsconfig) - Opzioni per elementi `Action`
   * [`ContainerStylesConfig`](#schema-containerstylesconfig) - Controlla l'applicazione dello stile per i contenitori predefiniti e di enfasi
   * [`FactSetConfig`](#schema-factsetconfig) - Controlla la visualizzazione degli elementi `FactSet`
   * [`FontSizesConfig`](#schema-fontsizesconfig) - Controlla la metrica relativa alle dimensioni del carattere per i diversi stili di testo
   * [`FontWeightsConfig`](#schema-fontweightsconfig) - Controlla la metrica relativa allo spessore del carattere
   * [`ForegroundColorsConfig`](#schema-foregroundcolorsconfig) - Controlla i vari colori del carattere
   * [`ImageSetConfig`](#schema-imagesetconfig) - Controlla la modalità di visualizzazione degli elementi `ImageSet`
   * [`ImageSizesConfig`](#schema-imagesizesconfig) - Controlla le dimensioni degli elementi `Image`
   * [`MediaConfig`](#schema-mediaconfig) - Controlla la visualizzazione e il comportamento degli elementi `Media`
   * [`SeparatorConfig`](#schema-separatorconfig) - Controlla la modalità di visualizzazione dei separatori
   * [`ShowCardConfig`](#schema-showcardconfig) - Controlla il comportamento e lo stile di `Action.ShowCard`
   * [`SpacingsConfig`](#schema-spacingsconfig) - Controlla la disposizione degli elementi
   * [`TextBlockConfig`](#schema-textblockconfig) - Parametri che controllano la visualizzazione del testo

## <a name="card-configuration"></a>Configurazione delle schede

<a name="schema-adaptivecardconfig"></a>
## <a name="adaptivecardconfig"></a>AdaptiveCardConfig

Opzioni di livello principale per `AdaptiveCards`

|Proprietà|Type|Obbligatoria|Description|Versione|
|--------|----|--------|-----------|-------|
|**allowCustomStyle**|`boolean`| No, impostazione predefinita: `true`|Controlla se è consentito lo stile personalizzato|1.0
|**supportsInteractivity**|`boolean`| No, impostazione predefinita: `true`|Controlla se è consentito richiamare gli elementi `Action` interattivi|1.0
|**imageBaseUrl**|`string`| No|URL di base da usare durante il caricamento delle risorse|1.0
|**fontFamily**|`string`| No, impostazione predefinita: `"Calibri"`|Tipo di carattere da usare per il rendering del testo|1.0
|**actions**|`object`| No|Opzioni per gli elementi `Action`|1.0
|**adaptiveCard**|`object`| No|Opzioni di livello principale per `AdaptiveCards`|1.0
|**containerStyles**|`object`| No|Controlla l'applicazione dello stile per i contenitori predefiniti e di enfasi|1.0
|**imageSizes**|`object`| No|Controlla le dimensioni degli elementi `Image`|1.0
|**imageSet**|`object`| No|Controlla la modalità di visualizzazione degli elementi `ImageSet`|1.0
|**factSet**|`object`| No|Controlla la visualizzazione degli elementi `FactSet`|1.0
|**fontSizes**|`object`| No|Controlla la metrica relativa alle dimensioni del carattere per i diversi stili di testo|1.0
|**fontWeights**|`object`| No|Controlla la metrica relativa allo spessore del carattere|1.0
|**spacing**|`object`| No|Controlla la disposizione degli elementi|1.0
|**separator**|`object`| No|Controlla la modalità di visualizzazione dei separatori|1.0
|**media**|`object`| No|Controlla la visualizzazione e il comportamento degli elementi `Media`|1.1


<a name="schema-actionsconfig"></a>
## <a name="actionsconfig"></a>ActionsConfig

Opzioni per gli elementi `Action`

|Proprietà|Type|Obbligatoria|Description|Versione|
|--------|----|--------|-----------|-------|
|**actionsOrientation**|`string`| No, impostazione predefinita: `"horizontal"`|Controlla la disposizione dei pulsanti|1.0
|**actionAlignment**|`string`| No, impostazione predefinita: `"stretch"`|Controlla il layout dei pulsanti|1.0
|**buttonSpacing**|`integer`| No, impostazione predefinita: `10`|Controlla la quantità di spaziatura da usare tra i pulsanti|1.0
|**maxActions**|`integer`| No, impostazione predefinita: `5`|Controlla il numero di azioni consentite in totale|1.0
|**spacing**|`string`| No, impostazione predefinita: `"default"`|Controlla la spaziatura complessiva dell'elemento action|1.0
|**showCard**|`object`| No|Controlla il comportamento e lo stile di `Action.ShowCard`|1.0
|**iconPlacement**|`string`| No, impostazione predefinita: `"aboveTitle"`|Controlla dove posizionare l'icona dell'azione|1.0
|**iconSize**|`integer`| No, impostazione predefinita: `30`|Controlla le dimensioni dell'icona dell'azione|1.0


<a name="schema-containerstylesconfig"></a>
## <a name="containerstylesconfig"></a>ContainerStylesConfig

Controlla l'applicazione dello stile per i contenitori predefiniti e di enfasi

|Proprietà|Type|Obbligatoria|Description|Versione|
|--------|----|--------|-----------|-------|
|**default**|`object`| No|Stile contenitore predefinito|1.0
|**emphasis**|`object`| No|Stile contenitore da usare per l'enfasi|1.0


<a name="schema-factsetconfig"></a>
## <a name="factsetconfig"></a>FactSetConfig

Controlla la visualizzazione degli elementi `FactSet`

|Proprietà|Type|Obbligatoria|Description|Versione|
|--------|----|--------|-----------|-------|
|**title**|`object`| No, impostazione predefinita: `{"weight":"bolder","size":"default","color":"default","isSubtle":false,"wrap":true,"maxWidth":150}`|Parametri che controllano la visualizzazione del testo|1.0
|**value**|`object`| No, impostazione predefinita: `{"weight":"default","size":"default","color":"default","isSubtle":false,"wrap":true,"maxWidth":0}`|Parametri che controllano la visualizzazione del testo|1.0
|**spacing**|`integer`| No, impostazione predefinita: `10`|&nbsp;|1.0


<a name="schema-fontsizesconfig"></a>
## <a name="fontsizesconfig"></a>FontSizesConfig

Controlla la metrica relativa alle dimensioni del carattere per i diversi stili di testo

|Proprietà|Type|Obbligatoria|Description|Versione|
|--------|----|--------|-----------|-------|
|**small**|`integer`| No, impostazione predefinita: `10`|Dimensione piccola dei caratteri|1.0
|**default**|`integer`| No, impostazione predefinita: `12`|Dimensione predefinita dei caratteri|1.0
|**medium**|`integer`| No, impostazione predefinita: `14`|Dimensione media dei caratteri|1.0
|**large**|`integer`| No, impostazione predefinita: `17`|Dimensione grande dei caratteri|1.0
|**extraLarge**|`integer`| No, impostazione predefinita: `20`|Dimensione molto grande dei caratteri|1.0


<a name="schema-fontweightsconfig"></a>
## <a name="fontweightsconfig"></a>FontWeightsConfig

Controlla la metrica relativa allo spessore del carattere

|Proprietà|Type|Obbligatoria|Description|Versione|
|--------|----|--------|-----------|-------|
|**lighter**|`integer`| No, impostazione predefinita: `200`|&nbsp;|1.0
|**default**|`integer`| No, impostazione predefinita: `400`|&nbsp;|1.0
|**bolder**|`integer`| No, impostazione predefinita: `800`|&nbsp;|1.0


<a name="schema-foregroundcolorsconfig"></a>
## <a name="foregroundcolorsconfig"></a>ForegroundColorsConfig

Controlla i vari colori del carattere

|Proprietà|Type|Obbligatoria|Description|Versione|
|--------|----|--------|-----------|-------|
|**default**|`object`| No, impostazione predefinita: `{"default":"#FF000000","subtle":"#B2000000"}`|&nbsp;|1.0
|**accent**|`object`| No, impostazione predefinita: `{"default":"#FF0000FF","subtle":"#B20000FF"}`|&nbsp;|1.0
|**dark**|`object`| No, impostazione predefinita: `{"default":"#FF101010","subtle":"#B2101010"}`|&nbsp;|1.0
|**light**|`object`| No, impostazione predefinita: `{"default":"#FFFFFFFF","subtle":"#B2FFFFFF"}`|&nbsp;|1.0
|**good**|`object`| No, impostazione predefinita: `{"default":"#FF008000","subtle":"#B2008000"}`|&nbsp;|1.0
|**warning**|`object`| No, impostazione predefinita: `{"default":"#FFFFD700","subtle":"#B2FFD700"}`|&nbsp;|1.0
|**attention**|`object`| No, impostazione predefinita: `{"default":"#FF8B0000","subtle":"#B28B0000"}`|&nbsp;|1.0


<a name="schema-imagesetconfig"></a>
## <a name="imagesetconfig"></a>ImageSetConfig

Controlla la modalità di visualizzazione degli elementi `ImageSet`

|Proprietà|Type|Obbligatoria|Description|Versione|
|--------|----|--------|-----------|-------|
|**imageSize**|`string`| No, impostazione predefinita: `"auto"`|Controlla le dimensioni delle singole immagini|1.0
|**maxImageHeight**|`integer`| No, impostazione predefinita: `100`|Vincola l'altezza dell'immagine a questo valore|1.0


<a name="schema-imagesizesconfig"></a>
## <a name="imagesizesconfig"></a>ImageSizesConfig

Controlla le dimensioni degli elementi `Image`

|Proprietà|Type|Obbligatoria|Description|Versione|
|--------|----|--------|-----------|-------|
|**small**|`integer`| No, impostazione predefinita: `80`|Valore relativo alle dimensioni immagine piccole|1.0
|**medium**|`integer`| No, impostazione predefinita: `120`|Valore relativo alle dimensioni immagine medie|1.0
|**large**|`integer`| No, impostazione predefinita: `180`|Valore relativo alle dimensioni immagine grandi|1.0


<a name="schema-mediaconfig"></a>
## <a name="mediaconfig"></a>MediaConfig

Controlla la visualizzazione e il comportamento degli elementi `Media`

#### <a name="introduced-in-version-11"></a>Introdotta nella versione 1.1

|Proprietà|Type|Obbligatoria|Description|Versione|
|--------|----|--------|-----------|-------|
|**defaultPoster**|`string`| No|URI dell'immagine da visualizzare quando il pulsante Riproduci non è stato richiamato|1.1
|**playButton**|`string`| No|Immagine da visualizzare come pulsante Riproduci|1.1
|**allowInlinePlayback**|`boolean`| No, impostazione predefinita: `true`|Indica se visualizzare gli elementi multimediali inline o se richiamarli esternamente|1.1


<a name="schema-separatorconfig"></a>
## <a name="separatorconfig"></a>SeparatorConfig

Controlla la modalità di visualizzazione dei separatori

|Proprietà|Type|Obbligatoria|Description|Versione|
|--------|----|--------|-----------|-------|
|**lineThickness**|`integer`| No, impostazione predefinita: `1`|Spessore della linea di separazione|1.0
|**lineColor**|`string,null`| No, impostazione predefinita: `#B2000000`|Colore da usare per tracciare la linea di separazione|1.0


<a name="schema-showcardconfig"></a>
## <a name="showcardconfig"></a>ShowCardConfig

Controlla il comportamento e lo stile di `Action.ShowCard`

|Proprietà|Type|Obbligatoria|Description|Versione|
|--------|----|--------|-----------|-------|
|**actionMode**|`string`| No, impostazione predefinita: `"inline"`|Controlla la modalità di visualizzazione della scheda|1.0
|**style**|`object`| No, impostazione predefinita: `emphasis`|Controlla lo stile di un contenitore|1.0
|**inlineTopMargin**|`integer`| No, impostazione predefinita: `16`|Quantità di margine da usare per la visualizzazione della scheda|1.0


<a name="schema-spacingsconfig"></a>
## <a name="spacingsconfig"></a>SpacingsConfig

Controlla la disposizione degli elementi

|Proprietà|Type|Obbligatoria|Description|Versione|
|--------|----|--------|-----------|-------|
|**small**|`integer`| No, impostazione predefinita: `3`|Valore relativo alla spaziatura piccola|1.0
|**default**|`integer`| No, impostazione predefinita: `8`|Valore relativo alla spaziatura predefinita|1.0
|**medium**|`integer`| No, impostazione predefinita: `20`|Valore relativo alla spaziatura media|1.0
|**large**|`integer`| No, impostazione predefinita: `30`|Valore relativo alla spaziatura grande|1.0
|**extraLarge**|`integer`| No, impostazione predefinita: `40`|Valore relativo alla spaziatura molto grande|1.0
|**padding**|`integer`| No, impostazione predefinita: `20`|Valore relativo alla spaziatura interna|1.0


<a name="schema-textblockconfig"></a>
## <a name="textblockconfig"></a>TextBlockConfig

Parametri che controllano la visualizzazione del testo

|Proprietà|Type|Obbligatoria|Description|Versione|
|--------|----|--------|-----------|-------|
|**size**|`string`| No, impostazione predefinita: `"default"`|Dimensioni del carattere da usare quando non è presente la specifica di una scheda|1.0
|**weight**|`string`| No, impostazione predefinita: `"normal"`|Spessore del carattere da usare quando non è presente la specifica di una scheda|1.0
|**color**|`string`| No, impostazione predefinita: `"default"`|Colore del carattere da usare quando non è presente la specifica di una scheda|1.0
|**isSubtle**|`boolean`| No, impostazione predefinita: `false`|Indica se il testo deve essere impercettibile se non è presente la specifica di una scheda|1.0
|**wrap**|`boolean`| No, impostazione predefinita: `true`|Indica se il testo deve andare a capo se non è presente la specifica di una scheda|1.0
|**maxWidth**|`integer`| No, impostazione predefinita: `0`|Larghezza massima da usare se non è presente la specifica di una scheda|1.0
