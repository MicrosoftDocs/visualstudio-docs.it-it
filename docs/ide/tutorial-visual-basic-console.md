---
title: Introduzione a Visual Basic in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 12/08/2017
ms.technology:
- vs-acquisition
ms.topic: tutorial
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 34c3fe8351196e11073e836d875e940a9ce17d36
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="getting-started-with-visual-basic-in-visual-studio"></a>Introduzione a Visual Basic in Visual Studio
In questa esercitazione per Visual Basic (VB), si userà Visual Studio per creare ed eseguire alcune app console diverse ed esplorare nello stesso tempo alcune funzionalità dell'[ambiente di sviluppo integrato (IDE, Integrated Development Environment)](visual-studio-ide.md) di Visual Studio.

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) per installarlo gratuitamente.

## <a name="before-you-begin"></a>Prima di iniziare
Ecco una rapida serie di domande frequenti per presentare alcuni concetti chiave.
### <a name="what-is-visual-basic"></a>Che cos'è Visual Basic?
Visual Basic è un linguaggio di programmazione indipendente dai tipi progettato per garantire la massima facilità di apprendimento. Deriva dall'acronimo BASIC, che significa "Beginner's All-purpose Symbolic Instruction Code" (Codice di istruzioni simbolico multifunzione per principianti).
### <a name="what-is-visual-studio"></a>Che cos'è Visual Studio?
Visual Studio è una suite integrata per lo sviluppo di strumenti di produttività per gli sviluppatori. Si può immaginare Visual Studio come un programma utilizzabile per creare programmi e applicazioni.  
### <a name="what-is-a-console-app"></a>Che cos'è un'app console?
Un'app console riceve input e visualizza output in una finestra della riga di comando, detta anche console.
### <a name="what-is-net-core"></a>Informazioni su .NET Core
.NET Core è il passaggio successivo nell'evoluzione di .NET Framework. Mentre .NET Framework consentiva di condividere codice tra linguaggi di programmazione diversi, .NET Core aggiunge la possibilità di condividere codice tra piattaforme diverse. E, ciliegina sulla torta, è open source. Sia .NET Framework che .NET Core includono librerie di funzionalità precompilate, nonché un Common Language Runtime (CLR) che svolge la funzione di macchina virtuale in cui eseguire il codice.

## <a name="start-developing"></a>Iniziare a sviluppare
È arrivato il momento di iniziare a sviluppare.

### <a name="create-a-project"></a>Creare un progetto
In primo luogo si creerà un progetto di applicazione Visual Basic. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

1. Aprire Visual Studio 2017.

2. Nella barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual Basic**, quindi selezionare **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Quindi assegnare al file il nome *HelloWorld*.  

   ![Modello di progetto Console App (.NET Core) nella finestra di dialogo Nuovo progetto dell'IDE di Visual Studio](../ide/media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

#### <a name="add-a-workgroup-optional"></a>Aggiungere un gruppo di lavoro (facoltativo)
Se il modello di progetto **Console App (.NET Core)** non è visualizzato, è possibile ottenerlo aggiungendo il carico di lavoro **Sviluppo multipiattaforma .NET Core**. È possibile aggiungere questo carico di lavoro in uno dei due modi seguenti, a seconda degli aggiornamenti di Visual Studio 2017 installati nel computer.

##### <a name="option-1-use-the-new-project-dialog-box"></a>Opzione 1: usare la finestra di dialogo Nuovo progetto
1. Fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro a sinistra della finestra di dialogo **Nuovo progetto**.

  ![Fare clic sul collegamento Apri il programma di installazione di Visual Studio nella finestra di dialogo Nuovo progetto](../ide/media/vs-open-visual-studio-installer-generic.png)

2. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

   ![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

##### <a name="option-2-use-the-tools-menu-bar"></a>Opzione 2: usare la barra del menu Strumenti
1. Chiudere la finestra di dialogo **Nuovo progetto** e dalla barra dei menu superiore scegliere **Strumenti** > **Ottieni strumenti e funzionalità**.

2. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.   

## <a name="create-a-what-is-your-name-application"></a>Creare un'applicazione "What Is Your Name?"
Verrà ora creata un'applicazione che chiede all'utente di immettere il proprio nome, che viene quindi visualizzato insieme alla data e all'ora. Ecco come:

1. Se non è già aperto, aprire il progetto *WhatIsYourName*.

2. Immettere il codice Visual Basic seguente immediatamente dopo la parentesi di apertura che segue la riga `Sub Main(args As String())` e prima della riga `End Sub`:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Questo codice sostituisce le istruzioni <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> e <xref:System.Console.ReadKey%2A> esistenti.

 ![Finestra del codice con il codice di "What Is Your Name?"](../ide/media/vb-codewindow-what-name.png)

3. Quando la finestra della console si apre, immettere il proprio nome. La finestra della console dovrebbe avere un aspetto simile allo screenshot seguente:

   ![Finestra della console con "What is your name?", la data, l'ora della console e il messaggio Premere un tasto per continuare](../ide/media/vb-console-what-name.png)

5. Premere un tasto qualsiasi per chiudere la finestra della console.

## <a name="create-a-calculate-this-application"></a>Creare un'applicazione "CalculateThis"
1. Aprire Visual Studio 2017 e quindi sulla barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.

2. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual Basic**, quindi selezionare **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Quindi assegnare al file il nome *CalculateThis*.  

3. Immettere il codice seguente tra la riga `Module Program` e la riga `End Module`:

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

  La finestra del codice dovrebbe avere un aspetto analogo allo screenshot seguente:

   ![Finestra del codice che mostra il codice di CalculateThis](../ide/media/vb-codewindow-calculate-this.png)

4. Fare clic su **CalculateThis** per eseguire il programma. La finestra della console dovrebbe avere un aspetto simile allo screenshot seguente:       

    ![Finestra della console che mostra l'app CalculateThis con le azioni possibili.](../ide/media/vb-console-calculate-this.png)

## <a name="next-steps"></a>Passaggi successivi
L'esercitazione è stata completata. Per altre informazioni su Visual Basic e sull'IDE di Visual Studio, vedere le pagine seguenti.

* [Guida a Visual Basic](/dotnet/visual-basic/index)
* [Novità di Visual Basic](/dotnet/visual-basic/getting-started/whats-new)
* [IntelliSense per i file di codice di Visual Basic](visual-basic-specific-intellisense.md)
* [Riferimenti per il linguaggio Visual Basic](/dotnet/visual-basic/language-reference/index)
* Esercitazione video [Visual Basic Fundamentals for Absolute Beginners](https://mva.microsoft.com/en-us/training-courses/visual-basic-fundamentals-for-absolute-beginners-16507) (Concetti di base su Visual Basic per principianti)
