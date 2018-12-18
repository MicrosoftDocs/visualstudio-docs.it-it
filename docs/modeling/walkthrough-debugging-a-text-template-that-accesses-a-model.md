---
title: 'Procedura dettagliata: debug di un modello di testo che accede a un modello'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: afa61e3d6158e5651fdc88969270a3bcf3af63c5
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Procedura dettagliata: debug di un modello di testo che accede a un modello
Quando si modificano o si aggiungono modelli di testo in una soluzione di linguaggio specifico di dominio, è possibile ricevere errori quando il motore di trasformazione del modello al codice sorgente oppure durante la compilazione del codice generato. La seguente procedura dettagliata vengono illustrate alcune delle operazioni che è possibile eseguire per eseguire il debug di un modello di testo.

> [!NOTE]
>  Per ulteriori informazioni sul testo modelli in generale, vedere [la generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md). Per ulteriori informazioni sul debug di modelli di testo, vedere [procedura dettagliata: debug di un modello di testo](http://msdn.microsoft.com/Library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f).

## <a name="creating-a-domain-specific-language-solution"></a>Creazione di una soluzione di linguaggio specifico di dominio
 In questa procedura, si crea una soluzione di linguaggio specifico di dominio che ha le caratteristiche seguenti:

-   Nome: DebuggingTestLanguage

-   Modello di soluzione: lingua minima

-   Estensione di file:. ddd

-   Nome della società: Fabrikam

 Per ulteriori informazioni sulla creazione di una soluzione di linguaggio specifico di dominio, vedere [procedura: creare una soluzione di linguaggio specifico di dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="creating-a-text-template"></a>Creazione di un modello di testo
 Aggiungere un modello di testo alla soluzione.

#### <a name="to-create-a-text-template"></a>Per creare un modello di testo

1.  Compilare la soluzione e avviarne l'esecuzione nel debugger. (Nel **compilare** menu, fare clic su **Ricompila soluzione**e scegliere il **Debug** dal menu fare clic su **Avvia debug**.) Una nuova istanza di Visual Studio apre il progetto di debug.

2.  Aggiungere un file di testo denominato `DebugTest.tt` al progetto di debug.

3.  Assicurarsi che il **lo strumento personalizzato** di DebugTest.tt è impostata su `TextTemplatingFileGenerator`.

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Debug di direttive di accedere a un modello da un modello di testo
 Prima di accedere a un modello dalle istruzioni e le espressioni in un modello di testo, è innanzitutto necessario chiamare un processore di direttiva generato. Chiamare il processore di direttiva generato rende le classi nel modello disponibile al codice del modello di testo come proprietà. Per ulteriori informazioni, vedere [l'accesso a modelli da modelli di testo](../modeling/accessing-models-from-text-templates.md).

 Nelle procedure seguenti, si eseguirà il debug di un nome di direttiva non corretto e un nome di proprietà non corrette.

#### <a name="to-debug-an-incorrect-directive-name"></a>Eseguire il debug di un nome di direttiva non corretto

1.  Sostituire il codice in DebugTest.tt con il codice seguente:

    > [!NOTE]
    >  Il codice contiene un errore. È stato introdotto per eseguire il debug.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2.  In **Esplora**DebugTest.tt destro e quindi fare clic su **Esegui strumento personalizzato**.

     Il **elenco errori** finestra viene visualizzato questo errore:

     **Il processore denominato 'DebuggingTestLanguageDirectiveProcessor' non supporta la direttiva denominata 'modelRoot'. La trasformazione non verrà eseguita.**

     In questo caso, la chiamata di direttiva contiene un nome di direttiva non corretto. È stato specificato `modelRoot` come il nome della direttiva, ma il nome di direttiva corretto `DebuggingTestLanguage`.

3.  Fare doppio clic su errore nel **elenco errori** finestra per passare al codice.

4.  Per correggere il codice, modificare il nome di direttiva in `DebuggingTestLanguage`.

     La modifica viene evidenziata.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5.  In **Esplora**DebugTest.tt destro e quindi fare clic su **Esegui strumento personalizzato**.

     A questo punto il sistema trasforma il modello di testo e genera il file di output corrispondente. Eventuali errori nel non verrà visualizzato il **elenco errori** finestra.

#### <a name="to-debug-an-incorrect-property-name"></a>Eseguire il debug di un nome di proprietà non corrette

1.  Sostituire il codice in DebugTest.tt con il codice seguente:

    > [!NOTE]
    >  Il codice contiene un errore. È stato introdotto per eseguire il debug.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2.  Nel **Esplora**DebugTest.tt destro e quindi fare clic su **Esegui strumento personalizzato**.

     Il **elenco errori** finestra viene visualizzato uno di questi errori:

     (C#)

     **La compilazione di trasformazione: Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation' non contiene una definizione per 'ExampleModel'**

     (Visual Basic)

     **La compilazione di trasformazione: 'ExampleModel' non è un membro di ' Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation'.**

     In questo caso, il codice del modello di testo contiene un nome di proprietà non corrette. È stato specificato `ExampleModel` come il nome della proprietà, ma la proprietà corretta è nome `LibraryModel`. È possibile trovare il nome corretto della proprietà di fornisce parametro, come illustrato nel codice seguente:

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3.  Fare doppio clic su errore nella finestra Elenco errori per passare al codice.

4.  Per correggere il codice, modificare il nome della proprietà `LibraryModel` nel codice del modello di testo.

     Le modifiche sono evidenziate.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.LibraryModel #>
    <#
    foreach (ExampleElement element in this.LibraryModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.LibraryModel #>
    <#
    For Each element as ExampleElement in Me.LibraryModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

5.  In **Esplora**DebugTest.tt destro e quindi fare clic su **Esegui strumento personalizzato**.

     A questo punto il sistema trasforma il modello di testo e genera il file di output corrispondente. Eventuali errori nel non verrà visualizzato il **elenco errori** finestra.