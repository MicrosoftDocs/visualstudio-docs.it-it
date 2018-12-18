---
title: "Guida introduttiva: Creare per la prima volta un'app console in Visual Studio con Visual Basic | Microsoft Docs"
ms.custom: ''
ms.date: 12/10/2017
ms.technology:
- vs-acquisition
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 39e7b9f03a5ef0a37594dad015084648eaa2bade
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Guida introduttiva: Creare per la prima volta un'app console in Visual Studio con Visual Basic
In questa introduzione di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio si creerà una semplice applicazione di Visual Basic che viene eseguita nella console.

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) per installarlo gratuitamente.

## <a name="create-a-project"></a>Creare un progetto
In primo luogo si creerà un progetto di applicazione Visual Basic. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

1. Aprire Visual Studio 2017.

2. Nella barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual Basic**, quindi selezionare **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Quindi assegnare al progetto il nome *HelloWorld*.

   ![Modello di progetto Console App (.NET Core) nella finestra di dialogo Nuovo progetto dell'IDE di Visual Studio](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Se non viene visualizzato il modello di progetto **Console App (.NET Core)** (App console (.NET Core)), fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**.

   ![Fare clic sul collegamento Apri il programma di installazione di Visual Studio nella finestra di dialogo Nuovo progetto](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

     ![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

## <a name="create-the-application"></a>Creare l'applicazione
Dopo la selezione del modello di progetto Visual Basic e l'assegnazione di un nome al progetto, in Visual Studio viene creata una semplice applicazione "Hello World". Chiama il metodo <xref:System.Console.WriteLine%2A> per visualizzare la stringa letterale "Hello World!" nella finestra della console.

![Visualizzare il codice Hello World predefinito dal modello](../ide/media/vb-console-helloworld-template.png)

Se si fa clic sul pulsante **HelloWorld** nell'IDE è possibile eseguire il programma in modalità debug.

  ![Fare clic sul pulsante HelloWorld per eseguire il programma in modalità debug](../ide/media/vb-console-hello-world-button.png)

Se si esegue questa operazione, la finestra della console resta visibile per un istante, quindi viene chiusa. Ciò accade perché il metodo `Main` termina dopo l'esecuzione dell'unica istruzione, quindi l'applicazione termina.

### <a name="add-some-code"></a>Aggiungere codice
Ora si aggiungerà del codice per sospendere l'applicazione e richiedere l'input dell'utente.

1. Aggiungere il codice seguente subito dopo la chiamata al metodo <xref:System.Console.WriteLine%2A>:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   Questo codice sospende l'esecuzione del programma fino a quando non si preme un tasto.

2. Nella barra dei menu selezionare **Compila** > **Compila soluzione**.

   Il programma viene compilato in un linguaggio intermedio (IL) che viene successivamente convertito in codice binario da un compilatore JIT (Just-In-Time).

## <a name="run-the-application"></a>Esecuzione dell'applicazione
1. Fare clic sul pulsante **HelloWorld** nella barra degli strumenti.

   ![Fare clic sul pulsante HelloWorld per eseguire il programma dalla barra degli strumenti](../ide/media/vb-console-hello-world-button.png)

2. Premere un tasto qualsiasi per chiudere la finestra della console.

   ![Finestra della console che visualizza Hello World e Premere un tasto qualsiasi per continuare](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Passaggi successivi
La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per l'apprendimento dell'uso di Visual Basic e dell'IDE di Visual Studio. Per altre informazioni, continuare con l'esercitazione seguente.

> [!div class="nextstepaction"]
> [Introduzione a Visual Basic in Visual Studio](tutorial-visual-basic-console.md)
