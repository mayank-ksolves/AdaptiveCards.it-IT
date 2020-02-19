---
title: Azioni - .NET WPF SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: dfee76c5dc0a8caafcd693b47337c28f84e71a53
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454344"
---
# <a name="actions---net-wpf"></a><span data-ttu-id="0bb61-102">Azioni - WPF .NET</span><span class="sxs-lookup"><span data-stu-id="0bb61-102">Actions - .NET WPF</span></span>

<span data-ttu-id="0bb61-103">Verrà eseguito il rendering di eventuali `actions` all'interno della scheda come `Button` WPF, ma dipende dall'app gestire ciò che accade quando l'utente preme tali pulsanti.</span><span class="sxs-lookup"><span data-stu-id="0bb61-103">Any `actions` within the card will render as WPF `Button`s, but it's up to your app to handle what happens when a user presses them.</span></span> 

<span data-ttu-id="0bb61-104">A tale scopo, l'oggetto `RenderedAdaptiveCard` fornisce un evento `OnAction`.</span><span class="sxs-lookup"><span data-stu-id="0bb61-104">The `RenderedAdaptiveCard` object provides an `OnAction` event for this purpose.</span></span>

```csharp
// Event handler fires when a user clicks an action within the card
renderedCard.OnAction += MyActionHandler;

private void MyActionHandler(RenderedAdaptiveCard sender, AdaptiveActionEventArgs e)
{
    if (e.Action is AdaptiveOpenUrlAction openUrlAction)
    {
        Process.Start(openUrlAction.Url.AbsoluteUri);
    }
    else if (e.Action is AdaptiveShowCardAction showCardAction)
    {
        // Action.ShowCard can be rendered inline automatically
        // ... but if you want to handle show card as a "popup", you handle this event
        if (_myHostConfig.Actions.ShowCard.ActionMode == ShowCardActionMode.Popup)
        {
            var dialog = new ShowCardWindow(showCardAction.Title, showCardAction, Resources);
            dialog.Owner = this;
            dialog.ShowDialog();
        }
    }
    else if (e.Action is AdaptiveSubmitAction submitAction)
    {
        var inputs = sender.UserInputs.AsJson();
        inputs.Merge(submitAction.Data);
        MessageBox.Show(this, JsonConvert.SerializeObject(inputs, Formatting.Indented), "SubmitAction");
    }
}
```
