---
title: Informazioni su come testare il codice con Live Unit Testing in Visual Studio 2017 | Microsoft Docs
ms.date: 08/31/2017
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: bd2bc43081418844f03b5cb58af46f6888d57652
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="get-started-with-live-unit-testing-in-visual-studio"></a>Introduzione a Live Unit Testing in Visual Studio

Quando in una soluzione Visual Studio viene abilitato Live Unit Testing, il code coverage e lo stato del test vengono visualizzati mediante una colorazione. I test vengono eseguiti in modo dinamico ogni volta in cui il codice viene modificato. Viene generata una notifica ogni volta in cui le modifiche hanno interrotto il codice e vengono indicate le aree in cui è necessario eseguire test aggiuntivi.

Live Unit Testing può essere usato per testare soluzioni che hanno come destinazione .NET Framework o .NET Core. In questa esercitazione verrà illustrato come usare Live Unit Testing tramite la creazione di una libreria di classi semplice che ha come destinazione .NET Standard e la creazione di un progetto di MSTest che ha come destinazione .NET Core per l'esecuzione del test.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
La soluzione C# completa può essere scaricata dal repository [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) in GitHub.
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
La soluzione Visual Basic completa può essere scaricata dal repository [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/visual-basic/UtilityLibraries/) in GitHub.

---

## <a name="prerequisites"></a>Prerequisiti

L'esercitazione richiede Visual Studio 2017 Enterprise Edition versione 15.3 con il carico di lavoro .NET Core 2.0.

## <a name="create-the-solution-and-the-class-library-project"></a>Creare la soluzione e il progetto di libreria di classi

Iniziare creando una soluzione di Visual Studio denominata `UtilityLibraries` costituita da un progetto di libreria di classi di .NET Standard singolo, `StringLibrary`. È possibile scrivere `StringLibrary` in C# o in Visual Basic.

La soluzione è semplicemente un contenitore per uno o più progetti. Per creare la soluzione, aprire Visual Studio 2017 ed eseguire le operazioni seguenti:

1. Selezionare **File**, **Nuovo**, **Progetto** dal menu di primo livello di Visual Studio.

1. Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Altri tipi di progetti** e selezionare **Soluzioni di Visual Studio**. Selezionare il modello **Soluzione vuota** nel riquadro di destra e immettere `UtilityLibraries` nella casella di testo **Nome**, come illustrato nella figura seguente:

   ![Finestra di dialogo Nuovo progetto](./media/lut-start/new-solution.png)

1. Fare clic su **OK** per creare la soluzione.

Dopo aver creato la soluzione, creare una libreria di classi denominata `StringLibrary` contenente metodi di estensione per l'uso di stringhe.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione `UtilityLibraries` e selezionare **Aggiungi**, **Nuovo progetto**.

1. Nella finestra di dialogo **Aggiungi nuovo progetto** selezionare il nodo C# e quindi **.NET Standard**.

   > [!NOTE]
   > Poiché la libreria ha come destinazione .NET Standard invece di una particolare implementazione di .NET, può essere chiamata da qualsiasi implementazione di .NET che supporti la versione di .NET Standard. Per altre informazioni, vedere [.NET Standard](/dotnet/standard/net-standard).

1. Selezionare il modello **Class Library (.NET Standard)** (Libreria di classi (.NET Standard)) nel riquadro di destra e immettere `StringLibrary` nella casella di testo **Nome**, come illustrato nella figura seguente:

   ![Finestra di dialogo Aggiungi nuovo progetto](./media/lut-start/add-project-cs.png)

1. Selezionare **OK** per creare il progetto.

1. Nella finestra del codice sostituire il codice esistente con il seguente:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   `StringLibrary` ha tre metodi statici:

      - `StartsWithUpper` restituisce `true` se una stringa inizia con una lettera maiuscola; in caso contrario, restituisce `false`.

      - `StartsWithLower` restituisce `true` se una stringa inizia con una lettera minuscola; in caso contrario, restituisce `false`.

      - `HasEmbeddedSpaces` restituisce `true` se una stringa include uno spazio vuoto; in caso contrario, restituisce `false`.

1.  Selezionare **Compila**, **Compila soluzione** dal menu di primo livello di Visual Studio. La compilazione della libreria da parte di Visual Studio dovrebbe avvenire correttamente.

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione `UtilityLibraries` e selezionare **Aggiungi**, **Nuovo progetto**.

