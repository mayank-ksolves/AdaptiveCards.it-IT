---
title: Convalida dell'input
author: rebeccaanne
ms.author: rebecch
ms.date: 07/24/2020
ms.topic: article
ms.openlocfilehash: 4c8aa73a218946944b25557eae141e231e8a6ac5
ms.sourcegitcommit: 2a394b75439b382d7bc3134078ecff02429617b8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2020
ms.locfileid: "87544963"
---
# <a name="input-validation"></a><span data-ttu-id="9f31f-102">Convalida dell'input</span><span class="sxs-lookup"><span data-stu-id="9f31f-102">Input Validation</span></span>

<span data-ttu-id="9f31f-103">Nelle versioni 1.3 e successive dello schema, AdaptiveCards supporta la convalida dell'input lato client per i tipi di input.</span><span class="sxs-lookup"><span data-stu-id="9f31f-103">In versions 1.3 and later of the schema, AdaptiveCards supports client side input validation of Input types.</span></span>

### <a name="validation-properties"></a><span data-ttu-id="9f31f-104">Proprietà di convalida</span><span class="sxs-lookup"><span data-stu-id="9f31f-104">Validation Properties</span></span>

<span data-ttu-id="9f31f-105">Per la convalida in AdaptiveCards sono supportate le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="9f31f-105">The following properties are supported for validation in AdaptiveCards:</span></span>

| <span data-ttu-id="9f31f-106">Input</span><span class="sxs-lookup"><span data-stu-id="9f31f-106">Input</span></span> | <span data-ttu-id="9f31f-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="9f31f-107">Properties</span></span> |
| --- | --- | 
| `Input.ChoiceSet` | `isRequired` | 
| `Input.Date` | `isRequired` <br> `min`<br> `max` | 
| `Input.Number` | `isRequired` <br> `min`<br> `max` |
| `Input.Text` | `isRequired` <br> `regex` <br> `maxLength` |
| `Input.Time` | `isRequired` <br> `min`<br> `max` | 
| `Input.Toggle` | `isRequired` | 

<span data-ttu-id="9f31f-108">Per tutti i tipi di input è disponibile una proprietà `errorMessage` per specificare l'errore che deve essere visualizzato se l'utente immette un valore non valido.</span><span class="sxs-lookup"><span data-stu-id="9f31f-108">An `errorMessage` property is available on all input types to specify what error a user should be shown if they enter an invalid value.</span></span> 

> [!NOTE]
>
> <span data-ttu-id="9f31f-109">In alcune piattaforme le proprietà min e max (inclusa maxLength) possono essere applicate direttamente dal controllo.</span><span class="sxs-lookup"><span data-stu-id="9f31f-109">Min and max properties (including maxLength) on some platforms may be enforced directly by the control.</span></span> <span data-ttu-id="9f31f-110">È ad esempio possibile applicare una proprietà min per Input.Date impedendo agli utenti di selezionare una data prima del limite minimo in un controllo di selezione data.</span><span class="sxs-lookup"><span data-stu-id="9f31f-110">For example, a min property on Input.Date may be enforced by not allowing users to select a date before the minimum in a date picker.</span></span> <span data-ttu-id="9f31f-111">In tal caso, è possibile che il messaggio di errore non venga visualizzato.</span><span class="sxs-lookup"><span data-stu-id="9f31f-111">In that case, the error message may not be shown.</span></span>

## <a name="fields-to-be-validated-and-submitted"></a><span data-ttu-id="9f31f-112">Campi da convalidare e inviare</span><span class="sxs-lookup"><span data-stu-id="9f31f-112">Fields to be validated and submitted</span></span>

