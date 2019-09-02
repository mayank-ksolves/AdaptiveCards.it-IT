---
title: Motivazioni e principi
author: matthidinger
ms.author: mahiding
ms.date: 5/14/2018
ms.topic: article
ms.openlocfilehash: 78fe44463c4ddb832ba0cc72d456b6d21518bac4
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553153"
---
# <a name="motivations-and-principles"></a>Motivazioni e principi

Di seguito sono riportati i principi e le motivazioni alla base dell'evoluzione del formato Scheda adattiva.

## <a name="motivations-behind-the-format"></a>Motivazioni alla base del formato

All'inizio del 2016 diversi team Microsoft (tra cui Outlook, Windows e Bot Framework) si sono resi conto che volevano tutti qualcosa di molto simile ("schede") e che ognuno stava progettando soluzioni personalizzate in modo indipendente:

- Windows aveva il proprio formato dei riquadri animati e delle notifiche
-  Bot Framework stava usando un set di modelli di scheda predefiniti che gli sviluppatori potevano scegliere per inviare messaggi bot
- Outlook stava usando il proprio formato MessageCard per la funzionalità dei messaggi interattivi

Allo stesso tempo, altre piattaforme come LINE, FaceBook Messenger, Slack e così via stavano definendo il proprio formato di "scheda" proprietario. Alcuni dipendenti Microsoft si sono quindi riuniti e hanno iniziato a cercare una soluzione per definire un singolo formato di scheda aperto e un set di SDK in grado di soddisfare i requisiti seguenti:

- Facilitare l'interscambio di schede tra host
- Consentire a ogni host di mantenere il controllo dello stile delle schede per garantire la coerenza visiva
- Consentire a un'applicazione host di visualizzare facilmente le schede tramite SDK pronti per l'uso
- Fornire infine valore a terze parti e poter essere adottati su larga scala nell'ambito del settore

## <a name="principles-governing-adaptive-cards"></a>Principi alla base delle schede adattive

1.  **Scheda adattiva è un formato di scheda _semplice_ e _dichiarativo_**

    1.  Non è concepito come sostituzione/alternativa del formato HTML o XAML
    2.  Non esiste **alcun "code-behind** " con le schede adattive
        1. Gli autori delle schede non possono incorporare codice personalizzato/arbitrario con i payload e, di conseguenza, un host di schede adattive non ha mai la necessità di eseguire codice di terze parti
        2. Dinamismo e interattività vengono realizzati esclusivamente tramite markup dichiarativo
    3.  In questo modo si evita un lavoro eccessivo per creare un SDK per schede adattive per una nuova piattaforma

2.  **Il formato Scheda adattiva non può imporre l'uso di una particolare tecnologia sottostante**

    1.  Il formato Scheda adattiva non si basa su JavaScript, C#, Python o un altro linguaggio
    2.  Analogamente, non si basa su HTML o XAML o altri framework grafici o di interfaccia utente
    3.  È quindi possibile eseguire il rendering delle schede adattive in modo nativo su qualsiasi piattaforma purché esista un renderer

3.  **Il formato Scheda adattiva è una _proprietà condivisa_**

    1.  Insieme agli SDK corrispondenti, il formato deve essere open source e la sua evoluzione deve essere basata sulla community
    2.  Il formato non è quindi né di proprietà né gestito da un team specifico

4.  **Il formato Scheda adattiva non è progettato "solo per l'uso da parte di Microsoft"**

    1.  È progettato invece per soddisfare le esigenze di un'ampia gamma di applicazioni e casi d'uso

5.  **Il _gruppo di lavoro delle schede adattive_ disciplina l'evoluzione del formato**

    1.  Questo gruppo di lavoro è costituito da un gruppo di dipendenti Microsoft profondamente interessati al successo del formato
    2.  Questo gruppo effettua riunioni settimanali (attualmente il lunedì) durante le quali vengono esaminate le proposte di funzionalità, vengono discussi e classificati i problemi aperti e viene tenuta traccia dello stato di avanzamento generale degli elementi di lavoro vNext
    3.  Il gruppo di lavoro usa il feedback dell'intera community, inclusi i team Microsoft interni, per decidere in che modo si evolve il formato
        1. Chiunque può partecipare al gruppo di lavoro tramite l'apertura di problemi in GitHub (vedi più avanti)
        2. I problemi e le richieste di funzionalità basati sull'uso effettivo del framework delle schede adattive (sia come host che come autore di schede) hanno maggiore impatto sul futuro del formato
    4.  Per essere approvate dal gruppo di lavoro, le nuove funzionalità proposte devono avere le caratteristiche seguenti:
        1. Essere giustificate da casi d'uso reali
        2. Avere una specifica funzionale
    5.  Le nuove funzionalità approvate vengono aggiunte al backlog e prese in considerazione per vNext
        1. I criteri usati per definire la priorità delle nuove funzionalità includono la gamma di scenari abilitati dalla funzionalità, la complessità, la gestibilità e altro ancora
        2. In caso di dubbi, è meglio evitare. È molto più semplice aspettare e introdurre una funzionalità dopo che è stata progettata correttamente piuttosto che dover convivere per sempre con un errore
    6.  Tutte le nuove funzionalità vengono implementate in tutti gli SDK supportati
    7.  Tutte le nuove funzionalità sono documentate e associate a una scheda di test pubblicata nella cartella degli esempi
    8.  Le nuove versioni del formato e gli SDK passano attraverso una fase beta
    9.  La pianificazione del rilascio per lo schema delle schede adattive e le versioni degli SDK si basa sulla qualità e non sulla data

6.  **Interoperabilità**
    1.  Le schede create in conformità al formato documentato, ad esempio non usando alcuna estensione specifica dell'host, verranno sottoposte correttamente a rendering in qualsiasi host compatibile con le schede adattive
    2.  Le uniche eccezioni a questi principi sono le seguenti:
        1.  Alcuni host potrebbero non consentire l'interattività e pertanto non eseguiranno il rendering di input o di azioni
        2.  L'esecuzione delle azioni Action.Submit è a discrezione dell'host e non tutti gli host gestiranno necessariamente in modo corretto tutti i payload di Action.Submit. Inoltre, alcuni host potrebbero non supportare affatto Action.Submit

7.  **Il formato deve essere estendibile**

    1.  Gli host devono avere la libertà di aggiungere il supporto di elementi personalizzati o di azioni personalizzate che vanno oltre quanto previsto dal formato
    2.  Questo aspetto è particolarmente importante per le azioni, in quanto host diversi non supportano necessariamente lo stesso set di azioni
    3.  Queste aggiunte sono a discrezione dell'host
        1. Non sono aggiunte *di fatto* alla specifica della scheda adattiva
        2. Di conseguenza, creano un payload che le usa incompatibile con il formato Scheda adattiva disponibile per il pubblico
        3. Tuttavia, possono essere presentate al gruppo di lavoro e proposte come nuove funzionalità per una versione futura del formato, come descritto nel punto 5

8.  **Gli autori delle schede sono i proprietari del contenuto, le app host sono proprietarie dell'aspetto**

    1.  Le app host impongono il proprio stile, quindi le schede hanno un aspetto analogo alle estensioni native dell'esperienza dell'app
    2.  Gli autori di schede possono comunque specificare lo stile, ma solo tramite espressioni semantiche di colori, dimensioni e così via

9.  **Verranno forniti SDK per le piattaforme di sviluppo più diffuse**

    1.  Gli SDK semplificano il rendering dei payload delle schede adattive in qualsiasi host
    2.  In questo modo l'accesso è ugualmente facile sia per gli sviluppatori di terze parti che per i team Microsoft
