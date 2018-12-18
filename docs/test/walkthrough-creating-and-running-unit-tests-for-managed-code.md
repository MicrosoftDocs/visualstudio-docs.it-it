---
title: 'Procedura dettagliata: Creazione ed esecuzione di unit test per codice gestito in Visual Studio | Microsoft Docs'
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: a34fded72a0d04f3920e0d7a76f9550993b520e7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Procedura dettagliata: Creare ed eseguire unit test per codice gestito

Questa procedura dettagliata illustra come creare, eseguire e personalizzare una serie di unit test usando il framework di unit test di Microsoft per il codice gestito ed Esplora test di Visual Studio. Verrà illustrato prima di tutto il progetto C# in fase di sviluppo, quindi saranno creati i test in cui verrà usato il codice e saranno esaminati i risultati. Sarà infine possibile modificare il codice del progetto ed eseguire nuovamente i test.

 Di seguito sono elencate le diverse sezioni di questo argomento:

 [Preparare la procedura dettagliata](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough)

 [Creare un progetto di unit test](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_a_unit_test_project)

 [Creare la classe di test](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_test_class)

-   [Requisiti della classe di test](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_class_requirements)

 [Creare il primo metodo di test](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_first_test_method)

-   [Requisiti del metodo di test](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_method_requirements)

 [Compilare ed eseguire il test](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Build_and_run_the_test)

 [Correggere il codice e rieseguire i test](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Fix_your_code_and_rerun_your_tests)

 [Usare gli unit test per migliorare il codice](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Use_unit_tests_to_improve_your_code)

> [!NOTE]
>  Questa procedura dettagliata usa il framework di unit test di Microsoft per il codice gestito. Esplora test consente anche di eseguire test da framework di unit test di terze parti provvisti di adapter per Esplora test. Per altre informazioni, vedere [Installare framework di unit test di terze parti](../test/install-third-party-unit-test-frameworks.md)

