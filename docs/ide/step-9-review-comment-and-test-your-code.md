---
title: 'Passaggio 9: Esaminare, commentare e testare il codice'
description: Informazioni su come aggiungere un commento al codice e testare l'app.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c11e13f87ab166c3e1f545dbe2a885ada5e488b5
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295377"
---
# <a name="step-9-review-comment-and-test-your-code"></a>Passaggio 9: Esaminare, commentare e testare il codice

Successivamente si aggiunge un commento al codice. Un commento è una nota che non modifica il comportamento dell'app. Facilita la comprensione del codice da parte di altri utenti. L'aggiunta di commenti al codice è un'operazione consigliabile.

In C# due barre (//) contrassegnano una riga come commento. In Visual Basic viene utilizzata una virgoletta singola (') per contrassegnare una riga come commento. Dopo aver aggiunto un commento, testare l'applicazione. È consigliabile eseguire frequentemente e testare il codice mentre si lavora sui progetti, in modo che sia possibile intercettare e correggere eventuali problemi, prima che il codice diventi più complesso. Si tratta di un *test iterativo*.

Si è appena compilato un programma che funziona e sebbene non sia ancora finito, è già in grado di caricare un'immagine. Prima di aggiungere un commento al codice e di testarlo, prendere tempo per rivedere i concetti di codifica, poiché tali concetti si utilizzeranno frequentemente:

- Dopo aver fatto doppio clic sul pulsante **Mostra immagine** in **Progettazione Windows Form**, l'IDE ha aggiunto automaticamente un *metodo* al codice del programma.

- I metodi rappresentano la modalità di organizzazione del codice, vale a dire il modo in cui viene raggruppato il codice.

- Nella maggior parte dei casi, un metodo esegue un piccolo numero di operazioni in un ordine specifico, ad esempio come il `showButton_Click()` Metodo (o `ShowButton_Click()` ) Mostra una finestra di dialogo e quindi carica un'immagine.

- Un metodo è costituito da *istruzioni* o righe di codice. Un metodo può essere considerato un modo per raggruppare istruzioni d codice.

- Quando un metodo viene eseguito, o *chiamato*, le istruzioni nel metodo vengono eseguite in ordine, una dopo l'altra, a cominciare dalla prima.

   Di seguito è riportato un esempio di istruzione.

  ```csharp
  PictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Le istruzioni consentono ai programmi di eseguire azioni. In C# un'istruzione termina sempre con un punto e virgola. In Visual Basic la fine di una riga è la fine di un'istruzione. In Visual Basic non è necessario alcun punto e virgola. L'istruzione precedente indica <xref:System.Windows.Forms.PictureBox> al controllo di caricare il file selezionato dall'utente con il componente **OpenFileDialog** .

## <a name="to-add-comments"></a>Per aggiungere commenti

1. Aggiungere il seguente commento al codice.

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb" id="Snippet1":::

    Il gestore dell'evento <xref:System.Windows.Forms.Control.Click> del pulsante **showButton** è ora completato e funziona. Si è iniziato a scrivere codice, iniziando con l'istruzione `if`. Un' `if` istruzione è il modo in cui si indica all'app, "controllare questa cosa e, se è vero, eseguire queste azioni". In questo caso, si indica all'app di aprire la finestra di dialogo **Apri file** e se l'utente seleziona un file e sceglie il pulsante **OK** , caricare il file in **PictureBox**.

    > [!TIP]
    > L'IDE è compilato in modo da semplificare la scrittura del codice anche tramite i *frammenti di codice*. Un frammento è un collegamento che viene espanso in un piccolo blocco di codice.
    >
    >  È possibile visualizzare tutti i frammenti disponibili. Sulla barra dei menu scegliere **strumenti**  >  **Gestione frammenti di codice**. Per C#, il `if` frammento di codice si trova in **Visual C#** . Per Visual Basic, i `if` frammenti di codice sono inclusi nei **modelli di codice**  >  **condizionali e cicli**. È possibile utilizzare questo strumento di gestione per esplorare frammenti esistenti o aggiungere frammenti personalizzati.
    >
    >  Per attivare un frammento quando si digita il codice, digitarlo e premere **TAB**. Molti frammenti di codice vengono visualizzati nella finestra di **IntelliSense** ed è per questo motivo che è necessario premere **TAB** due volte: prima per selezionare il frammento di codice nella finestra di **IntelliSense** e poi per indicare all'IDE di usare il frammento di codice. Si noti che IntelliSense supporta il frammento `if`, ma non il frammento `ifelse`.

1. Prima di eseguire l'applicazione, salvare l'app scegliendo il pulsante della barra degli strumenti **Salva tutto** , che dovrebbe essere simile allo screenshot seguente.

     ![Pulsante della barra degli strumenti Salva tutto](../ide/media/express_iconsaveall.png)<br>
***Salva tutto** _ _button *

     In alternativa, per salvare l'app, scegliere **file**  >  **Salva tutto** dalla barra dei menu o premere **CTRL** + **MAIUSC** + **S**. Una procedura consigliata consiste nel salvare presto e spesso.

     Quando è in esecuzione, il programma dovrebbe essere simile all'immagine seguente.

     ![Visualizzatore di immagini](../ide/media/express_pictureviewerdonerun.png)<br>***Visualizzatore di immagini***

## <a name="to-test-your-app"></a>Per testare l'app

1. Premere il tasto **F5** o scegliere il pulsante della barra degli strumenti **Avvia debug** .

1. Scegliere il pulsante **Visualizza immagine** per eseguire il codice appena scritto. Prima di tutto, l'app apre una finestra di dialogo **Apri file** . Verificare che i filtri vengano visualizzati nell'elenco a discesa **Tipo file** nella parte inferiore della finestra di dialogo. Passare quindi a un'immagine e aprirla. In genere è possibile trovare immagini di esempio incluse nel sistema operativo Windows nella cartella *Documenti*, che si trova all'interno della cartella *Immagini\Immagini campione*.

    > [!TIP]
    > Se nella finestra di dialogo relativa alla **selezione di un file immagine** non sono presenti immagini, assicurarsi che il filtro **Tutti i file (*.\*)** sia selezionato nell'elenco a discesa nella parte inferiore destra della finestra di dialogo.

1. Caricare un'immagine. L'immagine viene visualizzata in PictureBox. Provare quindi a ridimensionare il form trascinandone i bordi. Poiché PictureBox è ancorato all'interno di TableLayoutPanel, il quale è a sua volta ancorato all'interno del form, l'area dell'immagine verrà ridimensionata in modo da eguagliare la larghezza del form e da riempire il 90% del form nella parte superiore. È per questo motivo che sono stati usati i contenitori <xref:System.Windows.Forms.TableLayoutPanel> e <xref:System.Windows.Forms.FlowLayoutPanel>, che mantengono le dimensioni corrette del modulo quando l'utente lo ridimensiona.

     A questo punto le immagini più grandi superano i bordi del visualizzatore immagini. Nel prossimo passaggio verrà aggiunto il codice per adattare le immagini alla finestra.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere **[passaggio 10: scrivere codice per pulsanti aggiuntivi e una casella di controllo](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)**.

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 8: Scrivere codice per il gestore dell'evento del pulsante Mostra immagine](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

## <a name="see-also"></a>Vedere anche

* [Esercitazione 2: creare un quiz matematico a tempo](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: creare un gioco di abbinamenti](tutorial-3-create-a-matching-game.md)