1. Nella finestra di dialogo **Aggiungi nuovo progetto** selezionare il nodo Visual Basic e quindi **.NET Standard**.

   > [!NOTE]
   > Poiché la libreria ha come destinazione .NET Standard invece di una particolare implementazione di .NET, può essere chiamata da qualsiasi implementazione di .NET che supporti la versione di .NET Standard. Per altre informazioni, vedere [.NET Standard](/dotnet/standard/net-standard).

1. Selezionare il modello **Class Library (.NET Standard)** (Libreria di classi (.NET Standard)) nel riquadro di destra e immettere `StringLibrary` nella casella di testo **Nome**, come illustrato nella figura seguente:

   ![Finestra di dialogo Aggiungi nuovo progetto](./media/lut-start/add-project-vb.png)

1. Selezionare **OK** per creare il progetto.

1. Nella finestra del codice sostituire il codice esistente con il seguente:

   [!code-vb[StringLibrary source code](samples/visual-basic/utilitylibraries/stringlibrary/class1.vb)]

   `StringLibrary` ha tre metodi statici:

      - `StartsWithUpper` restituisce `true` se una stringa inizia con una lettera maiuscola; in caso contrario, restituisce `false`.

      - `StartsWithLower` restituisce `true` se una stringa inizia con una lettera minuscola; in caso contrario, restituisce `false`.

      - `HasEmbeddedSpaces` restituisce `true` se una stringa include uno spazio vuoto; in caso contrario, restituisce `false`.

1. Fare clic con il pulsante destro del mouse nel progetto StringLibrary in **Esplora soluzioni** e selezionare **Proprietà**. Nella scheda **Applicazione** eliminare il testo nella casella di testo **Spazio dei nomi radice**, come illustrato nella figura seguente. Lo spazio dei nomi radice è definito dall'[istruzione Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement) nel codice sorgente.

   ![Finestra di dialogo Proprietà del progetto per un progetto di Visual Basic](./media/lut-start/vb-properties.png)

1.  Selezionare **Compila**, **Compila soluzione** dal menu di primo livello di Visual Studio. La compilazione della libreria da parte di Visual Studio dovrebbe avvenire correttamente.

---

## <a name="create-the-test-project"></a>Creare il progetto di test

Il passaggio successivo consiste nel creare il progetto di unit test per testare la libreria `StringLibrary`. Creare gli unit test eseguendo i passaggi seguenti:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione `UtilityLibraries` e selezionare **Aggiungi**, **Nuovo progetto**.

1. Nella finestra di dialogo **Aggiungi nuovo progetto** selezionare il nodo C# e quindi **.NET Core**.

   > [!NOTE]
   > Non è necessario scrivere gli unit test nello stesso linguaggio della libreria di classi.

1. Selezionare il modello **Progetto Unit Test (.NET Core)** nel riquadro di destra e immettere `StringLibraryTests` nella casella di testo **Nome**, come illustrato nella figura seguente:

   ![Finestra di dialogo Aggiungi nuovo progetto per il progetto di unit test](./media/lut-start/add-unit-test-cs.png)

1. Selezionare **OK** per creare il progetto.

   > [!NOTE]
   > Questa esercitazione introduttiva usa Live Unit Testing con il framework di test MSTest. È possibile usare anche i framework di test xUnit e NUnit.

1. Il progetto di unit test non può accedere automaticamente alla libreria di classi di cui sta eseguendo il test. L'accesso alla libreria di test viene garantito tramite l'aggiunta di un riferimento al progetto della libreria di classi. A questo scopo, fare clic con il pulsante destro del mouse sul progetto `StringLibraryTests` e selezionare **Aggiungi**, **Riferimento**. Nella finestra di dialogo **Gestione riferimenti** assicurarsi che la scheda **Soluzione** sia selezionata e selezionare il progetto `StringLibrary`, come illustrato nella figura seguente.

   ![Finestra di dialogo Gestione riferimenti](./media/lut-start/add-reference.png)

1. Sostituire il codice di unit test boilerplate specificato dal modello con il codice seguente:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

1. Salvare il progetto selezionando l'icona **Salva** sulla barra degli strumenti.

1. Poiché il codice unit test include alcuni caratteri non ASCII, Visual Studio visualizza la finestra di dialogo seguente per informare che alcuni caratteri andranno persi se si salva il file nel relativo formato ASCII predefinito. Scegliere il pulsante **Salva con altra codifica**.

   ![Scegliere una codifica di file](media/lut-start/ascii-encoding.png)

