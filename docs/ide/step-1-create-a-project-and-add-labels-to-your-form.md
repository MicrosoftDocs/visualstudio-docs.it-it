---
title: 'Passaggio 1: creare un progetto e aggiungere etichette al form | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
caps.latest.revision: "16"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ab50592e345a54853e9cfbd95d0b9bd1bc86d794
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>Passaggio 1: creare un progetto e aggiungere etichette al form
I passaggi iniziali dello sviluppo di questo quiz consistono nella creazione del progetto e nell'aggiunta di etichette, di un pulsante e di altri controlli a un modulo. Si impostano inoltre le proprietà di ogni controllo che si desidera aggiungere. Il progetto conterrà il modulo, i controlli e, più avanti nell'esercitazione, il codice. Il pulsante avvia il quiz, le etichette mostrano i problemi del quiz e gli altri controlli mostrano le risposte e il tempo rimanente per completarlo.  
  
> [!NOTE]
>  Questo argomento fa parte di una serie di esercitazioni sui concetti di codifica di base. Per una panoramica dell'esercitazione, vedere [Esercitazione 2: creare un quiz matematico a tempo](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
### <a name="to-create-a-project-and-and-set-properties-for-a-form"></a>Per creare un progetto e impostare le proprietà per un modulo  
  
1.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2.  Nell'elenco **Modelli installati** scegliere **C#** o **Visual Basic**.  
  
3.  Nell'elenco di modelli scegliere il modello **Windows Forms Application**, assegnare a esso il nome **Quiz matematico** e scegliere il pulsante **OK**.  
  
     Verrà visualizzato un modulo con nome **Form1.cs** o **Form1.vb**, a seconda del linguaggio di programmazione scelto.  
  
4.  Scegliere il modulo e impostare la proprietà **Text** su **Quiz matematico**.  
  
     La finestra **Proprietà** conterrà le proprietà per il modulo.  
  
5.  Impostare le dimensioni del modulo su 500 pixel di larghezza per 400 pixel di altezza.  
  
     È possibile ridimensionare il modulo trascinando i relativi bordi finché le dimensioni corrette non compaiono nell'angolo inferiore sinistro dell'ambiente di sviluppo integrato (IDE). In alternativa, è possibile modificare i valori della proprietà **Size**.  
  
6.  Impostare il valore della proprietà **FormBorderStyle** su **Fixed3D** e la proprietà **MaximizeBox** su **False**.  
  
     Questi valori impediranno agli esecutori del quiz di ridimensionare il modulo.  
  
### <a name="to-create-the-time-remaining-box"></a>Per creare la casella Tempo rimanente  
  
1.  Aggiungere un controllo **Label** dalla casella degli strumenti e impostare il valore della proprietà **(Name)** su `timeLabel`.  
  
     Questa etichetta diventerà una casella nell'angolo superiore destro in cui verrà visualizzato il numero di secondi rimanenti per il quiz.  
  
2.  Impostare la proprietà **AutoSize** su **False** in modo da poter ridimensionare la casella.  
  
3.  Impostare la proprietà **BorderStyle** su **FixedSingle** per disegnare una riga intorno alla casella.  
  
4.  Impostare la proprietà **Size** su **200, 30**.  
  
5.  Spostare l'etichetta nell'angolo superiore destro del modulo, dove verranno visualizzate righe dello spaziatore blu.  
  
     Queste righe consentono di allineare i controlli nel modulo.  
  
6.  Nella finestra **Proprietà** scegliere la proprietà **Text** e usare BACKSPACE per cancellarne il valore.  
  
7.  Scegliere il segno più (+) accanto alla proprietà **Font**, quindi impostare il valore della proprietà **Size** su **15,75**.  
  
     È possibile modificare diverse proprietà del tipo di carattere, come illustrato di seguito.  
  
     ![Finestra Proprietà con la dimensione del carattere](../ide/media/express_setfontsize.png "Express_setFontSize")  
Finestra Proprietà con la dimensione del carattere  
  
8.  Aggiungere un altro controllo **Label** dalla Casella degli strumenti e impostare la dimensione del tipo di carattere su **15,75**.  
  
9. Impostare la proprietà **Text** su **Tempo rimanente**.  
  
10. Spostare l'etichetta in modo che risulti allineata a sinistra dell'etichetta **timeLabel**.  
  
### <a name="to-add-controls-for-the-addition-problems"></a>Per aggiungere controlli per i problemi di addizione  
  
1.  Aggiungere un controllo **Label** dalla Casella degli strumenti e impostare la relativa proprietà **Text** su **?** (punto interrogativo).  
  
2.  Impostare la proprietà **AutoSize** su **False**.  
  
3.  Impostare la proprietà **Size** su **60, 50**.  
  
4.  Impostare la dimensione del carattere su **18**.  
  
5.  Impostare la proprietà **TextAlign** su **MiddleCenter**.  
  
6.  Impostare la proprietà **Location** su **50, 75** per posizionare il controllo sul modulo.  
  
7.  Impostare la proprietà **(Name)** su **plusLeftLabel**.  
  
8.  Scegliere l'etichetta **plusLeftLabel**, quindi premere CTRL+C o scegliere **Copia** dal menu **Modifica**.  
  
9. Incollare l'etichetta tre volte premendo CTRL+V o scegliendo **Incolla** dal menu **Modifica**.  
  