<span data-ttu-id="9f31f-113">Gli input vengono convalidati quando l'utente fa clic su un'azione Action.Submit nella scheda.</span><span class="sxs-lookup"><span data-stu-id="9f31f-113">Inputs will be validated when the user clicks on an Action.Submit action in the card.</span></span> <span data-ttu-id="9f31f-114">Gli input che vengono convalidati e inviati per una determinata azione Action.Submit sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="9f31f-114">Those inputs which will be validated and submitted for a given Action.Submit action are:</span></span>

 - <span data-ttu-id="9f31f-115">Input nella stessa scheda dell'azione Action.Submit</span><span class="sxs-lookup"><span data-stu-id="9f31f-115">Inputs on the same card as the Action.Submit</span></span>
 - <span data-ttu-id="9f31f-116">Input in una qualsiasi scheda padre della scheda contenente l'azione Action.Submit, nel caso di una scheda associata a un'azione Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="9f31f-116">Inputs on any parent cards of the card containing the Action.Submit in the case of a card under an Action.ShowCard</span></span>

<span data-ttu-id="9f31f-117">Se gli input superano la convalida, i valori nei rispettivi campi verranno restituiti al client.</span><span class="sxs-lookup"><span data-stu-id="9f31f-117">If those inputs pass validation, the values in their fields will be passed back to the client.</span></span> <span data-ttu-id="9f31f-118">Se invece non superano la convalida, verranno visualizzati i messaggi di errore relativi agli input non validi e l'invio non verrà eseguito.</span><span class="sxs-lookup"><span data-stu-id="9f31f-118">If they do not pass validation, the error messages for the invalid inputs will be shown, and the submit will not be sent.</span></span>

> [!NOTE]
>
> <span data-ttu-id="9f31f-119">Gli input **non** vengono convalidati o inviati se si trovano in una scheda figlio o in una scheda di pari livello di quella contenente l'azione Action.Submit.</span><span class="sxs-lookup"><span data-stu-id="9f31f-119">Inputs will **not** be validated or submitted if they are on a card that is a child or sibling card of the card containing the Action.Submit.</span></span> <span data-ttu-id="9f31f-120">Sono incluse le schede risultanti da Action.ShowCards in ActionSets nel corpo di tale scheda.</span><span class="sxs-lookup"><span data-stu-id="9f31f-120">This includes cards from Action.ShowCards in ActionSets in the body of that card.</span></span> <span data-ttu-id="9f31f-121">Questo comportamento è diverso da quello delle versioni del renderer precedenti la 2.0 e si applica alle schede di tutte le versioni dello schema, indipendentemente dal fatto che vengano utilizzate le proprietà di convalida dell'input.</span><span class="sxs-lookup"><span data-stu-id="9f31f-121">This is a change in behavior from renderer versions prior to 2.0, and applies to cards of all schema versions, regardless of whether input validation properties are used.</span></span> 

## <a name="other-considerations-and-known-issues"></a><span data-ttu-id="9f31f-122">Altre considerazioni e problemi noti</span><span class="sxs-lookup"><span data-stu-id="9f31f-122">Other Considerations and Known Issues</span></span>

 - <span data-ttu-id="9f31f-123">Non è consigliabile creare input con proprietà di convalida che potrebbero non essere sempre visibili a causa dell'interazione con Action.ToggleVisibility.</span><span class="sxs-lookup"><span data-stu-id="9f31f-123">It is not recommended to create inputs with validation properties that may not always be visible due to interaction with Action.ToggleVisibility.</span></span> <span data-ttu-id="9f31f-124">I messaggi di errore e le indicazioni visive per la segnalazione di input non valido non verranno visualizzati se l'input non è al momento visibile, il che può generare confusione riguardo al motivo per cui l'invio è bloccato.</span><span class="sxs-lookup"><span data-stu-id="9f31f-124">Error messages and visual indications that the input is invalid will not be shown if the input is not currently visible, which may cause confusion for users as to why their submit is blocked.</span></span>

 - <span data-ttu-id="9f31f-125">Il comportamento della convalida dell'input per gli host che usano schede con visualizzazione popup tramite il valore `"actions":"showCard":"actionMode":"popup"` nella configurazione host non è ben definito.</span><span class="sxs-lookup"><span data-stu-id="9f31f-125">Behavior of input validation for hosts using popup show cards using the  `"actions":"showCard":"actionMode":"popup"` value in their host config is not well defined.</span></span> <span data-ttu-id="9f31f-126">Le schede con visualizzazione popup potrebbero essere deprecate in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="9f31f-126">Popup show cards may be deprecated in a future release.</span></span>

