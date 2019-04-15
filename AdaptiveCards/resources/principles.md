---
title: Motivazioni e principi
author: matthidinger
ms.author: mahiding
ms.date: 5/14/2018
ms.topic: article
ms.openlocfilehash: 78fe44463c4ddb832ba0cc72d456b6d21518bac4
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553153"
---
# <a name="motivations-and-principles"></a>Motivazioni e principi

Di seguito sono le motivazioni e principi govering l'evoluzione del formato scheda adattiva.

## <a name="motivations-behind-the-format"></a>Motivazioni dietro il formato

Nel 2016, i diversi team Microsoft (tra cui Outlook, Windows e Bot Framework) fornita per la realizzazione che tutti desiderano qualcosa di molto simile ("schede") e che ognuno di essi sono stati progettare in modo indipendente le proprie soluzioni:

- Windows ha un proprio formato i riquadri animati e notifiche
-  Bot framework usava un set di modelli di scheda predefinita gli sviluppatori poteva scegliere tra l'invio di messaggi di Bot
- Outlook usava MessageCard un formato specifico per la funzionalità di messaggi interattivi

Allo stesso tempo, altre piattaforme, ad esempio riga, FaceBook Messenger, Slack e altro ancora definisca i propri, formato proprietarie "card". In modo che alcuni dipendenti Microsoft raccolti e avviato consente di definire un formato di carta singolo, aprire e un set di SDK che:

- A facilitare lo scambio di schede tra gli host
- Consentirebbe ogni host per mantenere il controllo lo stile delle schede per garantire la coerenza visual
- Sarebbe rendono più semplice per un'applicazione host visualizzare le schede con uno sforzo minimo tramite gli SDK pronti da usare
- E che potrebbero anche fornire un valore a terze parti e infine ottenere adottate ampiamente nel settore

## <a name="principles-governing-adaptive-cards"></a>Principi che regolano le schede adattive

1.  **Scheda adattiva è un _semplice_ e _dichiarativa_ formato carta**

    1.  Non è destinato sostituzione/alternativa HTML o XAML
    2.  È presente **alcun "code-behind"** con le schede adattive
        1. Gli autori di smart card non è possibile incorporare codice personalizzato o arbitrario con il payload e di conseguenza un host di Smart Card adattivo non deve mai eseguire il codice di terze parti
        2. Dinamismo e la relativa interattività vengono ottenuti esclusivamente tramite markup dichiarativo
    3.  Ciò garantisce che lo sforzo necessario per compilare un SDK di scheda adattiva per una nuova piattaforma rimanga ragionevole

2.  **Il formato carta adattivo non è possibile imporre l'uso di qualsiasi particolare tecnologia sottostante**

    1.  Il formato carta adattivo non si basa su JavaScript, C#, Python o qualsiasi altro linguaggio
    2.  Analogamente non si basa su HTML o XAML o qualsiasi altro framework di grafica o dell'interfaccia utente
    3.  In questo modo, le schede adattive possibile eseguire il rendering in modo nativo su qualsiasi piattaforma per, purché esista un renderer

3.  **Il formato scheda adattiva è un _condivisi di proprietà_**

    1.  Insieme agli altri relativo SDK, il formato deve essere gestito dalla community relativo evoluzione e open source
    2.  Il formato è pertanto non di proprietà né dovuto a un qualsiasi team

4.  **Il formato carta adattivo non è progettato "solo per l'utilizzo di Microsoft"**

    1.  Invece è progettato per soddisfare le esigenze di un'ampia gamma di applicazioni e casi d'uso

5.  **Il _gruppo di lavoro della scheda adattiva_ governa l'evoluzione del formato**

    1.  Questo gruppo di lavoro è costituito da un set di dipendenti Microsoft che sono tutti profondamente coinvolti nel successo del formato
    2.  Il gruppo di lavoro eseguito riunioni settimanali (attualmente lunedì) durante il quale funzionalità proposte vengono esaminati, Apri problemi sono illustrate e valutate e tiene traccia della stato di avanzamento generale sugli elementi di lavoro vNext
    3.  Il gruppo di lavoro Usa commenti e suggerimenti della community in generale, incluso team interni Microsoft, per decidere come si evolve il formato
        1. Chiunque può far parte del gruppo di lavoro tramite l'apertura di problemi in GitHub (vedere sotto)
        2. Le richieste di problemi o funzionalità dovute all'utilizzo effettivo di framework le schede adattive (come host o quando si crea una smart card) detengono il maggior impatto sul futuro di formato
    4.  Per essere approvata dal gruppo di lavoro, proposta nuove funzionalità:
        1. Deve essere giustificata da casi d'uso di uno scenario reale
        2. Deve avere una specifica funzionale
    5.  Nuova funzionalità approvati sono aggiunti al backlog e considerata vNext
        1. I criteri usati per classificare le nuove funzionalità includono la varietà di scenari abilita la funzionalità, la complessità/manutenibilità e altro ancora
        2. In caso di dubbi, mantenerla! È molto più semplice per introdurre una funzionalità progettata correttamente in un secondo momento rispetto alla durata con un errore infinita.
    6.  Tutte le nuove funzionalità vengono implementate in tutti gli SDK supportati
    7.  Tutte le nuove funzionalità sono documentate e associata a una scheda test pubblicata nella cartella degli esempi
    8.  Le nuove versioni degli SDK e il formato attraversano una fase beta
    9.  La pianificazione del rilascio per lo schema di scheda adattiva e versioni precedenti del SDK si basa sulle qualità, non Data

6.  **Interoperabilità**
    1.  Verranno eseguito il rendering correttamente tutti gli host adattivo Smart Card in grado di supportare le schede create in conformità con il formato documentato (ad esempio, non tramite le estensioni specifiche degli host)
    2.  Le uniche eccezioni a questa entità sono:
        1.  Alcuni host potrebbero non consentire interattività e pertanto non eseguirà il rendering input né azioni
        2.  Esecuzione di azioni Action.Submit è a discrezione dell'host e non tutti gli host gestirà necessariamente correttamente tutti i payload Action.Submit. Inoltre, alcuni host potrebbero non supportare Action.Submit affatto

7.  **Il formato deve essere estendibile**

    1.  Gli host devono avere la libertà di aggiunta del supporto per gli elementi personalizzati o azioni personalizzate che vanno oltre ciò che è in grado di utilizzare il formato
    2.  Ciò è particolarmente importante per le azioni, come vari host non supportano necessariamente lo stesso set di azioni
    3.  Queste aggiunte sono a discrezione dell'host
        1. Non sono un *de facto* aggiunta alla specifica scheda adattiva
        2. Di conseguenza, effettuano un payload che li utilizza non compatibile con il formato scheda adattiva "Mainstream"
        3. Possono tuttavia essere presentata al gruppo di lavoro e proposti come le nuove funzionalità per una versione futura del formato, come descritto al punto 5 #

8.  **Gli autori di smart card proprietario del contenuto, l'aspetto di proprietari hosting delle App**

    1.  Hosting di App di imporre loro lo stile, per cui analizzare le schede e sembra sono estensioni native dell'esperienza dell'app
    2.  Gli autori di smart card possono comunque specificare lo stile, ma solo tramite espressioni di semantiche di colori, dimensioni e così via.

9.  **Gli SDK verranno forniti per le piattaforme di sviluppo più diffuse**

    1.  Gli SDK rendono più semplice eseguire il rendering di payload scheda adattiva in qualsiasi host
    2.  In questo modo la barriera all'ingresso di soli come può essere sia per gli sviluppatori di terze parti e Microsoft teams
