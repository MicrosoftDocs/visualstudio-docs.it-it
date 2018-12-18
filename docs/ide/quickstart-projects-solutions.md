---
title: Introduzione a progetti e soluzioni in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 12/11/2017
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 606b08608eea275a25a1a097ed75b7554a99f6a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="quickstart-projects-and-solutions"></a>Guida introduttiva: Progetti e soluzioni

Questa guida introduttiva di 10 minuti esamina che cosa significa creare una soluzione e un progetto in Visual Studio. Si esaminano le proprietà di un progetto e alcuni dei file che può contenere. Si crea anche un riferimento a un secondo progetto.

Se non è ancora stato installato Visual Studio, accedere alla pagina [Download di Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) per installarlo gratuitamente.

> [!TIP]
> In questa guida introduttiva la soluzione e il progetto vengono creati da zero, in un esercizio didattico che favorisce la comprensione del concetto di progetto. Nell'uso generico di Visual Studio è probabile che si usi uno dei numerosi modelli di progetto resi disponibili da Visual Studio per la creazione di un nuovo progetto.

> [!NOTE]
> Non è obbligatorio usare le soluzioni e i progetti per sviluppare app in Visual Studio. È anche possibile aprire semplicemente una cartella che contiene il codice e avviare la codifica, la compilazione e il debug. Se ad esempio si clona un repository di GitHub, è possibile che questo non contenga soluzioni e progetti di Visual Studio. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions"></a>Soluzioni

Le soluzioni sono contenitori usati da Visual Studio per organizzare uno o più progetti correlati. Quando in Visual Studio si apre una soluzione, vengono caricati automaticamente tutti i progetti contenuti nella soluzione.

### <a name="create-a-solution"></a>Creare una soluzione

Per iniziare si creerà una soluzione vuota. Una volta acquisita una conoscenza sufficiente di Visual Studio, la creazione di soluzioni vuote viene usata di rado. Quando si crea un nuovo progetto in Visual Studio, viene creata automaticamente una soluzione per ospitare il progetto, se non è presente una soluzione già aperta.

1. Avviare Visual Studio.

   Visual Studio si apre e la **Pagina iniziale** occupa la maggior parte dello spazio della finestra.

1. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.

   Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

1. Nel riquadro sinistro espandere **Altri tipi di progetti**, quindi scegliere **Soluzioni di Visual Studio**. Nel riquadro centrale scegliere **Soluzione vuota**. Assegnare alla soluzione il nome "QuickSolution", quindi scegliere **OK**.

   ![Modello di soluzione vuota](media/quickstart-projects-new-solution.png)

   La **Pagina iniziale** si chiude e viene visualizzata una soluzione in **Esplora soluzioni** sul lato destro della finestra di Visual Studio. **Esplora soluzioni** viene usato di frequente, per visualizzare il contenuto dei progetti.

### <a name="add-a-project"></a>Aggiungere un progetto

A questo punto si aggiunge il primo progetto alla soluzione. Si inizia con un progetto vuoto, quindi si aggiungono al progetto gli elementi necessari.

1. Nel menu di scelta rapida o nel menu a comparsa **Soluzione 'QuickSolution'** in **Esplora soluzioni** scegliere **Aggiungi** > **Nuovo progetto**.

   Verrà aperta la finestra di dialogo **Aggiungi nuovo progetto** .

1. Nel riquadro sinistro espandere **Visual C#** e scegliere **Desktop classico di Windows**. Nel riquadro centrale scegliere **Progetto vuoto (.NET Framework)**. Assegnare al progetto il nome "QuickDate" e scegliere **OK**.

   Il progetto "QuickDate" appare sotto la soluzione in **Esplora soluzioni**. Attualmente contiene un unico file con nome **App.config**.

   > [!NOTE]
   > Se **Visual C#** non viene visualizzato nel riquadro sinistro della finestra di dialogo, è necessario installare il carico di lavoro **Sviluppo per desktop .NET**. Per installarlo facilmente, scegliere il collegamento **Apri il programma di installazione di Visual Studio** nell'angolo in basso a sinistra della finestra di dialogo. Dopo l'avvio del **programma di installazione di Visual Studio**, scegliere il carico di lavoro **Sviluppo per desktop .NET** e quindi il pulsante **Modifica**.

   ![Collegamento Apri il programma di installazione di Visual Studio](media/quickstart-projects-open-installer.png)

## <a name="add-an-item-to-the-project"></a>Aggiungere un elemento al progetto

Il progetto è vuoto. Ora si aggiungerà un file di codice.

1. Nel menu di scelta rapida o nel menu a comparsa di **QuickDate** in **Esplora soluzioni** scegliere **Aggiungi** > **Nuovo elemento**.

   Viene aperta la finestra di dialogo **Aggiungi nuovo elemento**.

1. Espandere **Elementi di Visual C#**, quindi scegliere **Codice**. Nel riquadro centrale scegliere **Classe**. Assegnare il nome "Calendar" alla classe e scegliere il pulsante **Aggiungi**.

   Il file "Calendar.cs" viene aggiunto al progetto. Il valore **cs** finale è l'estensione del nome file assegnata ai file di codice C#. Il file appare nella gerarchia visuale del progetto in **Esplora soluzioni** e il suo contenuto viene aperto nell'editor.

1. Sostituire il contenuto del file **Calendar.cs** con il codice seguente.

   ```csharp
   using System;

   namespace QuickDate
   {
       internal class Calendar
       {
           static void Main(string[] args)
           {
               DateTime now = GetCurrentDate();
               Console.WriteLine($"Today's date is {now}");
               Console.ReadLine();
           }

           internal static DateTime GetCurrentDate()
           {
               return DateTime.Now.Date;
           }
       }
   }
   ```

   In questa fase non è necessario comprendere le operazioni eseguite dal codice. Se si vuole, è possibile eseguire il programma e verificare che visualizza la data corrente nella finestra della console.