> [!NOTE]
>  Per informazioni su come eseguire i test dalla riga di comando, vedere [Procedura dettagliata: Uso dell'utilità di test della riga di comando](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867).

## <a name="prerequisites"></a>Prerequisiti

-   Il progetto Bank. Vedere [Progetto di esempio per la creazione di unit test](../test/sample-project-for-creating-unit-tests.md).

##  <a name="BKMK_Prepare_the_walkthrough"></a> Preparare la procedura dettagliata

1.  Aprire Visual Studio.

2.  Scegliere **Nuovo** dal menu **File** , quindi scegliere **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3.  In **Modelli installati**fare clic su **Visual C#**.

4.  Nell'elenco di tipi di applicazione fare clic su **Libreria di classi**.

5.  Digitare **Bank** nella casella `Bank` , quindi scegliere **OK**.

    > [!NOTE]
    > Se il nome "Bank" è stato già usato, scegliere un altro nome per il progetto.

     Viene creato nuovo progetto Bank, visualizzato in Esplora soluzioni con il file Class1.cs aperto nell'Editor di codice.

    > [!NOTE]
    > Per aprire il file Class1.cs nell'Editor di codice, nel caso non fosse aperto, fare doppio clic sul file stesso in Esplora soluzioni.

6.  Copiare il codice sorgente dal [progetto di esempio per la creazione di unit test](../test/sample-project-for-creating-unit-tests.md).

7.  Sostituire il contenuto originale di Class1.cs con il codice del [progetto di esempio per la creazione di unit test](../test/sample-project-for-creating-unit-tests.md).

8.  Salvare il file come BankAccount.cs

9. Scegliere **Compila soluzione** dal menu **Compila**.

 A questo punto è disponibile un progetto denominato Bank che contiene il codice sorgente da testare e gli strumenti da usare a questo scopo. Nello spazio dei nomi per Bank, **BankAccountNS**, è presente la classe pubblica **BankAccount**, i cui metodi saranno testati nelle routine seguenti.

 In questa guida introduttiva viene illustrato soprattutto il metodo `Debit` . Il metodo Debit viene chiamato quando si preleva denaro da un conto e contiene il codice seguente:

```csharp
// method under test
public void Debit(double amount)
{
    if(amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    m_balance += amount;
}
```

##  <a name="BKMK_Create_a_unit_test_project"></a> Creare un progetto di unit test
 **Prerequisito**: seguire la routine [Prepare the walkthrough](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough).

### <a name="to-create-a-unit-test-project"></a>Per creare un progetto di unit test

1.  Scegliere **Aggiungi** dal menu **File**, quindi **Nuovo progetto**.

2.  Nella finestra di dialogo Nuovo progetto espandere **Installato**, **Visual C#**, quindi scegliere **Test**.

3.  Nell'elenco dei modelli selezionare **Progetto unit test**.

4.  Nella casella **Nome** immettere BankTest, quindi scegliere **OK**.

     Il progetto **BankTests** verrà aggiunto alla soluzione **Bank** .

5.  Nel progetto **BankTests** aggiungere un riferimento alla soluzione **Bank** .

     In Esplora soluzioni selezionare **Riferimenti** nel progetto **BankTests** , quindi scegliere **Aggiungi riferimento** dal menu di scelta rapida.

6.  Nella finestra di dialogo Gestione riferimenti espandere **Soluzione** , quindi selezionare l'elemento **Bank** .

##  <a name="BKMK_Create_the_test_class"></a> Creare la classe di test
 È necessaria una classe di test per verificare la classe `BankAccount` . È possibile usare UnitTest1.cs generato dal modello del progetto, ma è necessario fornire nomi più descrittivi per il file e la classe. È possibile eseguire questa operazione in un unico passaggio rinominando il file in Esplora soluzioni.

 **Ridenominazione di un file di classe**

 In Esplora soluzioni selezionare il file UnitTest1.cs nel progetto BankTests. Dal menu di scelta rapida scegliere **Rinomina**, quindi rinominare il file assegnandogli il nome BankAccountTests.cs. Scegliere **Sì** nella finestra di dialogo in cui viene chiesto se rinominare tutti i riferimenti del progetto all'elemento di codice 'UnitTest1'. Questo passaggio cambia il nome della classe in `BankAccountTest`.

 Il file BankAccountTests.cs contiene ora il codice seguente:

```csharp
// unit test code
using System;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace BankTests
{
    [TestClass]
    public class BankAccountTests
    {
        [TestMethod]
        public void TestMethod1()
        {
        }
    }
}
```

 **Aggiungere un'istruzione using al progetto sottoposto a test**

 È anche possibile aggiungere un'istruzione using alla classe per consentire di effettuare chiamate nel progetto sottoposto a test senza usare nomi completi. All'inizio del file di classe aggiungere:

```csharp
using BankAccountNS;
```

###  <a name="BKMK_Test_class_requirements"></a> Requisiti della classe di test
 I requisiti minimi per una classe di test sono i seguenti:

-   L'attributo `[TestClass]` è obbligatorio nel framework per unit test di Microsoft per il codice gestito per qualsiasi classe che contiene metodi di unit test che si desidera eseguire in Esplora test.

-   Ogni metodo di test che si desidera eseguire in Esplora test deve avere l'attributo `[TestMethod]`.

 È possibile avere altre classi in un progetto di unit test che non presentano l'attributo `[TestClass]` ed è possibile avere altri metodi nelle classi di test che non presentano l'attributo `[TestMethod]` . È possibile usare questi altri metodi e classi nei metodi di test.

##  <a name="BKMK_Create_the_first_test_method"></a> Creare il primo metodo di test
 In questa routine viene illustrato come scrivere i metodi di unit test per verificare il comportamento del metodo `Debit` della classe `BankAccount` . Il metodo è elencato sopra.

 Analizzando il metodo sottoposto a test, si determina che esistono almeno tre comportamenti che devono essere controllati:

1.  Il metodo genera un oggetto <xref:System.ArgumentOutOfRangeException> se la quantità di debito è superiore al saldo.

2.  Genera `ArgumentOutOfRangeException` anche se la quantità di debito è minore di zero.

3.  Se i controlli in 1.) e in 2.) vengono superati, il metodo sottrae l'importo dal saldo del conto.

 Nel primo test si verifica che un importo valido (uno che sia minore del saldo del conto e che sia maggiore di zero) prelevi l'importo corretto dal conto.

### <a name="to-create-a-test-method"></a>Per creare un metodo di test

1.  Aggiungere un'istruzione using `BankAccountNS;` al file BankAccountTests.cs.

2.  Aggiungere il metodo seguente alla classe `BankAccountTests` :

    ```csharp
    // unit test code
    [TestMethod]
    public void Debit_WithValidAmount_UpdatesBalance()
    {
        // arrange
        double beginningBalance = 11.99;
        double debitAmount = 4.55;
        double expected = 7.44;
        BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

        // act
        account.Debit(debitAmount);

        // assert
        double actual = account.Balance;
        Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
    }
    ```

 Il metodo è piuttosto semplice. Verrà configurato un nuovo oggetto `BankAccount` con un saldo iniziale e quindi verrà prelevato un importo valido. Verrà usato il framework di unit test di Microsoft per il codice gestito dal metodo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> per verificare che il saldo finale sia quello previsto.

###  <a name="BKMK_Test_method_requirements"></a> Requisiti del metodo di test
 Un metodo di test deve soddisfare i seguenti requisiti:

