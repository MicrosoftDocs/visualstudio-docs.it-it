---
title: Introduzione alla modifica di codice in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/30/2017
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 46f627d7157972e277589d2edf07309190c6430d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="quickstart-use-the-code-editor"></a>Guida introduttiva: Usare l'editor del codice

In questa presentazione dell'editor, della durata di 10 minuti, si aggiunge codice a un file per vedere le modalità con cui Visual Studio semplifica la scrittura, la navigazione e la comprensione del codice.

Se non è ancora stato installato Visual Studio, accedere alla pagina [Download di Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) per installarlo gratuitamente.

Questa guida introduttiva presuppone una certa familiarità con un linguaggio di programmazione. In caso contrario, è consigliabile leggere prima di tutto una delle guide introduttive alla programmazione, ad esempio su come creare un'app Web con [Python](../ide/quickstart-python.md) o [C#](../ide/tutorial-csharp-aspnet-core.md) oppure come creare un'app console con [Visual Basic](../ide/quickstart-visual-basic-console.md) o [C++](../ide/quickstart-cpp.md).

## <a name="create-a-new-code-file"></a>Creare un nuovo file di codice

Per iniziare si crea un nuovo file e si aggiunge codice al file. Si noti che per sfruttare alcuni dei vantaggi offerti dall'editor non è necessario creare un progetto.

1. Aprire Visual Studio, quindi nel menu **File** sulla barra dei menu scegliere **Nuovo** > **File**.

1. Nella finestra di dialogo **Nuovo file**, nella categoria **Generale**, scegliere **Classe di Visual C#** e quindi scegliere **Apri**.

   Nell'editor viene aperto un nuovo file con lo scheletro di una classe C#.

## <a name="using-code-snippets"></a>Uso di frammenti di codice

Visual Studio offre frammenti di codice utili che è possibile usare per generare in modo semplice e rapido blocchi di codice di uso comune. [I frammenti di codice](../ide/code-snippets.md) sono disponibili per vari linguaggi di programmazione, tra cui C#, Visual Basic e C++. Ora si aggiunge il frammento C# `void Main` al file.

1. Posizionare il cursore sotto la parentesi graffa di chiusura del costruttore `Class1` e immettere i caratteri `svm`.

   Viene visualizzata una finestra di dialogo IntelliSense con informazioni sul frammento `svm`.

   ![Frammento IntelliSense](media/quickstart-intellisense-snippet.png)

1. Premere due volte **TAB** per inserire il frammento di codice.

   La firma del metodo `static void Main()` viene aggiunta al file. Il metodo `Main()` è il punto di ingresso per le applicazioni C#.

I frammenti di codice disponibili variano a seconda del linguaggio. Per vedere i frammenti di codice disponibili per il linguaggio di programmazione scegliere **Modifica**, **IntelliSense**, **Inserisci frammento** e quindi scegliere la cartella del linguaggio. Per C# l'elenco ha l'aspetto seguente:

![Elenco di frammenti di codice per C#](media/quickstart-code-snippet-list.png)

L'elenco include frammenti per la creazione di una classe, un costruttore, `Console.WriteLine()`, cicli `for`, istruzioni `if` e `switch` e altro ancora.

## <a name="commenting-out-code"></a>Impostazione di codice come commento

La barra degli strumenti dispone di vari pulsanti che favoriscono la produttività durante la creazione di codice. Ad esempio è possibile attivare o disattivare la modalità di terminazione IntelliSense, aumentare o ridurre un rientro, impostare un segnalibro o impostare del codice come commento. In questa sezione si imposta come commento del codice che non si vuole compilare.

![Barra degli strumenti editor](media/quickstart-editor-toolbar.png)

1. Incollare il codice seguente nel corpo del metodo `Main()`.

    ```csharp
    // _words is a string array that we'll sort alphabetically
    string[] _words = {
        "the",
        "quick",
        "brown",
        "fox",
        "jumps"
    };

    string[] morewords = {
        "over",
        "the",
        "lazy",
        "dog"
    };

    IEnumerable<string> query = from word in _words
                                orderby word.Length
                                select word;
    ```

1. In questa fase non si usa la variabile `morewords`, ma questa potrebbe risultare utile in seguito, quindi non la si elimina. Invece si impostano le linee corrispondenti come commento. Selezionare l'intera definizione di `morewords` fino al punto e virgola finale, quindi scegliere il pulsante **Imposta le righe selezionate come commento** sulla barra degli strumenti o premere **CTRL**+**K**, **CTRL**+**C**.

   ![Pulsante di impostazione come commento](media/quickstart-comment-out.png)

   I caratteri del commento di C# `//` vengono aggiunti all'inizio di ogni linea selezionata per impostare la linea come codice.

## <a name="collapsing-code-blocks"></a>Compressione dei blocchi di codice

Non è necessario visualizzare il costruttore vuoto per `Class1` che è stato generato, pertanto per semplificare la visualizzazione del codice si procederà a comprimere il costruttore. Scegliere la piccola casella grigia contenente il segno meno sul margine della prima riga del costruttore. Con la tastiera posizionare il cursore in qualsiasi punto del codice del costruttore e premere **CTRL**+**M**, **CTRL**+**M**.

![Pulsante di compressione evidenziato](media/quickstart-collapse.png)

Il blocco di codice viene compresso e visualizza solo la prima riga seguita dai puntini di sospensione (`...`). Per espandere di nuovo il blocco di codice fare clic sulla stessa casella grigia, che ora contiene un segno più, oppure premere di nuovo **CTRL**+**M**, **CTRL**+**M**. Questa funzionalità è detta [gestione della struttura](../ide/outlining.md) ed è particolarmente utile per comprimere metodi con molto codice o intere classi.

## <a name="viewing-symbol-definitions"></a>Visualizzazione delle definizioni dei simboli

L'editor di Visual Studio semplifica l'ispezione della definizione di un tipo, un metodo e così via. Ad esempio è possibile navigare al file contenente la definizione scegliendo **Vai alla definizione** in qualsiasi punto in cui esiste un riferimento al simbolo. Un metodo ancora più veloce che non sposta lo stato attivo dal file in uso è rappresentato da [Visualizza definizione](../ide/go-to-and-peek-definition.md#peek-definition). Di seguito si procede a visualizzare la definizione di `string`.

1. Fare clic con il pulsante destro del mouse su una qualsiasi ricorrenza di `string` e scegliere **Visualizza definizione** dal menu del contenuto o premere **ALT**+**F12**.

   Viene visualizzata una finestra popup con la definizione della classe `String`. È possibile scorrere all'interno della finestra popup o anche esaminare la definizione di un altro tipo dal codice visualizzato.

   ![Finestra Visualizza definizione](media/quickstart-peek-definition.png)

1. Chiudere la finestra di visualizzazione della definizione scegliendo la piccola casella contenente una "x" nell'angolo in alto a destra della finestra popup.

## <a name="using-intellisense-to-complete-words"></a>Uso di IntelliSense per il completamento di parole

[IntelliSense](../ide/using-intellisense.md) è una risorsa molto importante per la creazione di codice. Consente di visualizzare informazioni sui membri disponibili di un tipo o sui dettagli parametro per diversi overload di un metodo. È anche possibile usare IntelliSense per completare una parola dopo aver digitato un numero di caratteri sufficiente a evitare ambiguità. Ora si aggiungerà una riga di codice per visualizzare le stringhe ordinate nella finestra della console.

1. Sotto la variabile `query` iniziare a digitare il codice seguente:

   ```csharp
   foreach (string str in qu
   ```

   IntelliSense visualizza **informazioni rapide** sul simbolo `query`.

   ![Completamento della parola di IntelliSense](media/quickstart-intellisense-completion-list.png)

1. Per inserire il resto della parola `query` mediante la funzionalità IntelliSense "Completa parola" premere **TAB**.

1. Completare il blocco di codice in modo che abbia un aspetto simile al codice seguente. È anche possibile esercitarsi ulteriormente nell'uso di frammenti di codice immettendo `cw` e quindi premendo **TAB** due volte per generare il codice `Console.WriteLine`.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactoring-a-name"></a>Refactoring di un nome

Quando si inizia a creare codice è facile commettere errori e quindi dover modificare il nome di una variabile o di un metodo. Ora si userà la funzionalità [refactoring](../ide/refactoring-in-visual-studio.md) di Visual Studio per rinominare la variabile `_words` come `words`.

1. Posizionare il cursore sulla definizione della variabile `words`, quindi scegliere **Rinomina** dal menu di scelta rapida o dal menu a comparsa oppure premere **CTRL**+**R**, **CTRL**+**R**.

   Nella parte superiore destra dell'editor viene visualizzata la finestra di dialogo popup **Rinomina**.

1. Immettere il nome desiderato: `words`. Si noti che anche il riferimento a `words` nella query viene rinominato automaticamente. Prima di premere **INVIO** selezionare la casella di controllo **Includi commenti** nella finestra popup **Rinomina**.

   ![Rinomina (finestra di dialogo)](media/quickstart-rename.png)

1. Premere **INVIO**.

   Entrambe le ricorrenze di `words` sono state rinominate, e così anche il riferimento a `words` nel commento del codice.

## <a name="next-steps"></a>Passaggi successivi

Questa guida introduttiva per l'editor di Visual Studio è stata completata. Ora è possibile vedere altre guide introduttive per l'IDE di Visual Studio, esaminare altri metodi per lo [spostamento nel codice](../ide/navigating-code.md) o vedere i collegamenti ad altre informazioni sulle funzionalità appena esaminate. Buon lavoro.

## <a name="see-also"></a>Vedere anche

- [Guida introduttiva: Presentazione dell'IDE di Visual Studio](../ide/quickstart-ide-orientation.md)
- [Guida introduttiva: Personalizzare l'IDE e l'editor di Visual Studio](../ide/quickstart-personalize-the-ide.md)
- [Guida introduttiva: Progetti e soluzioni](../ide/quickstart-projects-solutions.md)
- [Frammenti di codice](../ide/code-snippets.md)
- [Struttura](../ide/outlining.md)
- [Vai a definizione e Visualizza definizione](../ide/go-to-and-peek-definition.md)
- [Refactoring](../ide/refactoring-in-visual-studio.md)
- [Utilizzo di IntelliSense](../ide/using-intellisense.md)
