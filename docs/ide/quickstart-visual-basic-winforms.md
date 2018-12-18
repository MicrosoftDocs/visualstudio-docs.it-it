---
title: 'Guida introduttiva: Creare un''app Windows Forms in Visual Studio con Visual Basic | Microsoft Docs'
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: ghogen
dev_langs: vb
ms.workload: multiple
ms.openlocfilehash: ecab13523c5d2ae362a58527f8c15ce1f26dd225
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Guida introduttiva: Creare un'app Windows Forms in Visual Studio con Visual Basic
In questa introduzione di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio si creerà una semplice applicazione di Visual Basic con un'interfaccia utente basata su Windows.

Se non è ancora stato installato Visual Studio, accedere alla pagina [Download di Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) per installarlo gratuitamente.

## <a name="create-a-project"></a>Creare un progetto
In primo luogo si creerà un progetto di applicazione Visual Basic. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.  

1. Aprire Visual Studio 2017.  

2. Nella barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.  

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual Basic**, quindi selezionare **Desktop classico di Windows**. Nel riquadro centrale scegliere il modello **App Windows Forms (.NET Framework)**. Assegnare al file il nome `HelloWorld`.  

     Se non viene visualizzato il modello del progetto **App Windows Forms (.NET Framework)**, chiudere la finestra di dialogo **Nuovo progetto** e nella barra dei menu in alto scegliere **Strumenti** > **Ottieni strumenti e funzionalità**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo per desktop .NET**, quindi scegliere **Modifica**.  

     ![Carico di lavoro Sviluppo per desktop .NET nel programma di installazione di Visual Studio](../ide/media/install-dot-net-desktop-env.png)  

## <a name="create-the-application"></a>Creare l'applicazione
Dopo aver selezionato il modello di progetto Visual Basic e assegnato un nome al file, in Visual studio viene aperto un modulo. Un modulo è un'interfaccia utente di Windows. Ora si crea un'applicazione "Hello World" aggiungendo controlli al modulo, quindi si esegue l'applicazione.   

### <a name="add-a-button-to-the-form"></a>Aggiungere un pulsante al modulo  

1. Fare clic su **Casella degli strumenti** per aprire la finestra a comparsa della casella degli strumenti.

     ![Fare clic su Casella degli strumenti per aprire la finestra della casella degli strumenti](../ide/media/vb-toolbox-toolwindow.png)  

     (Se l'opzione di apertura a comparsa della Casella degli strumenti non viene visualizzata, è possibile aprirla dalla barra dei menu. A tale scopo fare clic su **Visualizza** > **Casella degli strumenti**. In alternativa, premere **CTRL**+**ALT**+**X**.)

2. Fare clic sull'icona **Blocca** per ancorare la Casella degli strumenti.

     ![Fare clic sull'icona Blocca per ancorare la Casella degli strumenti all'IDE](../ide/media/vb-pin-the-toolbox-window.png)  
3. Fare clic sul controllo **Pulsante** e trascinarlo nel modulo.

     ![Aggiungere un pulsante al modulo](../ide/media/vb-add-a-button-to-form1.png)

4. Nella sezione **Aspetto** della finestra **Proprietà** digitare "Click this", e premere **INVIO**.

     ![Aggiungere testo al pulsante nel modulo](../ide/media/vb-button-control-text.png)  

     (Se la finestra Proprietà non viene visualizzata, è possibile aprirla dalla barra dei menu. A tale scopo fare clic su **Visualizza** > **Finestra Proprietà**. In alternativa premere **F4**.)

5. Nella sezione **Progettazione** della finestra **Proprietà** cambiare il nome da "Button1" a "btnClickThis", quindi premere **INVIO**.

     ![Aggiungere una funzione al pulsante nel modulo](../ide/media/vb-button-control-function.png)

### <a name="add-a-label-to-the-form"></a>Aggiungere un'etichetta al modulo
È stato aggiunto un controllo pulsante per creare un'azione. Ora si aggiungerà un controllo etichetta al quale inviare del testo.

1. Selezionare il controllo **Etichetta** nella Casella degli strumenti, quindi trascinarlo sul modulo e rilasciarlo sotto il pulsante **Click this**.

2. Nella sezione **Progettazione** della finestra **Proprietà** cambiare il nome da "Label1" a "lblHelloWorld", quindi premere **INVIO**.

### <a name="add-code-to-the-form"></a>Aggiungere codice al modulo

1. Nella finestra**Form1.vb &#91;Design&#93;** fare doppio clic sul pulsante **Click this** per aprire la finestra **Form1.vb**.

      In alternativa è possibile espandere **Form1.vb** nella finestra **Esplora soluzioni** e quindi fare clic su **Form1**.

2. Nella finestra **Form1.vb** tra la riga **Private Sub** e la riga **End Sub** digitare o incollare `lblHelloWorld.Text = "Hello World!"`.

     ![Aggiungere codice a un modulo](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Esecuzione dell'applicazione
1. Fare clic sul pulsante **Avvia** per eseguire l'applicazione.

     ![Fare clic su Avvia per eseguire il debug e avviare l'app](../ide/media/vb-click-start-hello-world.png)

   Vengono eseguite diverse operazioni. Nell'IDE di Visual Studio viene aperta la finestra Strumenti di diagnostica e anche una finestra Output. All'esterno dell'IDE viene visualizzata una finestra di dialogo Form1. La finestra include il pulsante **Click this** e il testo "Label1".

2. Fare clic sul pulsante **Click this** nella finestra di dialogo **Form1**. Osservare che il testo "Label1" diventa "Hello World!".

    ![Finestra di dialogo Form1 con il testo Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per l'apprendimento dell'uso di Visual Basic e dell'IDE di Visual Studio. Per approfondire ancora le conoscenze, continuare con un'esercitazione nella sezione **Esercitazioni** del sommario.  

## <a name="see-also"></a>Vedere anche   
* [Guida introduttiva: Creare un'app console in Visual Studio con Visual Basic](quickstart-visual-basic-console.md)
* [Learn more about Visual Basic IntelliSense](visual-basic-specific-intellisense.md) (Altre informazioni su Visual Basic IntelliSense)  