1. Dall'elenco a discesa **Codifica** disponibile nella finestra di dialogo **Opzioni di salvataggio avanzate** selezionare **Unicode (UTF-8 senza firma digitale) - Tabella codici 65001**, come illustrato nella figura seguente:

   ![Scelta della codifica UTF-8](media/lut-start/utf8-encoding.png)

1. Compilare il progetto di unit test da **Compila**, **Ricompila soluzione** dal menu di primo livello di Visual Studio.

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione `UtilityLibraries` e selezionare **Aggiungi**, **Nuovo progetto**.

1. Nella finestra di dialogo **Aggiungi nuovo progetto** selezionare il nodo Visual Basic e quindi **.NET Core**.

   > [!NOTE]
   > Non è necessario scrivere gli unit test nello stesso linguaggio della libreria di classi.

1. Selezionare il modello **Progetto Unit Test (.NET Core)** nel riquadro di destra e immettere `StringLibraryTests` nella casella di testo **Nome**, come illustrato nella figura seguente:

   ![Finestra di dialogo Aggiungi nuovo progetto per unit test](./media/lut-start/add-unit-test-vb.png)

1. Selezionare **OK** per creare il progetto.

   > [!NOTE]
   > Questa esercitazione introduttiva usa Live Unit Testing con il framework di test MSTest. È possibile usare anche i framework di test xUnit e NUnit.

1. Il progetto di unit test non può accedere automaticamente alla libreria di classi di cui sta eseguendo il test. L'accesso alla libreria di test viene garantito tramite l'aggiunta di un riferimento al progetto della libreria di classi. A questo scopo, fare clic con il pulsante destro del mouse sul progetto `StringLibraryTests` e selezionare **Aggiungi**, **Riferimento**. Nella finestra di dialogo **Gestione riferimenti** assicurarsi che la scheda **Soluzione** sia selezionata e selezionare il progetto `StringLibrary`, come illustrato nella figura seguente.

   ![Finestra di dialogo Gestione riferimenti](./media/lut-start/add-reference.png)

1. Sostituire il codice di unit test boilerplate specificato dal modello con il codice seguente:

   [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest1.vb)]

1. Salvare il progetto selezionando l'icona **Salva** sulla barra degli strumenti.

1. Poiché il codice unit test include alcuni caratteri non ASCII, Visual Studio visualizza la finestra di dialogo seguente per informare che alcuni caratteri andranno persi se si salva il file nel relativo formato ASCII predefinito. Scegliere il pulsante **Salva con altra codifica**.

   ![Scegliere una codifica di file](media/lut-start/ascii-encoding.png)

1. Dall'elenco a discesa **Codifica** disponibile nella finestra di dialogo **Opzioni di salvataggio avanzate** selezionare **Unicode (UTF-8 senza firma digitale) - Tabella codici 65001**, come illustrato nella figura seguente:

   ![Scelta della codifica UTF-8](media/lut-start/utf8-encoding.png)

1. Compilare il progetto di unit test da **Compila**, **Ricompila soluzione** dal menu di primo livello di Visual Studio.

---

Sono stati creati una libreria di classi e i relativi unit test. Le operazioni preliminari per usare Live Unit Testing sono state completate.

## <a name="enable-live-unit-testing"></a>Abilitare Live Unit Testing

Finora i test per la libreria di classi `StringLibrary` sono stati scritti ma non eseguiti. Una volta abilitato, Live Unit Testing li esegue automaticamente. A tal scopo, eseguire le operazioni seguenti:

1. Facoltativamente, selezionare la finestra di codice che contiene il codice per `StringLibrary`. Si tratta di class1.cs per un progetto C# o di Class1.vb per un progetto di Visual Basic. Questo passaggio consente di controllare visivamente il risultato dei test e la portata del code coverage dopo aver abilitato Live Unit Testing.

1. Selezionare **Test**, **Live Unit Testing**, **Avvia** dal menu di primo livello di Visual Studio.

1. Visual Studio avvia Live Unit Testing, che esegue automaticamente tutti i test.