-   Il metodo deve essere provvisto dell'attributo `[TestMethod]` .

-   Il metodo deve restituire `void`.

-   Il metodo non può avere parametri.

##  <a name="BKMK_Build_and_run_the_test"></a> Compilare ed eseguire il test

### <a name="to-build-and-run-the-test"></a>Per compilare ed eseguire il test

1.  Scegliere **Compila soluzione** dal menu **Compila**.

     Se non sono presenti errori, la finestra di UnitTestExplorer viene visualizzata con **Debit_WithValidAmount_UpdatesBalance** visualizzato nel gruppo **Test non eseguiti** . Se Esplora test non viene visualizzato al termine di una compilazione corretta, scegliere **Test** dal menu, quindi scegliere **Windows**e infine  **Esplora test**.

2.  Scegliere **Esegui tutto** per eseguire il test. Mentre il test è in esecuzione, la barra di stato nella parte superiore della finestra viene animata. Al termine del test, la barra diventa verde se tutti i metodi di test vengono superati oppure rossa se almeno uno dei test ha esito negativo.

3.  In questo caso, il test non riesce. Il metodo di test viene spostato nel gruppo **Test non superati** . Selezionare il metodo in Esplora test per visualizzare i dettagli nella parte inferiore della finestra.

##  <a name="BKMK_Fix_your_code_and_rerun_your_tests"></a> Correggere il codice e rieseguire i test
 **Analizzare i risultati dei test**

 Il risultato del test contiene un messaggio che descrive l'errore. Per il metodo `AreEquals`, il messaggio visualizza il contenuto previsto (il parametro (**\<*XXX*>** previsto) e ciò che è stato ricevuto (il parametro **\<*YYY*>** effettivo). Si prevedeva che il saldo venisse detratto dal saldo iniziale, ma è stato invece aumentato dell'importo del prelievo.

 Il riesame del codice di Debit mostra che lo unit test ha trovato un bug. La quantità da ritirare viene aggiunta al saldo del conto quando dovrebbe essere sottratta.

 **Correggere il bug**

 Per correggere l'errore, sostituire semplicemente la riga

```csharp
m_balance += amount;
```

 con

```csharp
m_balance -= amount;
```

 **Eseguire nuovamente il test**

 In Esplora test scegliere **Esegui tutto** per rieseguire il test. La barra verde/rossa diventa verde e il test viene spostato nel gruppo **Test superati** .

##  <a name="BKMK_Use_unit_tests_to_improve_your_code"></a> Usare gli unit test per migliorare il codice
 In questa sezione viene descritto come un processo iterativo di analisi, di sviluppo di unit test e di refactoring può aiutare a rendere il codice di produzione più affidabile ed efficace.

 **Analizzare i problemi**

 Dopo aver creato un metodo di test per confermare che un importo valido è stato correttamente detratto nel metodo `Debit` , è possibile tornare ai casi rimanenti nell'analisi originale:

1.  Il metodo genera un oggetto `ArgumentOutOfRangeException` se la quantità di debito è superiore al saldo.

2.  Genera `ArgumentOutOfRangeException` anche se la quantità di debito è minore di zero.

 **Creare i metodi di test**

 Un primo tentativo di creare un metodo di test per risolvere questi problemi sembra promettente:

```csharp
//unit test method
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    account.Debit(debitAmount);

    // assert is handled by ExpectedException
}
```

 Verrà usato l'attributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> per confermare che è stata generata l'eccezione appropriata. L'attributo causa l'esito negativo del test a meno che non venga generata un'eccezione `ArgumentOutOfRangeException` . L'esecuzione del test con valori sia positivi che negativi di `debitAmount` e la modifica temporanea del metodo sottoposto a test per generare una <xref:System.ApplicationException> generica quando la quantità è inferiore a zero indicano che il test funziona correttamente. Per eseguire il test del caso in cui l'importo prelevato è maggiore del saldo, è sufficiente seguire questa procedura:

