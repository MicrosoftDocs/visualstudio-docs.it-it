---
title: Testing unità di codice Visual C# in Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: 32f76e3ebd6827ecb9ce0c27fa69b17a3da02f4e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="unit-testing-visual-c-code"></a>Testing unità di codice Visual C#

Questo argomento descrive come creare unit test per una classe Visual C# in un'app UWP. La classe Rooter rammenta vagamente la teoria dei limiti di calcolo implementando una funzione che calcola una stima della radice quadrata di un numero specificato. Nell'app Maths questa funzione può quindi essere utilizzata per illustrare all'utente le varie operazioni che si possono eseguire con questa funzione matematica.

In questo argomento viene illustrato come utilizzare unit test come primo passaggio dell'attività di sviluppo. Secondo questo approccio devi innanzitutto scrivere un metodo di test che verifica il comportamento specifico del sistema che stai testando, quindi scriverai il codice che supera il test. Apportando modifiche nell'ordine in cui sono presentate le procedure riportate di seguito, è possibile invertire questa strategia scrivendo prima il codice da testare e quindi gli unit test.

In questo argomento si creerà inoltre una soluzione di Visual Studio e progetti distinti per gli unit test e la DLL da testare. È anche possibile includere gli unit test direttamente nel progetto DLL oppure creare soluzioni separate per gli unit test e la DLL.

## <a name="create-the-solution-and-the-unit-test-project"></a>Creare la soluzione e il progetto unit test

1. Nel menu **File** scegliere **Nuovo** > **Progetto**.

2. Nella finestra di dialogo **Nuovo progetto** espandere **Installati** > **Visual C#** e quindi scegliere **Universale di Windows**. Scegliere quindi **App vuota** dall'elenco di modelli di progetto.

3. Assegnare al progetto il nome `Maths` e verificare che l'opzione **Crea directory per soluzione** sia selezionata.

4. In Esplora soluzioni selezionare il nome della soluzione, scegliere **Aggiungi** dal menu di scelta rapida e quindi **Nuovo progetto**.

5. Nella finestra di dialogo **Nuovo progetto** espandere **Installati**, **Visual C#** e quindi scegliere **Universale di Windows**. Scegli quindi **App unit test (Windows universale)** nell'elenco di modelli di progetto.

