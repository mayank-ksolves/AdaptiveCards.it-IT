---
title: Classe AdaptiveCard-Novell. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: 0f64bf635023271d8b40bf55fce079300aae7652
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146085"
---
# <a name="adaptivecard"></a>AdaptiveCard

```csharp
public class AdaptiveCard : Java.Lang.Object 
```

**Namespace**

```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.ObjectModel
```

## <a name="summary"></a>Riepilogo

| Attributi | |
| ---- | --- |
| Azioni | Azioni da visualizzare nella barra delle azioni della scheda. |
| BackgroundImage | Specifica l'immagine di sfondo della scheda. |
| Corpo | Elementi della scheda da visualizzare nell'area della scheda primaria. |
| ElementType | Deve essere "AdaptiveCard". |
| FallbackText | Testo visualizzato quando il client non supporta la versione specificata (può contenere Markdown). |
| Altezza | |
| InputNecessityIndicators | |
| Lingua | Lingua ISO-639-1 di 2 lettere utilizzata nella scheda. Utilizzato per localizzare le funzioni di data/ora. |
| Altezza minima | Specifica l'altezza minima della scheda. |
| SelectAction | Azione che verrà richiamata quando la scheda viene toccata o selezionata. Action. ShowCard non è supportato. |
| Speak | Specifica l'elemento da pronunciare per l'intera scheda. Si tratta di un frammento di testo semplice o SSML. |
| Stile | |
| Version | Versione dello schema richiesta da questa scheda. Se un client è inferiore a questa versione, verrà eseguito il rendering di fallbackText. Nota: la versione non è necessaria per le schede all'interno di un'azione. ShowCard. Tuttavia, è obbligatorio per la scheda di livello superiore. |
| VerticalContentAlignment | Definisce il modo in cui il contenuto deve essere allineato verticalmente all'interno del contenitore. Pertinente solo per schede a altezza fissa o schede con minHeight specificato. |

&nbsp;

**Costruttori pubblici**

---

<a href="#ctor0"><div>
```csharp
AdaptiveCard(string version, string fallbackText, BackgroundImage backgroundImage, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight)
```
</div></a>

<a href="#ctor1"><div>
```csharp
AdaptiveCard(string version, string fallbackText, BackgroundImage backgroundImage, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight, BaseCardElementVector body, BaseActionElementVector actions)
```
</div></a>

<a href="#ctor2"><div>
```csharp
AdaptiveCard(string version, string fallbackText, string backgroundImageUrl, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight)
```
</div></a>

<a href="#ctor3"><div>
```csharp
AdaptiveCard(string version, string fallbackText, string backgroundImageUrl, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight, BaseCardElementVector body, BaseActionElementVector actions)
```
</div></a>

