---
title: 'Passaggio 8: scrivere il codice per il gestore dell''evento del pulsante Mostra immagine | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
caps.latest.revision: "24"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b7c76492e3d07b0c32edb4ea91a5b3c152f1a206
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Passaggio 8: scrivere il codice per il gestore dell'evento del pulsante Visualizza immagine
In questo passaggio si imposta il funzionamento del pulsante **Mostra immagine** nel modo seguente:  
  
-   Quando un utente sceglie il pulsante, il programma visualizza una finestra di dialogo **Apri file**.  
  
-   Se l'utente apre un file di immagine, tale immagine viene visualizzata nel controllo PictureBox.  
  
 Nell'IDE è disponibile uno strumento potente denominato IntelliSense che agevola la scrittura del codice. A mano a mano che si immette il codice, l'IDE apre una casella con completamenti suggeriti per le parole parziali immesse. Il programma tenta di determinare l'operazione successiva che l'utente desidera eseguire e passa automaticamente all'ultimo elemento che si sceglie dall'elenco. È possibile utilizzare le frecce su o giù per spostarsi nell'elenco oppure continuare a digitare lettere per limitare le scelte. Quando viene visualizzata la scelta desiderata, premere TAB per selezionarla. In alternativa, è possibile ignorare i suggerimenti, se non si ritengono necessari.  
  
 ![link to video](../data-tools/media/playvideo.gif "PlayVideo")Per una versione video di questo argomento, vedere [Tutorial 1: Create a Picture Viewer in Visual Basic - Video 4](http://go.microsoft.com/fwlink/?LinkId=205215) (Esercitazione 1: Creare un visualizzatore di immagini in Visual Basic) o [Tutorial 1: Create a Picture Viewer in C# - Video 4](http://go.microsoft.com/fwlink/?LinkId=205203) (Esercitazione 1: Creare un visualizzatore di immagini in C# - Video 4). In questi video viene usata una versione precedente di Visual Studio, pertanto vi sono piccole differenze in alcuni comandi di menu e altri elementi dell'interfaccia utente. Tuttavia, i concetti e le procedure funzionano in modo analogo nella versione corrente di Visual Studio.  
  
### <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Per scrivere il codice per il gestore dell'evento del pulsante Visualizza immagine  
  
1.  Passare a Progettazione Windows Form e fare doppio clic sul pulsante **Mostra immagine**. L'IDE passa immediatamente alla finestra di progettazione del codice e sposta il cursore all'interno del metodo `showButton_Click()` aggiunto precedentemente.  
  
2.  Digitare una `i` nella riga vuota tra le due parentesi graffe { }. In Visual Basic digitare nella riga vuota tra Private Sub... ed End Sub. Viene visualizzata una finestra di **IntelliSense** come illustrato nell'immagine seguente.  
  
     ![IntelliSense con Visual C&#35; codice](../ide/media/express_ifintellisense.png "Express_IfIntellisense")  
IntelliSense con codice Visual C#  
  
3.  Nella finestra di **IntelliSense** dovrebbe essere evidenziata la parola **if**. In caso contrario, immettere una `f` minuscola per visualizzarla. Si noti che viene visualizzato un piccolo *tooltip* accanto alla finestra di **IntelliSense** con la descrizione **Frammento di codice per l'istruzione if**. Anche in Visual Basic la descrizione comando dichiara che si tratta di un frammento, ma con una formulazione leggermente diversa. Poiché si vuole usare il frammento di codice, premere TAB per inserire **if** nel codice. Premere quindi di nuovo TAB per usare il frammento **if**. Se si è fatto clic in un altro punto e la finestra di **IntelliSense** non è più visualizzata, tornare alla **i** e ridigitarla. Verrà nuovamente visualizzata la finestra di **IntelliSense**.  
  
     ![Visual C&#35; codice](../ide/media/express_highlighttrue.png "Express_HighlightTrue")  
Codice Visual C#  
  
4.  Viene quindi usato IntelliSense per immettere altro codice per aprire una finestra **Apri file**. Se l'utente ha fatto clic sul pulsante **OK**, il controllo PictureBox carica il file selezionato dall'utente. Nei passaggi seguenti viene illustrato come immettere il codice. Sebbene i passaggi siano numerosi, si tratta solo di poche sequenze di tasti:  
  
    1.  Iniziare con il testo **true** selezionato nel frammento. Digitare `op` per sovrascriverlo. In Visual Basic l'iniziale è maiuscola, pertanto digitare `Op`.  
  
    2.  Viene visualizzata la finestra di **IntelliSense** con **openFileDialog1**. Premere TAB per selezionarlo. In Visual Basic l'iniziale è maiuscola, pertanto viene visualizzato **OpenFileDialog1**. Assicurarsi che **OpenFileDialog1** sia selezionato.  
  
         Per altre informazioni su `OpenFileDialog`, vedere [OpenFileDialog](http://msdn.microsoft.com/library/system.windows.forms.openfiledialog.aspx).  
  
    3.  Digitare un punto (`.`). Poiché è stato digitato un punto subito dopo **openFileDialog1**, viene visualizzata una finestra di **IntelliSense** contenente tutte le proprietà e i metodi del componente **OpenFileDialog**. Si tratta delle stesse proprietà visualizzate nel finestra **Proprietà** quando si sceglie la finestra in Progettazione Windows Form. È inoltre possibile scegliere metodi che indicano al componente di eseguire operazioni (ad esempio, aprire una finestra di dialogo).  
  
        > [!NOTE]
        >  Nella finestra di **IntelliSense** possono essere visualizzati sia proprietà che metodi. Per determinare gli elementi visualizzati, osservare l'icona a sinistra di ogni elemento nella finestra **IntelliSense**. È visualizzata l'immagine di un blocco accanto a ogni metodo e l'immagine di una chiave inglese (o di una chiave fissa) accanto a ogni proprietà. È anche visualizzata un'icona a forma di saetta accanto a ogni evento. Queste immagini vengono visualizzate nel modo seguente.  
  
         ![Icona del metodo](../ide/media/express_iconmethod.png "Express_IconMethod")  
Icona del metodo  
  
         ![Icona della proprietà](../ide/media/express_iconproperty.png "Express_IconProperty")  
Icona della proprietà  
  
         ![Icona dell'evento](../ide/media/express_iconevent.png "Express_IconEvent")  
Icona dell'evento  
  
    4.  Iniziare a digitare `ShowDialog` (l'uso di maiuscole non viene considerato in IntelliSense). Il metodo `ShowDialog()` visualizzerà la finestra di dialogo **Apri file**. Dopo che nella finestra è stato evidenziato **ShowDialog**, premere TAB. È anche possibile evidenziare "ShowDialog" e premere il tasto F1 per ottenere informazioni.  
  
         Per altre informazioni sul metodo `ShowDialog()`, vedere [Metodo ShowDialog](http://msdn.microsoft.com/library/c7ykbedk.aspx).  
  
    5.  Quando si usa un metodo in un controllo o un componente, ovvero si effettua una *chiamata a un metodo*, è necessario aggiungere le parentesi. Immettere quindi le parentesi di apertura e chiusura immediatamente dopo la "g" di `ShowDialog`: `()` Viene visualizzato "openFileDialog1.ShowDialog()".  
  
        > [!NOTE]
        >  I metodi sono una parte importante di qualsiasi programma e in questa esercitazione ne sono stati illustrate diverse modalità di utilizzo. È possibile chiamare un metodo di un componente per indicare l'esecuzione di un'operazione, come è stato fatto quando si è chiamato il metodo `ShowDialog()` del componente **OpenFileDialog**. È possibile creare metodi personalizzati per fare eseguire operazioni al programma, come quello che si sta compilando, denominato metodo `showButton_Click()`, che apre una finestra di dialogo e un'immagine quando l'utente sceglie un pulsante.  
  
    6.  Per Visual C#, aggiungere uno spazio e quindi aggiungere due segni di uguale (`==`). Per Visual Basic, aggiungere uno spazio e quindi usare un solo segno di uguale (`=`). Visual C# e Visual Basic utilizzano operatori di uguaglianza diversi.  
  
    7.  Aggiungere un altro spazio. Viene immediatamente visualizzata un'altra finestra di **IntelliSense**. Iniziare a digitare `DialogResult` e premere TAB per aggiungerlo.  
  
        > [!NOTE]
        >  Quando si scrive codice per chiamare un metodo, a volte viene restituito un valore. In questo caso il metodo `ShowDialog()` del componente **OpenFileDialog** restituisce un valore DialogResult. DialogResult è un valore speciale che fornisce informazioni sulle operazioni eseguite in una finestra di dialogo. Un componente **OpenFileDialog** può far sì che l'utente scelga **OK** o **Annulla**, pertanto il relativo metodo `ShowDialog()` restituisce DialogResult.OK o DialogResult.Cancel.  
  
    8.  Digitare un punto per aprire la finestra di **IntelliSense** del valore DialogResult. Immettere la lettera `O` e premere TAB per inserire **OK**.  
  
         Per altre informazioni su `DialogResult`, vedere [DialogResult](http://msdn.microsoft.com/library/system.windows.forms.dialogresult.aspx).  
  
        > [!NOTE]
        >  La prima riga di codice è stata completata. Per Visual C#, il codice è analogo al seguente.  
        >   
        >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`  
        >   
        >  Per Visual Basic, il codice è analogo al seguente.  
        >   
        >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`  
  
    9. Aggiungere ora l'ultima riga di codice. È possibile digitarlo (o copiarlo e incollarlo), ma è consigliabile utilizzare IntelliSense per aggiungerlo. Più si ha dimestichezza con IntelliSense, più rapidamente si scriverà il codice. L'aspetto del metodo `showButton_Click()` finale sarà simile al seguente. Scegliere la scheda **VB** per visualizzare la versione Visual Basic del codice.  
  
         [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]
         [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]  
  
### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
-   Per andare al passaggio successivo dell'esercitazione, vedere [Passaggio 9: rivedere, commentare e testare il codice](../ide/step-9-review-comment-and-test-your-code.md).  
  
-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 7: aggiungere componenti di finestra di dialogo al form](../ide/step-7-add-dialog-components-to-your-form.md).