Al termine dell'esecuzione dei test, in **Esplora test** vengono visualizzati i risultati complessivi e i risultati dei test singoli. Nella finestra del codice vengono anche visualizzati graficamente il code coverage del test e il risultato per i test. Come illustrato nella figura seguente, tutti e tre i test sono stati eseguiti correttamente. Viene anche illustrato che i test hanno coperto tutti i percorsi nel metodo `StartsWithUpper` e che tutti i test sono stati eseguiti correttamente. Ciò è indicato dal segno di spunta verde, "✓". Infine, viene illustrato che nessuno degli altri metodi in `StringLibrary` ha un code coverage, indicato da una linea blu, "➖".

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![Finestra Esplora test e finestra di codice dopo l'avvio di Live Unit Testing](media/lut-start/lut-results-cs.png)

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
![Finestra Esplora test e finestra di codice dopo l'avvio di Live Unit Testing](media/lut-start/lut-results-vb.png)

---

È anche possibile ottenere informazioni più dettagliate sulla copertura e sui risultati dei test selezionando un'icona di code coverage specifica nella finestra del codice. Per esaminare il dettaglio, eseguire le operazioni seguenti:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Fare clic sul segno di spunta verde nella riga che include `if (String.IsNullOrWhiteSpace(s))` nel metodo `StartsWithUpper`. Come illustrato nella figura seguente, Live Unit Testing indica che tre test coprono la riga di codice e che tutti e tre sono stati eseguiti correttamente.

   ![Code coverage per l'istruzione condizionale "if"](media/lut-start/code-coverage-cs1.png)

1. Fare clic sul segno di spunta verde nella riga che include `return Char.IsUpper(s[0])` nel metodo `StartsWithUpper`. Come illustrato nella figura seguente, Live Unit Testing indica che solo due test coprono la riga di codice e che tutti e due sono stati eseguiti correttamente.

   ![Code coverage per l'istruzione return](media/lut-start/code-coverage-cs2.png)

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Fare clic sul segno di spunta verde nella riga che include `If (String.IsNullOrWhiteSpace(s)) Then` nel metodo `StartsWithUpper`. Come illustrato nella figura seguente, Live Unit Testing indica che tre test coprono la riga di codice e che tutti e tre sono stati eseguiti correttamente.

   ![Code coverage per l'istruzione condizionale "if"](media/lut-start/code-coverage-vb1.png)

1. Fare clic sul segno di spunta verde nella riga che include `Return Char.IsUpper(s(0))` nel metodo `StartsWithUpper`. Come illustrato nella figura seguente, Live Unit Testing indica che solo due test coprono la riga di codice e che tutti e due sono stati eseguiti correttamente.

   ![Code coverage per l'istruzione return](media/lut-start/code-coverage-vb2.png)

---

Il problema principale che viene rilevato da Live Unit Testing è il code coverage incompleto. Questo problema verrà illustrato nella sezione successiva.

## <a name="expand-test-coverage"></a>Espandere la copertura dei test

In questa sezione verrà illustrato come estendere gli unit test al metodo `StartsWithLower`. Durante questa operazione, Live Unit Testing continuerà a testare il codice.

Per estendere il code coverage al metodo `StartsWithLower`, eseguire le operazioni seguenti:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Aggiungere i metodi `TestStartsWithLower` e `TestDoesNotStartWithLower` seguenti al file di codice sorgente del test del progetto:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Modificare il metodo `DirectCallWithNullOrEmpty` aggiungendo il codice seguente immediatamente dopo la chiamata al metodo [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse).

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Live Unit Testing esegue automaticamente i test nuovi e modificati quando si modifica il codice sorgente. Come illustrato nella figura seguente di **Esplora test**, tutti i test, inclusi i due test aggiunti e quello modificato, hanno avuto esito positivo.

   ![Esplora test dopo l'espansione della copertura dei test.](media/lut-start/test-dynamic.png)

1. Passare alla finestra che contiene il codice sorgente per la classe `StringLibrary`. In Live Unit Testing ora viene visualizzato il code coverage esteso al metodo `StartsWithLower`.

    ![Code coverage per il metodo StartsWithLower](media/lut-start/lut-extended-cs.png)

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Aggiungere i metodi `TestStartsWithLower` e `TestDoesNotStartWithLower` seguenti al file di codice sorgente del test del progetto:

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#1)]

1. Modificare il metodo `DirectCallWithNullOrEmpty` aggiungendo il codice seguente immediatamente dopo la chiamata al metodo [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse).

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#2)]

1. Live Unit Testing esegue automaticamente i test nuovi e modificati quando si modifica il codice sorgente. Come illustrato nella figura seguente di **Esplora test**, tutti i test, inclusi i due test aggiunti e quello modificato, hanno avuto esito positivo.

   ![Esplora test dopo l'espansione della copertura dei test.](media/lut-start/test-dynamic.png)

1. Passare alla finestra che contiene il codice sorgente per la classe `StringLibrary`. In Live Unit Testing ora viene visualizzato il code coverage esteso al metodo `StartsWithLower`.

    ![Code coverage per il metodo StartsWithLower](media/lut-start/lut-extended-vb.png)

---

In alcuni casi, i test superati in **Esplora test** possono essere inattivi. Ciò indica che il test è attualmente in esecuzione o che non è stato eseguito nuovamente in quanto non sono state apportate modifiche al codice che avrebbero influito sul test dopo l'ultima esecuzione.

Fino a questo punto, tutti i test hanno avuto esito positivo. Nella sezione successiva esamineremo come gestire l'esito negativo dei test.

## <a name="handling-a-test-failure"></a>Gestione dei test non riusciti

In questa sezione verrà illustrato come usare Live Unit Testing per identificare e risolvere i problemi relativi ai test con esito negativo. A questo scopo sarà necessario espandere la copertura dei test al metodo `HasEmbeddedSpaces`.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Aggiungere il metodo seguente al file di test:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Quando viene eseguito il test, Live Unit Testing indica che il metodo `TestHasEmbeddedSpaces` non è riuscito, come illustrato nella figura seguente: ![Esplora test che indica che il test ha avuto esito negativo.](media/lut-start/test-failure.png)

1. Selezionare la finestra in cui viene visualizzato il codice della libreria. Si noti che Live Unit Testing ha espanso il code coverage al metodo `HasEmbeddedSpaces`. Viene segnalato anche il test con esito negativo tramite l'aggiunta di una "🞩" rossa in corrispondenza delle righe per le quali i test non sono stati superati.

1. Passare il mouse sulla riga con la firma del metodo `HasEmbeddedSpaces`. In Live Unit Testing verrà visualizzata una descrizione comando che segnala che il metodo è coperto da un test, come illustrato nella figura seguente:

   ![Informazioni di Live Unit Testing su un test non riuscito.](media/lut-start/test-failure-info-cs.png)

1. Selezionare il test non riuscito **TestHasEmbeddedSpaces**. Si noti che Live Unit Testing offre alcune opzioni, come ad esempio l'esecuzione di tutti i test o solo di alcuni, il debug di tutti i test o solo di alcuni, come illustrato nella figura seguente:

   ![Opzioni Live Unit Testing per un test non riuscito.](media/lut-start/test-failure-options.png)

1. Selezionare **Debug Selected** (Debug selezionato) per eseguire il debug del test non riuscito.

1. Visual Studio esegue il test in modalità di debug. Il test assegna ogni stringa di una matrice a una variabile denominata `phrase` e la passa al metodo `HasEmbeddedSpaces`. L'esecuzione del programma viene sospesa e viene richiamato il debugger la prima volta in cui l'espressione di asserzione è `false`. La figura seguente illustra la finestra di dialogo di eccezione generata dal valore imprevisto nella chiamata del metodo [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue).

   ![Finestra di dialogo di eccezione di Live Unit Testing.](media/lut-start/exception-dialog-cs.png)

   Per risolvere i problemi relativi ai test con esito negativo, sono disponibili anche tutti gli strumenti di debug offerti da Visual Studio, come illustrato nella figura seguente:

   ![Strumenti di debug di Visual Studio.](media/lut-start/debugging-tools-cs.png)

   Si noti che nella finestra **Auto** il valore della variabile `phrase` è "Name\tDescription", che è il secondo elemento della matrice. Il metodo di test prevede che `HasEmbeddedSpaces` restituisca `true` quando viene passata questa stringa; in questo caso restituisce invece `false`. Evidentemente, non riconosce "\t", il carattere di tabulazione, come uno spazio incorporato.

1. Selezionare **Debug**, **Continua**, premere F5 o fare clic sul pulsante **Continua** sulla barra degli strumenti per continuare a eseguire il programma di test. Dal momento che si è verificata un'eccezione non gestita, il test viene terminato.

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Aggiungere il metodo seguente al file di test:

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/unittest2.vb#3)]

1. Quando viene eseguito il test, Live Unit Testing indica che il metodo `TestHasEmbeddedSpaces` non è riuscito, come illustrato nella figura seguente:

   ![Esplora test che indica che un test ha avuto esito negativo.](media/lut-start/test-failure.png)

1. Selezionare la finestra in cui viene visualizzato il codice della libreria. Si noti che Live Unit Testing ha espanso il code coverage al metodo `HasEmbeddedSpaces`. Viene segnalato anche il test con esito negativo tramite l'aggiunta di una "🞩" rossa in corrispondenza delle righe per le quali i test non sono stati superati.

1. Passare il mouse sulla riga con la firma del metodo `HasEmbeddedSpaces`. In Live Unit Testing verrà visualizzata una descrizione comando che segnala che il metodo è coperto da un test, come illustrato nella figura seguente:

   ![Informazioni di Live Unit Testing su un test non riuscito.](media/lut-start/test-failure-info-vb.png)

1. Selezionare il test non riuscito **TestHasEmbeddedSpaces**. Si noti che Live Unit Testing offre alcune opzioni, come ad esempio l'esecuzione di tutti i test o solo di alcuni, il debug di tutti i test o solo di alcuni, come illustrato nella figura seguente:

   ![Opzioni Live Unit Testing per un test non riuscito.](media/lut-start/test-failure-options.png)

1. Selezionare **Debug Selected** (Debug selezionato) per eseguire il debug del test non riuscito.

1. Visual Studio esegue il test in modalità di debug. Il test assegna ogni stringa di una matrice a una variabile denominata `phrase` e la passa al metodo `HasEmbeddedSpaces`. L'esecuzione del programma viene sospesa e viene richiamato il debugger la prima volta in cui l'espressione di asserzione è `false`. La figura seguente illustra la finestra di dialogo di eccezione generata dal valore imprevisto nella chiamata del metodo [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue).

   ![Finestra di dialogo di eccezione di Live Unit Testing.](media/lut-start/exception-dialog-vb.png)

   Per risolvere i problemi relativi ai test con esito negativo, sono disponibili anche tutti gli strumenti di debug offerti da Visual Studio, come illustrato nella figura seguente:

   ![Strumenti di debug di Visual Studio.](media/lut-start/debugging-tools-vb.png)

   Si noti che nella finestra **Auto** il valore della variabile `phrase` è "Name" + vbTab + "Description", che è il secondo elemento della matrice. Il metodo di test prevede che `HasEmbeddedSpaces` restituisca `true` quando viene passata questa stringa; in questo caso restituisce invece `false`. Evidentemente, non riconosce il carattere di tabulazione come uno spazio incorporato.

1. Selezionare **Debug**, **Continua**, premere F5 o fare clic sul pulsante **Continua** sulla barra degli strumenti per continuare a eseguire il programma di test. Dal momento che si è verificata un'eccezione non gestita, il test viene terminato.

---

In questo modo vengono specificate informazioni sufficienti per un'analisi preliminare del bug. `TestHasEmbeddedSpaces`, la routine di test, ha generato un presupposto errato, oppure `HasEmbeddedSpaces` non riconosce correttamente tutti gli spazi incorporati. Per diagnosticare e risolvere il problema, iniziare con il metodo `StringLibrary.HasEmbeddedSpaces`:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Esaminare il confronto nel metodo `HasEmbeddedSpaces`. Lo spazio incorporato viene considerato come U+0020. Tuttavia, lo standard Unicode include altri caratteri spazio. Ne consegue che nel codice della libreria è stato eseguito un test per gli spazi vuoti errato.

1. Sostituire il confronto delle uguaglianze con una chiamata al metodo <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName>:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing consente di rieseguire automaticamente il metodo di test non superato e aggiorna i risultati nella finestra del codice e in **Esplora test**, come illustrato nella figura seguente:

    ![Il test HasEmbeddedSpaces con esito positivo.](media/lut-start/test-success-cs.png)

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Esaminare il confronto nel metodo `HasEmbeddedSpaces`. Lo spazio incorporato viene considerato come U+0020. Tuttavia, lo standard Unicode include altri caratteri spazio. Ne consegue che nel codice della libreria è stato eseguito un test per gli spazi vuoti errato.

1. Sostituire il confronto delle uguaglianze con una chiamata al metodo <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName>:

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/class2.vb#1)]

1. Live Unit Testing consente di rieseguire automaticamente il metodo di test non superato e aggiorna i risultati nella finestra del codice e in **Esplora test**, come illustrato nella figura seguente:

    ![Il test HasEmbeddedSpaces con esito positivo.](media/lut-start/test-success-vb.png)

---

## <a name="see-also"></a>Vedere anche
[Live Unit Testing con Visual Studio 2017](live-unit-testing.md)
[Domande frequenti su Live Unit Testing](live-unit-testing-faq.md)