## <a name="add-a-second-project"></a>Aggiungere un secondo progetto

Molto spesso le soluzioni contengono più di un progetto e spesso tali progetti includono riferimenti reciproci. Alcuni progetti di una soluzione possono essere librerie di classi, altri possono essere applicazioni eseguibili e altri ancora progetti unit test o siti Web.

Ora si aggiungerà un progetto unit test alla soluzione. Questa volta si inizierà con un modello di progetto, pertanto non sarà necessario inserire codice aggiuntivo nel progetto.

1. Nel menu di scelta rapida o nel menu a comparsa **Soluzione 'QuickSolution'** in **Esplora soluzioni** scegliere **Aggiungi** > **Nuovo progetto**.

   Verrà aperta la finestra di dialogo **Aggiungi nuovo progetto** .

1. Nel riquadro sinistro espandere **Visual Basic** e scegliere la categoria **Test**. Nel riquadro centrale scegliere **Progetto unit test (.NET Framework)**. Assegnare al progetto il nome "QuickTest" e scegliere il pulsante **OK**.

   Viene aggiunto un secondo progetto a **Esplora soluzioni** e nell'editor viene aperto un file con nome **UnitTest1.vb**. **vb** è l'estensione di nome file assegnata ai file di codice di Visual Basic.

   ![Esplora soluzioni con due progetti](media/quickstart-projects-solution-explorer.png)

## <a name="add-a-project-reference"></a>Aggiungere un riferimento al progetto

Il nuovo progetto unit test verrà utilizzato per il test del metodo nel progetto **QuickDate**, pertanto è necessario aggiungere un riferimento a tale progetto. Questa operazione crea una dipendenza di compilazione tra i due progetti: quando si crea la soluzione, il progetto **QuickDate** viene compilato prima di **QuickTest**.

1. Scegliere il nodo **Riferimenti** nel progetto **QuickTest**, quindi nel menu di scelta rapida o nel menu a comparsa scegliere **Aggiungi riferimento**.

   ![Menu Aggiungi riferimento](media/quickstart-projects-add-reference.png)

   Viene visualizzata la finestra di dialogo **Gestione riferimenti**.

1. Nel riquadro sinistro espandere **Progetti** e scegliere **Soluzione**. Nel riquadro centrale selezionare la casella di controllo accanto a **QuickDate** e quindi scegliere il pulsante **OK**.

   Viene aggiunto un riferimento al progetto **QuickDate**.

## <a name="add-test-code"></a>Aggiungere codice di test

1. Ora si aggiungerà codice di test al file di codice di Visual Basic. Sostituire il contenuto di **UnitTest1.vb** con il codice seguente.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Sotto alcune parti del codice viene visualizzata una linea rossa ondulata. Per risolvere l'errore si imposterà il progetto di test come [assembly Friend](/dotnet/csharp/programming-guide/concepts/assemblies-gac/friend-assemblies) del progetto **QuickDate**.

1. Tornare al progetto **QuickDate**, aprire il file **Calendar.cs** se non è già aperto e usare la seguente istruzione using e l'attributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> per risolvere l'errore nel progetto di test.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Il file di codice sarà simile al seguente.

   ![Codice CSharp](media/quickstart-projects-cs-code.png)

## <a name="project-properties"></a>Proprietà di progetti

La riga del file di codice C# contenente l'attributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> fa riferimento al nome assembly del progetto **QuickTest**. Il nome assembly può non corrispondere al nome del progetto. Per trovare il nome assembly di un progetto, aprire le proprietà del progetto.

1. In **Esplora soluzioni** selezionare il progetto **QuickTest**. Nel menu di scelta rapida o nel menu a comparsa selezionare **Proprietà** oppure premere semplicemente **ALT**+**INVIO**.

   Le pagine delle proprietà per il progetto vengono aperte nella scheda **Applicazione**. Si noti che il nome assembly del progetto **QuickTest** è di fatto "QuickTest". Se si vuole modificarlo, è necessario farlo qui. Se lo si modifica, quando si compila il progetto di test il nome del file eseguibile cambia da **QuickTest.exe** al nome scelto.

   ![Proprietà di progetti](media/quickstart-projects-properties.png)

1. Esplorare le altre schede delle pagine proprietà del progetto, quali **Compilazione** e **Impostazioni**. Le schede disponibili variano a seconda del tipo di progetto.

## <a name="next-steps"></a>Passaggi successivi

Per verificare che l'unit test funzioni scegliere **Test** > **Esegui** > **Tutti i test** nella barra dei menu. Viene visualizzata la finestra **Esplora test**. Verificare che venga superato il testo **TestGetCurrentDate**.

La guida introduttiva è stata completata. Ora può risultare utile vedere altre guide introduttive di Visual Studio o ottenere altre informazioni sulla [creazione di progetti e soluzioni](../ide/creating-solutions-and-projects.md).

## <a name="see-also"></a>Vedere anche

- [Guida introduttiva: Presentazione dell'IDE di Visual Studio](../ide/quickstart-ide-orientation.md)
- [Guida introduttiva: Personalizzare l'IDE e l'editor di Visual Studio](../ide/quickstart-personalize-the-ide.md)
- [Guida introduttiva: Scrittura di codice nell'editor](../ide/quickstart-editor.md)
- [Gestione delle proprietà di progetti e soluzioni](../ide/managing-project-and-solution-properties.md)
- [Gestione dei riferimenti in un progetto](../ide/managing-references-in-a-project.md)
- [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Panoramica dell'IDE di Visual Studio](../ide/visual-studio-ide.md)