1.  Creare un nuovo metodo di test denominato `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.

2.  Copiare il corpo del metodo da `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` nel nuovo metodo.

3.  Impostare `debitAmount` su un numero maggiore del saldo.

 **Eseguire i test**

 L'esecuzione di due metodi con valori diversi per `debitAmount` dimostra che i test gestiscono in modo adeguato i casi rimanenti. L'esecuzione di tutti e tre i test conferma che tutti i casi nell'analisi originale sono correttamente coperti.

 **Continuare l'analisi**

 Tuttavia, gli ultimi due metodi di test presentano alcuni problemi. Non è possibile essere certi di quale condizione nel codice sottoposto a test generi l'eccezione quando entrambi i test sono in esecuzione. Potrebbero essere utili alcuni modi per differenziare le due condizioni. Conoscere quale condizione è stata violata potrebbe far aumentare la fiducia nei test. Queste informazioni sono anche utili al meccanismo di produzione che gestisce l'eccezione quando viene generata dal metodo sottoposto al test. La creazione di maggiori informazioni quando il metodo genera eccezioni sarebbe di aiuto, ma l'attributo `ExpectedException` non può generarle.

 Analizzando di nuovo il metodo sottoposto a test, si nota che entrambe le istruzioni condizionali usano un costruttore `ArgumentOutOfRangeException` che assume il nome dell'argomento come parametro:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

 Da una ricerca nella MSDN Library si scopre che esiste un costruttore che fornisce informazioni molto più dettagliate. <xref:System.ArgumentOutOfRangeException.%23ctor%2A>`(String, Object, String)` include il nome dell'argomento, il valore dell'argomento e un messaggio definito dall'utente. È possibile effettuare il refactoring del metodo sottoposto al test per usare questo costruttore. Ancor meglio, è possibile usare membri di tipo pubblico per specificare gli errori.

 **Effettuare il refactoring del codice sottoposto a test**

 Innanzitutto è necessario definire due costanti per i messaggi di errore nell'ambito di classe:

```csharp
// class under test
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount less than zero";
```

 Quindi si modificano le due istruzioni condizionali nel metodo `Debit` :

```csharp
// method under test
// ...
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
// ...
```

 **Eseguire il refactoring dei metodi di test**

 Nel metodo di test prima si rimuove l'attributo `ExpectedException` . Al suo posto, si rileva l'eccezione generata e si verifica che sia stata generata nell'istruzione della condizione corretta. Tuttavia, è ora necessario scegliere tra due opzioni per verificare le condizioni rimanenti. Ad esempio, nel metodo `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` è possibile effettuare una delle azioni seguenti:

-   Confermare che la proprietà `ActualValue` dell'eccezione (il secondo parametro del costruttore `ArgumentOutOfRangeException` ) è maggiore del saldo iniziale. Questa opzione richiede il test della proprietà `ActualValue` dell'eccezione con la variabile `beginningBalance` del metodo di test e richiede quindi di verificare che `ActualValue` sia maggiore di zero.

-   Confermare che il messaggio (il terzo parametro del costruttore) include l'oggetto `DebitAmountExceedsBalanceMessage` definito nella classe `BankAccount` .

 Il metodo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> nel framework per unit test di Microsoft consente di verificare la seconda opzione senza i calcoli richiesti per la prima opzione.

 Un secondo tentativo di rivedere `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` potrebbe essere simile al seguente:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // assert
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);
    }
}
```

 **Rieseguire il test, riscrivere e rianalizzare**

 Quando vengono eseguiti nuovamente metodi di test con valori differenti, si verifica la situazione seguente:

1.  Se si intercetta l'errore corretto usando un'asserzione in cui `debitAmount` è superiore al saldo, l'asserzione `Contains` viene passata, l'eccezione viene ignorata, quindi viene passato anche il metodo. Questo è il comportamento desiderato.

2.  Se `debitAmount` è minore di 0, l'asserzione ha esito negativo perché viene restituito il messaggio di errore errato. L'asserzione ha esito negativo anche se si introduce un'eccezione temporanea `ArgumentOutOfRange` in un altro punto nel metodo sotto il percorso del codice di test. Anche questo va bene.

3.  Se il valore `debitAmount` è valido, ad esempio minore del saldo ma maggiore di zero, non sarà intercettata alcuna eccezione e quindi non verrà mai intercettata neanche l'asserzione. Il metodo di test passa. Questo non va bene perché si desidera che il metodo di test non riesca se non viene generata alcuna eccezione.

 Il terzo fatto è un bug nel metodo di test. Per cercare di risolvere il problema, viene aggiunta un'asserzione <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> alla fine del metodo di test per gestire il caso se non viene generata alcuna eccezione.

 Ma una nuova esecuzione mostra che a questo punto il test ha esito negativo se viene rilevata l'eccezione corretta. L'istruzione catch reimposta l'eccezione e il metodo continua a essere eseguito, ma non viene eseguito correttamente alla nuova asserzione. Per risolvere il nuovo problema, è necessario aggiungere un'istruzione `return` dopo `StringAssert`. La riesecuzione del test conferma che sono stati corretti i problemi. La versione finale di `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` sarà simile alla seguente:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // assert
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);
        return;
    }
    Assert.Fail("No exception was thrown.");
}
```

In questa sezione finale, le operazioni eseguite per migliorare il codice di test hanno portato a metodi di test più affidabili e informativi. Soprattutto, l'analisi aggiuntiva ha anche condotto a un codice migliore nel progetto sottoposto a test.