&nbsp;
| Metodi pubblici | |
| --- | ---- |
| ```static ParseResult``` | [```DeserializeFromString(string jsonString, string rendererVersion)```](#deserializefromstring0) |
| ```static ParseResult``` | [```DeserializeFromString(string jsonString, string rendererVersion, ParseContext context)```](#deserializefromstring1) |
| ```static AdaptiveCard``` | [```MakeFallbackTextCard(string fallbackText, string language, string speak)```](#makefallbacktextcard) |
| ```string``` | [```Serialize()```](#serialize) |
| ```JsonValue``` | [```SerializeToJsonValue()```](#serializetojsonvalue) |

&nbsp;
## <a name="public-constructors"></a>Costruttori pubblici
---

### <a id="ctor0"></a>AdaptiveCard
<p style='text-align:right'>Aggiunto nella versione 0,1</p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    BackgroundImage backgroundImage, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment, 
                    HeightType height, 
                    long minHeight) 
```

| Parametri | |
| --- | --- |
| Versione di | ```string``` |
| fallbackText | ```string``` |
| backgroundImage | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BackgroundImage``` |
| stile | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| speak | ```string``` |
| language | ```string``` |
| verticalContentAlignment | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| height | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| minHeight | ```long``` |

&nbsp;&nbsp;

### <a id="ctor1"></a>AdaptiveCard
<p style='text-align:right'>Aggiunto nella versione 0,1</p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    BackgroundImage backgroundImage, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment, 
                    HeightType height, 
                    long minHeight, 
                    BaseCardElementVector body, 
                    BaseActionElementVector actions)
```

| Parametri | |
| --- | --- |
| Versione di | ```string``` |
| fallbackText | ```string``` |
| backgroundImage | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BackgroundImage``` |
| stile | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| speak | ```string``` |
| language | ```string``` |
| verticalContentAlignment | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| height | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| minHeight | ```long``` |
| body | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElementVector``` |
| azioni | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElementVector``` |

&nbsp;&nbsp;

### <a id="ctor2"></a>AdaptiveCard
<p style='text-align:right'>Aggiunto nella versione 0,1</p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    string backgroundImageUrl, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment,
                    HeightType height, 
                    long minHeight) 
```

| Parametri | |
| --- | --- |
| Versione di | ```string``` |
| fallbackText | ```string``` |
| backgroundImage | ```string``` |
| stile | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| speak | ```string``` |
| language | ```string``` |
| verticalContentAlignment | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| height | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| minHeight | ```long``` |

&nbsp;&nbsp;

### <a id="ctor3"></a>AdaptiveCard
<p style='text-align:right'>Aggiunto nella versione 0,1</p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    string backgroundImageUrl, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment,
                    HeightType height, 
                    long minHeight, 
                    BaseCardElementVector body,
                    BaseActionElementVector actions)

```

| Parametri | |
| --- | --- |
| Versione di | ```string``` |
| fallbackText | ```string``` |
| backgroundImage | ```string``` |
| stile | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| speak | ```string``` |
| language | ```string``` |
| verticalContentAlignment | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| height | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| minHeight | ```long``` |
| body | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElementVector``` |
| azioni | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElementVector``` |

&nbsp;

## <a name="public-methods"></a>Metodi pubblici
---
### <a id="deserializefromstring0"></a>DeserializeFromString
<p style='text-align:right'>Aggiunto nella versione 0.1.0</p>

```csharp
public static ParseResult DeserializeFromString (string jsonString, string rendererVersion)
```

Deserializza la scheda adattiva specificata come stringa JSON per la versione del renderer specificata.

| Parametri | |
| --- | --- |
| jsonString | ```string``` |
| rendererVersion | ```string``` |

| Returns | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseResult``` | |

#### <a name="sample"></a>Esempio

```csharp
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
```

--- 
### <a id="deserializefromstring1"></a>DeserializeFromString
<p style='text-align:right'>Aggiunto nella versione 0.1.0</p>

```csharp
public static ParseResult DeserializeFromString(string jsonString, string rendererVersion, ParseContext context)
```

Deserializza la scheda adattiva specificata come stringa JSON per la versione del renderer specificata usando un oggetto [ParseContext]() per gestire l'analisi degli elementi personalizzata.

| Parametri | |
| --- | --- |
| jsonString | ```string``` |
| rendererVersion | ```string``` |
| context | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseContext``` |

| Returns | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseResult``` | |

#### <a name="sample"></a>Esempio

```csharp
ParseContext parseContext = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version, parseContext);
```

---

### <a id="makefallbacktextcard"></a>MakeFallbackTextCard
<p style='text-align:right'>Aggiunto nella versione 0.1.0</p>

```csharp
public static AdaptiveCard MakeFallbackTextCard (string fallbackText, string language, string speak)
```

Deserializza la scheda adattiva specificata come stringa JSON per la versione del renderer specificata.

| Parametri | |
| --- | --- |
| fallbackText | ```string``` |
| language | ```string``` |
| speak | ```string``` |

| Returns | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard``` | Scheda adattiva che contiene il testo di fallback per una scheda unrendereable |

#### <a name="sample"></a>Esempio

```csharp
AdaptiveCard adaptiveCard = AdaptiveCard.MakeFallbackTextCard("This card failed to render", "es", "Unrendereable card");
```

---

### <a id="serialize"></a>Serializzare
<p style='text-align:right'>Aggiunto nella versione 0.1.0</p>

```csharp
public string Serialize ()
```

Serializza la scheda adattiva nel formato stringa JSON.

| Returns | |
| --- | --- |
| ```string``` | Scheda adattiva come stringa JSON |

#### <a name="sample"></a>Esempio

```csharp
string jsonString = parseResult.AdaptiveCard.Serialize();
```

---

### <a id="serializetojsonvalue"></a>SerializeToJsonValue
<p style='text-align:right'>Aggiunto nella versione 0.1.0</p>

```csharp
public JsonValue SerializeToJsonValue ()
```

Serializza la scheda adattiva in un oggetto valore JSON.

| Returns | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.JsonValue``` | |

#### <a name="sample"></a>Esempio

```csharp
JsonValue value = parseResult.AdaptiveCard.SerializeToJsonValue();
```