6. Aprire *UnitTest1.cs* nell'editor di Visual Studio.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using Maths;

   namespace RooterTests
   {
       [TestClass]
       public class UnitTest1

           [TestMethod]
           public void TestMethod1()
           {

           }
   ```

   Come si può notare:

   - Ogni test viene definito tramite l'attributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>. Un metodo di test deve restituire void e non può avere parametri.

   - I metodi di test devono appartenere a una classe decorata con l'attributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>.

        Quando si eseguono i test, viene creata un'istanza di ogni classe di test. I metodi di test vengono chiamati in un ordine non specificato.

   - È possibile definire metodi speciali che vengono richiamati prima e dopo ogni modulo, classe, o metodo. Per altre informazioni, vedere [Uso del framework MSTest negli unit test](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md).

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Verificare che i test siano eseguiti in Esplora test

1. Inserire codice di test in TestMethod1 nel file **UnitTest1.cs**:

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   Si noti che la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> fornisce diversi metodi statici che è possibile usare per verificare i risultati nei metodi di test.

2. Scegliere **Esegui** dal menu **Test**, quindi **Esegui tutto**.

   Il progetto di test viene compilato ed eseguito. Verrà visualizzata la finestra di Esplora test con il test elencato in **Test superati**. Nel riquadro di riepilogo nella parte inferiore della finestra sono disponibili ulteriori dettagli sul test selezionato.

   ![Esplora test](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="add-the-rooter-class-to-the-maths-project"></a>Aggiungere la classe Rooter al progetto Maths

1. In Esplora soluzioni selezionare il nome del progetto **Maths**. Scegliere **Aggiungi** dal menu di scelta rapida e quindi **Classe**.

2. Assegnare il nome *Rooter.cs* al file di classe.

3. Aggiungere il codice seguente al file *Rooter.cs* della classe Rooter:

   ```csharp
   public Rooter()
   {
   }

   // estimate the square root of a number
   public double SquareRoot(double x)
   {
       return 0.0;
   }
   ```

   La classe `Rooter` dichiara un costruttore e il metodo estimativo `SquareRoot`.

4. Il metodo `SquareRoot` è solo un'implementazione minima, sufficiente per testare la struttura di base della configurazione di test.

## <a name="couple-the-test-project-to-the-app-project"></a>Abbinare il progetto di test al progetto di app

1. Aggiungi un riferimento all'app Maths al progetto RooterTests.

    1. In Esplora soluzioni scegliere il progetto **RooterTests** e quindi **Aggiungi** dal menu di scelta rapida.

    2. Nella finestra di dialogo **Aggiungi riferimento - RooterTests** espandere **Soluzione** e scegliere **Progetti**. Selezionare quindi l'elemento **Maths**.

        ![Aggiungere un riferimento al progetto Maths](../test/media/ute_cs_windows_addreference.png)

2. Aggiungere un'istruzione using al file *UnitTest1.cs*:

    1. Aprire *UnitTest1.cs*.

    2. Aggiungi questo codice sotto la riga `using Microsoft.VisualStudio.TestTools.UnitTesting;`:

       ```csharp
       using Maths;
       ```

3. Aggiungi un test che utilizza la funzione Rooter. Aggiungere il codice seguente a *UnitTest1.cs*:

   ```csharp
   [TestMethod]
   public void BasicTest()
   {
       Maths.Rooter rooter = new Rooter();
       double expected = 0.0;
       double actual = rooter.SquareRoot(expected * expected);
       double tolerance = .001;
       Assert.AreEqual(expected, actual, tolerance);
   }
   ```

4. Compilare la soluzione.

   Il nuovo test viene visualizzato in Esplora test nel nodo **Test non eseguiti**.

5. In Esplora test scegliere **Esegui tutto**.

   ![Test di base superato](../test/media/ute_cpp_testexplorer_basictest.png)

È stato installato il test e i progetti di codice, e verificato che sia possibile eseguire test che eseguono funzioni nel progetto di codice. Ora è possibile iniziare a scrivere test e codici reali.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Aumentare i test in maniera iterativa e farli superare

1. Aggiungere un nuovo test:

   ```csharp
   [TestMethod]
   public void RangeTest()
   {
       Rooter rooter = new Rooter();
       for (double v = 1e-6; v < 1e6; v = v * 3.2)
       {
           double expected = v;
           double actual = rooter.SquareRoot(v*v);
           double tolerance = ToleranceHelper(expected);
           Assert.AreEqual(expected, actual, tolerance);
       }
   }
   ```

   > [!TIP]
   > È consigliabile non modificare i test che siano stati superati. Al contrario, aggiungere un nuovo test, aggiornare il codice in modo che il test passi e quindi aggiungere un altro test, e così via.
   >
   > Quando gli utenti modificano i requisiti, disabilitare i test che non sono più corretti. Scrivere nuovi test e farli funzionare uno alla volta, nello stesso modo incrementale.

2. In Esplora test scegliere **Esegui tutto**.

3. Il test ha esito negativo.

   ![RangeTest non riuscito](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Subito dopo averlo scritto, verifica che ogni test abbia esito negativo. Questo consente di evitare il semplice errore di scrivere un test che riesce sempre.

4. Modifica il codice sottoposto a test in modo che il nuovo test venga superato. Modificare la funzione `SquareRoot` in *Rooter.cs* nel modo seguente:

   ```csharp
   public double SquareRoot(double x)
   {
       double estimate = x;
       double diff = x;
       while (diff > estimate / 1000)
       {
           double previousEstimate = estimate;
           estimate = estimate - (estimate * estimate - x) / (2 * estimate);
           diff = Math.Abs(previousEstimate - estimate);
       }
       return estimate;
   }
   ```

5. Compilare la soluzione e quindi scegliere **Esegui tutto** in **Esplora test**.

   Ora tutti e tre i test vengono superati.

> [!TIP]
> Sviluppare il codice aggiungendo un test alla volta. Assicurarsi che tutti i test vengano superati dopo ogni iterazione.

## <a name="debug-a-failing-test"></a>Debug di un test non superato

1. Aggiungere un altro test a *UnitTest1.cpp*:

    ```csharp
    // Verify that negative inputs throw an exception.
    [TestMethod]
    public void NegativeRangeTest()
    {
        string message;
        Rooter rooter = new Rooter();
        for (double v = -0.1; v > -3.0; v = v - 0.5)
        {
            try
            {
                // Should raise an exception:
                double actual = rooter.SquareRoot(v);

                message = String.Format("No exception for input {0}", v);
                Assert.Fail(message);
            }
            catch (ArgumentOutOfRangeException ex)
            {
                continue; // Correct exception.
            }
            catch (Exception e)
            {
                message = String.Format("Incorrect exception for {0}", v);
                Assert.Fail(message);
            }
        }
    }
    ```

2. In **Esplora test** scegliere **Esegui tutto**.

   Il test ha esito negativo. Scegliere il nome del test in **Esplora test**. L'asserzione fallita viene evidenziata. Il messaggio di errore è visibile nel riquadro dei dettagli di **Esplora test**.

   ![NegativeRangeTests non riuscito](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Per capire perché il test non riesce, scorrere la funzione:

    1. Imposta un punto di interruzione all'inizio della funzione `SquareRoot`.

    2. Dal menu di scelta rapida del test non superato, scegliere **Esegui debug test selezionati**.

        Quando l'esecuzione si arresta in corrispondenza del punto di interruzione, eseguire il codice un'istruzione alla volta.

    3. Aggiungi codice al metodo Rooter per intercettare l'eccezione:

        ```csharp
        public double SquareRoot(double x)
        {
            if (x < 0.0)
            {
                throw new ArgumentOutOfRangeException();
        }
        ```

4. In Esplora test scegliere **Esegui tutto** per testare il metodo corretto e assicurarsi di non aver introdotto una regressione.

Tutti i test vengono ora superati.

![Tutti i test superati](../test/media/ute_ult_alltestspass.png)

## <a name="refactor-the-code"></a>Eseguire il refactoring del codice

**Semplificare il calcolo centrale nella funzione SquareRoot.**

1. Modifica l'implementazione del risultato

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Scegliere **Esegui tutto** per testare il metodo di cui è stato eseguito il refactoring e assicurarsi di non aver introdotto una regressione.

> [!TIP]
> Un set stabile di unit test corretti indica con sufficiente sicurezza che non sono stati introdotti bug in fase di modifica del codice.

**Eseguire il refactoring del codice di test per eliminare il codice duplicato.**

Si noti che il metodo `RangeTest` imposta come hardcoded il denominatore della variabile `tolerance` passata al metodo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>. Se prevedi di aggiungere altri test che utilizzano lo stesso calcolo di tolleranza, l'uso di un valore hardcoded in più posizioni potrebbe causare l'insorgere di errori.

1. Aggiungere un metodo private alla classe Unit1Test per calcolare il valore di tolleranza e quindi chiamare tale metodo.

    ```csharp
    private double ToleranceHelper(double expected)
    {
        return expected / 1000;
    }

    ...

    [TestMethod]
    public void RangeTest()
    {
        ...
        // old code
        // double tolerance = expected/1000;
        // new code
        double tolerance = ToleranceHelper(expected);
        Assert.AreEqual(expected, actual, tolerance);
    }
    ...
    ```

2. Scegliere **Esegui tutto** per testare il metodo di cui è stato eseguito il refactoring e assicurarsi di non aver introdotto un errore.

> [!NOTE]
> Se si aggiunge un metodo helper a una classe di test che non si vuole visualizzare in **Esplora test**, non aggiungere l'attributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> al metodo.