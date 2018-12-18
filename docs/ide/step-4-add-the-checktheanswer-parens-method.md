---
title: 'Passaggio 4: aggiungere il metodo CheckTheAnswer() | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-acquisition
ms.topic: conceptual
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3d6f38288b09ed9509b1c99b30fd72ed776700c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="step-4-add-the-checktheanswer-method"></a>Passaggio 4: aggiungere il metodo CheckTheAnswer()
Nella quarta parte di questa esercitazione si scriverà un metodo, `CheckTheAnswer()`, che verifica se le risposte ai problemi di matematica sono corrette. Questo argomento fa parte di una serie di esercitazioni sui concetti di codifica di base. Per una panoramica dell'esercitazione, vedere [Esercitazione 2: creare un quiz matematico a tempo](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
> [!NOTE]
>  Se si utilizza Visual Basic, poiché questo metodo restituisce un valore, anziché la solita parola chiave `Function` si utilizzerà invece la parola chiave `Sub`. È molto semplice: una subroutine non restituisce un valore, ma una funzione sì.  
  
### <a name="to-verify-whether-the-answers-are-correct"></a>Per verificare se le risposte sono corrette  
  
1.  Aggiungere il metodo `CheckTheAnswer()`.  
  
     Quando viene chiamato, questo metodo aggiunge i valori di addend1 e addend2 e confronta il risultato al valore nel controllo `NumericUpDown` della somma. Se i valori sono uguali, il metodo restituisce il valore `true`. In caso contrario, il metodo restituisce il valore `false`. Il codice dovrebbe essere analogo al seguente.  
  
     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]  
  
     Successivamente, si controllerà la risposta aggiornando il codice nel metodo per il gestore dell'evento Tick del timer per chiamare il nuovo metodo `CheckTheAnswer()`.  
  
2.  Aggiungere il codice seguente all'istruzione `if else`:  
  
     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]  
  
     Se la risposta è corretta, `CheckTheAnswer()` restituisce `true`. Il gestore eventi arresta il timer, visualizza un messaggio di congratulazioni e rende quindi nuovamente disponibile il pulsante **Avvio**. In caso contrario, il quiz continua.  
  
3.  Salvare il programma, eseguirlo, avviare un quiz e fornire una risposta corretta al problema di addizione.  
  
    > [!NOTE]
    >  Prima di immettere la risposta è necessario selezionare il valore predefinito oppure eliminare manualmente lo zero. Si correggerà questo comportamento più avanti in questa esercitazione.  
  
     Quando si fornisce una risposta corretta, viene aperta una finestra di messaggio, il pulsante **Avvio** diventa disponibile e il timer si arresta.  
  
### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
-   Per andare al passaggio successivo dell'esercitazione, vedere [Passaggio 5: aggiungere gestori di eventi Enter per i controlli NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).  
  
-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 3: aggiungere un timer per il conto alla rovescia](../ide/step-3-add-a-countdown-timer.md).