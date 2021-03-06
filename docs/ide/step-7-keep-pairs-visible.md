---
title: 'Passaggio 7: Mantenere le coppie visibili'
description: Informazioni su come aggiungere un'istruzione if in modo che, quando il giocatore seleziona una coppia di icone corrispondente, le icone restino visibili.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 68da08d84ea05c999a1678df4591737eb793daa6
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2021
ms.locfileid: "107297015"
---
# <a name="step-7-keep-pairs-visible"></a>Passaggio 7: Mantenere le coppie visibili
Il gioco funziona finché il giocatore sceglierà coppie di icone che non corrispondono. Si consideri però cosa dovrebbe accadere quando il giocatore sceglie una coppia esatta. Anziché far scomparire le icone attivando il timer, tramite il metodo <xref:System.Windows.Forms.Timer.Start>, il gioco deve reimpostarsi in modo da non tenere più traccia delle etichette tramite le variabili di riferimento `firstClicked` e `secondClicked`, senza reimpostare i colori delle due etichette scelte.

## <a name="to-keep-pairs-visible"></a>Per mantenere le coppie visibili

1. Aggiungere l'istruzione `if` seguente al metodo del gestore eventi `label_Click()`, quasi alla fine del codice, appena prima dell'istruzione di avvio del timer. Esaminare attentamente il codice mentre lo si aggiunge al programma. Considerarne il funzionamento.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step7/cs/form1.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step7/vb/form1.vb" id="Snippet9":::

     > [!IMPORTANT]
     > Usare il controllo linguaggio di programmazione nella parte superiore destra della pagina per visualizzare il frammento di codice C# o il frammento di codice Visual Basic.<br><br>![Controllo del linguaggio di programmazione per Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     La prima riga dell'istruzione `if` appena aggiunta controlla se l'icona nella prima etichetta scelta dal giocatore è uguale all'icona nella seconda etichetta. Se le icone sono identiche, il programma esegue le tre istruzioni racchiuse tra parentesi graffe in C# o le tre istruzioni all'interno dell'istruzione `if` in Visual Basic. Le prime due istruzioni reimpostano le variabili di riferimento `firstClicked` e `secondClicked` in modo che non tengano più traccia delle etichette. È possibile riconoscere le due istruzioni dal gestore eventi del timer <xref:System.Windows.Forms.Timer.Tick> . La terza istruzione è un' `return` istruzione, che indica al programma di ignorare le altre istruzioni nel metodo senza eseguirle.

     Se si usa la programmazione in C#, è possibile notare che parte del codice usa un solo segno di uguale ( `=` ), mentre altre istruzioni utilizzano due segni di uguale ( `==` ). Considerare il perché venga utilizzato in alcune occasioni `=`, in altre `==`.

     Questo è un ottimo esempio per comprendere la differenza. Esaminare attentamente il codice tra parentesi nell'istruzione `if`.

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     Osservare quindi attentamente la prima istruzione nel blocco di codice dopo l'istruzione `if`.

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     La prima delle due istruzioni controlla se due icone sono uguali. Poiché vengono confrontati due valori, il programma C# usa l' `==` operatore di uguaglianza. La seconda istruzione in realtà modifica il valore, detto *assegnazione*, impostando la variabile di riferimento `firstClicked` su `null` per reimpostarla. Per questo viene utilizzato l'operatore di assegnazione `=`. C# usa `=` per impostare i valori e `==` per confrontarli. Visual Basic utilizza `=` sia per l'assegnazione che per il confronto delle variabili.

2. Salvare ed eseguire il programma, quindi iniziare a scegliere icone nel form. Se si sceglie una coppia che non corrisponde, l'evento Tick del timer si attiva ed entrambe le icone scompaiono. Se si sceglie una coppia corrispondente, la nuova `if` istruzione viene eseguita e l'istruzione return fa sì che il metodo ignori il codice che avvia il timer, in modo che le icone restino visibili, come illustrato nella figura seguente.

     ![Gioco creato in questa esercitazione](../ide/media/express_finishedgame.png)<br/>
***Abbinamenti di gioco** _ _WITH coppie di icone visibili *

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere **[passaggio 8: aggiungere un metodo per verificare se il giocatore ha vinto](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)**.

- Per tornare al passaggio precedente dell'esercitazione, vedere [passaggio 6: aggiungere un timer](../ide/step-6-add-a-timer.md).