10. Disporre le tre nuove etichette in modo che risultino in fila a destra dell'etichetta **plusLeftLabel**.  
  
     È possibile utilizzare le righe dello spaziatore per distanziarle e allinearle.  
  
11. Impostare il valore della proprietà **Text** della seconda etichetta su **+** (segno più).  
  
12. Impostare il valore della proprietà **(Name)** della terza etichetta su **plusRightLabel**.  
  
13. Impostare il valore della proprietà **Text** della quarta etichetta su **=** (segno di uguale).  
  
14. Aggiungere un controllo **NumericUpDown** dalla Casella degli strumenti, impostare la dimensione del tipo di carattere su **18** e impostare la relativa larghezza su **100**.  
  
     Più avanti verranno fornite ulteriori informazioni su questo tipo di controllo.  
  
15. Allineare il controllo **NumericUpDown** ai controlli Label per il problema di addizione.  
  
16. Impostare il valore della proprietà **(Name)** per il controllo **NumericUpDown** su **somma**.  
  
     È stata creata la prima riga, come illustrato di seguito.  
  
     ![Prima riga del quiz matematico](../ide/media/express_firstrow.png "Express_firstRow")  
Prima riga del quiz matematico  
  
### <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Per aggiungere controlli per i problemi di sottrazione, moltiplicazione e divisione  
  
1.  Copiare tutti e cinque i controlli per il problema di addizione (i quattro controlli Label e il controllo NumericUpDown) e incollarli.  
  
     Il modulo contiene cinque nuovi controlli, ancora selezionati.  
  
2.  Spostare tutti i controlli in modo che risultino allineati sotto i controlli di addizione.  
  
     È possibile utilizzare le righe dello spaziatore per distanziare adeguatamente le due righe.  
  
3.  Impostare il valore della proprietà **Text** per la seconda etichetta su **-** (segno meno).  
  
4.  Assegnare alla prima etichetta punto interrogativo il nome **minusLeftLabel**.  
  
5.  Assegnare alla seconda etichetta punto interrogativo il nome **minusRightLabel**.  
  
6.  Denominare il controllo **NumericUpDown** **differenza**.  
  
7.  Incollare i cinque controlli altre due volte.  
  
8.  Per la terza riga, assegnare alla prima etichetta il nome **timesLeftLabel**, impostare la proprietà **Text** della seconda etichetta su **×** (segno di moltiplicazione), assegnare alla terza etichetta il nome **timesRightLabel** e assegnare al controllo NumericUpDown il nome **prodotto**.  
  
9. Per la quarta riga, assegnare alla prima etichetta il nome **dividedLeftLabel**, impostare la proprietà **Text** della seconda etichetta su **÷** (segno di divisione), assegnare alla terza etichetta il nome **dividedRightLabel** e assegnare al controllo NumericUpDown il nome **quoziente**.  
  
    > [!NOTE]
    >  È possibile copiare il segno di moltiplicazione × e il segno di divisione ÷ da questa esercitazione e incollarli nel form.  
  
### <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Per aggiungere un pulsante di avvio e impostare l'ordine dell'indice di tabulazione  
  
1.  Aggiungere un controllo **Button** dalla Casella degli strumenti e impostare la relativa proprietà **(Name)** su **startButton**.  
  
2.  Impostare la proprietà **Text** su **Avvia il quiz**.  
  
3.  Impostare la dimensione del carattere su **14**.  
  
4.  Impostare la proprietà **AutoSize** su **True**, in modo che il pulsante venga ridimensionato automaticamente per adattarsi al testo.  
  
5.  Centrare il pulsante nella parte inferiore del modulo.  
  
6.  Impostare il valore della proprietà **TabIndex** per il controllo **startButton** su **1**.  
  
    > [!NOTE]
    >  La proprietà **TabIndex** imposta l'ordine dei controlli quando l'esecutore del quiz preme TAB. Per verificarne il funzionamento, aprire una finestra di dialogo qualsiasi, ad esempio sulla barra dei menu scegliere **File**, **Apri**, quindi premere TAB alcune volte. Osservare il modo in cui il cursore si sposta da un controllo all'altro ogni volta che si preme il tasto TAB. Un programmatore ha deciso l'ordine quando ha creato il modulo.  
  
7.  Impostare il valore della proprietà **TabIndex** per il controllo somma NumericUpDown su **2**, per il controllo differenza su **3**, per il controllo prodotto su **4** e per il controllo quoziente su **5**.  
  
     Il modulo avrà ora il seguente aspetto.  
  
     ![Form del quiz matematico iniziale](../ide/media/express_formlaidout.png "Express_FormLaidOut")  
Form iniziale del quiz matematico  
  
8.  Per verificare se la proprietà **TabIndex** funziona come previsto, salvare ed eseguire il programma premendo F5 o scegliendo **Debug** e **Avvia debug** sulla barra dei menu e premendo TAB alcune volte.  
  
### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
-   Per andare al passaggio successivo dell'esercitazione, vedere [Passaggio 2: creare un problema di addizione casuale](../ide/step-2-create-a-random-addition-problem.md).  
  
-   Per tornare all'argomento introduttivo, vedere [Esercitazione 2: creare un quiz matematico a tempo](../ide/tutorial-2-create-a-timed-math-quiz.md).