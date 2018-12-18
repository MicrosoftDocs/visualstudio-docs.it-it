---
title: Refactoring del codice in Visual Studio per Mac | Microsoft Docs
description: "La riorganizzazione del codice in Visual Studio per Mac è stata semplificata grazie all'analisi dell'origine."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.openlocfilehash: ba92cd9a0e9ca28d132116f65fd41758bce1a1f0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="refactoring"></a>Refactoring

Il refactoring del codice è un modo per riorganizzare, ristrutturare e rendere più chiaro il codice esistente garantendo che il comportamento complessivo del codice non cambi.

Questa operazione produce una codebase più integra e quindi più facile da usare, leggere e gestire per qualsiasi sviluppatore o utente che fa riferimento al codice.

L'integrazione di Visual Studio per Mac con Roslyn, la piattaforma di compilazione .NET open source Microsoft, consente più operazioni di refactoring, oltre a offrire supporto completo per la versione di C# più recente.

## <a name="renaming"></a>Ridenominazione 

Il comando di refactoring *Rinomina* può essere usato su qualsiasi identificatore del codice (ad esempio un nome di classe, un nome di proprietà e così via) per trovare tutte le occorrenze di tale identificatore e modificarle. Per rinominare un simbolo, fare clic con il pulsante destro del mouse su di esso e scegliere **Refactoring > Rinomina** oppure usare il tasto di scelta rapida **Cmd+R**:

![Voce di menu Rinomina](media/refactoring-renaming1.png)

Verranno evidenziati il simbolo e tutti i relativi riferimenti. Quando si inizia a digitare un nuovo nome, verranno modificati automaticamente tutti i riferimenti nel codice. Per segnalare il completamento dell'operazione di ridenominazione, premere **INVIO**:

 ![Ridenominazione e identificatore](media/refactoring-renaming2.png)

## <a name="context-actions"></a>Azioni di contesto

Le azioni di contesto consentono di esaminare il codice C# e vedere tutte le possibili opzioni di refactoring. 

Le voci di contesto **Risolvi** e **Refactoring** sono combinate in una singola voce *Correzione rapida* che fornisce tutte le azioni di contesto disponibili:

![Visualizzare le voci di contesto](media/refactoring-context-action.png)

Passando il puntatore su una delle azioni di contesto, viene fornita un'anteprima di ciò che verrà aggiunto o rimosso dal codice.

In alternativa, è possibile premere **Opzione+INVIO** in qualsiasi punto nel codice:

![Voci di contesto visualizzate con Opzione+INVIO](media/refactoring-image2a.png)

Per abilitare queste opzioni, è necessario selezionare *Abilita l'analisi dell'origine dei file aperti* nelle opzioni **Visual Studio per Mac > Preferenze > Editor di testo > Analisi origine**:

 ![Abilitazione dell'analisi dell'origine](media/refactoring-options.png)

Ci sono più di 100 azioni che possono essere suggerite, che è possibile abilitare o disabilitare passando a **Visual Studio per Mac > Preferenze > Analisi origine > C# > Azioni codice** e selezionando o deselezionando la casella accanto all'azione:

 ![Azioni di analisi dell'origine C#](media/refactoring-image3a.png)

### <a name="common-context-actions"></a>Azioni di contesto comuni

Di seguito sono illustrate alcune delle azioni di contesto usate più comunemente.

#### <a name="extract-method"></a>Estrai metodo

L'operazione di refactoring Estrai metodo consente di creare un nuovo metodo estraendo una selezione di codice in un membro esistente. Questa azione esegue due operazioni:

* Crea un nuovo metodo contenente il codice selezionato
* Chiama il nuovo metodo nella posizione del codice selezionato.

##### <a name="example"></a>Esempio

1. Aggiungere il codice seguente:

```
    class MainClass
    {

        double CalculatePyramidVolume(double baseArea, double height)
        {

            double volume = (baseArea * height) / 3;

            return volume;
        }
    }
```

2. Evidenziare la riga `double volume = (baseArea * height) / 3;`, fare clic con il pulsante destro su di essa e scegliere **Refactoring > Estrai metodo**.

3. Usare i tasti di direzione per selezionare dove posizionare il nuovo metodo nel codice.


#### <a name="encapsulate-field"></a>Incapsula campo

L'operazione Incapsula campo consente di creare una proprietà da un campo esistente e aggiornare il codice per fare riferimento alla nuova proprietà creata. Creando una proprietà che incapsula il campo, si impedisce l'accesso diretto al campo pubblico, ovvero la sua modifica da parte di altri oggetti.

L'azione eseguirà le operazioni seguenti:

* Cambia il modificatore di accesso impostandolo come privato.
* Genera un getter e un setter per il campo (a meno che il campo non sia di sola lettura, nel qual caso genera solo un getter).


## <a name="source-analysis"></a>Analisi dell'origine

L'analisi dell'origine analizza il codice in tempo reale, sottolineando potenziali errori e violazioni di stile e fornendo correzioni automatiche come azioni di contesto. 

È possibile visualizzare tutti i risultati dell'analisi dell'origine per qualsiasi file, in qualsiasi momento, visualizzando la barra di scorrimento sul lato destro dell'editor di testo:

 ![Barra laterale di analisi dell'origine](media/refactoring-image4a.png)

Se si fa clic sul cerchio nella parte superiore, è possibile scorrere ogni suggerimento, con i problemi più gravi visualizzati per primi. Passando il puntatore su un singolo risultato o una singola riga viene visualizzato il problema, che può essere risolto tramite azioni di contesto:

 ![Elemento di analisi dell'origine](media/refactoring-image5.png)

