---
title: 'Passaggio 5: aggiungere gestori di eventi Enter per i controlli NumericUpDown | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-acquisition
ms.topic: conceptual
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 888b63dd4b98d13489c090165cacdac291055b70
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>Passaggio 5: aggiungere gestori di eventi Enter per i controlli NumericUpDown
Nella quinta parte di questa esercitazione si aggiungeranno i gestori eventi Enter per semplificare l'inserimento delle risposte ai problemi del quiz. Con questo codice si selezionerà e si cancellerà il valore corrente di ogni controllo NumericUpDown non appena l'esecutore del quiz sceglie il controllo e inizia a immettere un altro valore.  
  
> [!NOTE]
>  Questo argomento fa parte di una serie di esercitazioni sui concetti di codifica di base. Per una panoramica dell'esercitazione, vedere [Esercitazione 2: creare un quiz matematico a tempo](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
### <a name="to-verify-the-default-behavior"></a>Per verificare il comportamento predefinito  
  
1.  Eseguire il programma e avviare il quiz.  
  
     Nel controllo NumericUpDown per il problema relativo all'addizione, il cursore lampeggia accanto al valore **0** (zero).  
  
2.  Se si immette `3`, è possibile notare che il controllo indica **30**.  
  
3.  Se si immette `5` si nota che viene visualizzato il valore **350**, modificato dopo un secondo in **100**.  
  
     Prima di correggere il problema, esaminare questo comportamento. Si consideri per quale motivo lo **0** non scompare quando si immette `3` e per quale motivo il valore **350** viene sostituito con **100**, ma non immediatamente.  
  
     Questo comportamento può risultare strano, ma è significativo secondo la logica del codice. Quando si fa clic sul pulsante **Avvia**, la proprietà **Enabled** viene impostata su **False** e il pulsante viene visualizzato in grigio e non è disponibile. Il programma imposta la selezione corrente (stato attivo) sul controllo con il successivo valore TabIndex più basso, ovvero il controllo NumericUpDown per il problema dell'addizione. Quando si utilizza il tasto TAB per passare a un controllo NumericUpDown, il cursore viene automaticamente posizionato all'inizio del controllo, il che spiega perché i numeri immessi vengono visualizzati a sinistra e non a destra. Quando si specifica un numero maggiore del valore della proprietà **MaximumValue**, impostato su 100, il numero immesso viene sostituito con il valore di tale proprietà.  
  
### <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>Per aggiungere un gestore eventi Enter per un controllo NumericUpDown  
  
1.  Scegliere il primo controllo NumericUpDown (denominato "somma") nel form, quindi scegliere l'icona **Eventi** sulla barra degli strumenti nella finestra di dialogo **Proprietà**.  
  
     La scheda **Eventi** nella finestra di dialogo **Proprietà** visualizza tutti gli eventi a cui è possibile rispondere (che è possibile gestire) per l'elemento scelto nel form. Poiché è stato scelto il controllo NumericUpDown, tutti gli eventi elencati sono relativi a esso.  
  
2.  Scegliere l'evento **Enter**, immettere `answer_Enter`, quindi premere INVIO.  
  
     ![Finestra di dialogo Proprietà](../ide/media/express_answerenter.png "Express_AnswerEnter")  
Finestra di dialogo Proprietà  
  
     Si è appena aggiunto un gestore eventi Enter per il controllo NumericUpDown della somma e il gestore è stato denominato **answer_Enter**.  
  
3.  Nel metodo per il gestore eventi **answer_Enter** aggiungere il codice seguente.  
  
     [!code-vb[VbExpressTutorial3Step5_6#11](../ide/codesnippet/VisualBasic/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#11](../ide/codesnippet/CSharp/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.cs)]  
  
     Sebbene il codice possa sembrare complesso, è facile da capire se lo si analizza passaggio per passaggio. Innanzitutto, osservare l'inizio del metodo: `object sender` in C# o `sender As System.Object` in Visual Basic. Questo parametro fa riferimento all'oggetto di cui viene generato l'evento, noto come mittente. In questo caso l'oggetto mittente è il controllo NumericUpDown. Pertanto, nella prima riga del metodo si specifica che il mittente non è un oggetto generico, ma è in maniera specifica un controllo NumericUpDown. Tenere presente che ogni controllo NumericUpDown è un oggetto, ma non tutti gli oggetti sono controlli NumericUpDown. Il controllo NumericUpDown è denominato **answerBox** in questo metodo, poiché verrà usato per tutti i controlli NumericUpDown nel form, non solo dal controllo NumericUpDown della somma. Poiché si dichiara la variabile answerBox in questo metodo, il relativo ambito è applicabile solo a questo metodo. In altre parole, è possibile utilizzare la variabile solo all'interno del metodo.  
  
     La riga successiva verifica se answerBox è stato convertito (cast) correttamente da un oggetto in un controllo NumericUpDown. Se la conversione ha esito negativo, la variabile avrebbe un valore pari a `null` (C#) o `Nothing` (Visual Basic). La terza riga ottiene la lunghezza della risposta visualizzata nel controllo NumericUpDown, mentre la quarta riga seleziona il valore corrente nel controllo in base a tale lunghezza. A questo punto, quando l'esecutore del quiz sceglie il controllo, Visual Studio genera l'evento che determina la selezione della risposta corrente. Non appena l'esecutore del quiz inizia a immettere un'altra risposta, la risposta precedente viene cancellata e sostituita con la nuova.  
  
4.  In Progettazione Windows Form, scegliere il controllo NumericUpDown di differenza.  
  
5.  Nella pagina **Eventi** della finestra di dialogo **Proprietà** scorrere fino all'evento **Enter**, scegliere la freccia a discesa alla fine della riga, quindi scegliere il gestore eventi `answer_Enter` appena aggiunto.  
  
6.  Ripetere il passaggio precedente per i controlli NumericUpDown del prodotto e del quoziente.  
  
7.  Salvare ed eseguire il programma.  
  
     Quando si sceglie un controllo NumericUpDown, il valore esistente viene selezionato automaticamente quindi cancellato quando si inizia a immettere un altro valore.  
  
### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
-   Per andare al passaggio successivo dell'esercitazione, vedere [Passaggio 6: aggiungere un problema di sottrazione](../ide/step-6-add-a-subtraction-problem.md).  
  
-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 4: aggiungere il metodo CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md).