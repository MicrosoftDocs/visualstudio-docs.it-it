---
title: 'Procedura dettagliata: Creazione di un frammento di codice | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f9b09a8990de97357da2703f1d08dabec50ea75e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790113"
---
# <a name="walkthrough-creating-a-code-snippet"></a>Procedura dettagliata: creazione di un frammento di codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per creare un frammento di codice sono necessari pochi passaggi. È sufficiente creare un file XML, inserire gli elementi appropriati e aggiungere il codice. È anche possibile aggiungere al codice riferimenti e parametri sostitutivi. È possibile aggiungere il frammento all'installazione di Visual Studio usando il pulsante Importa in Gestione frammenti di codice (**Strumenti**, Gestione frammenti di codice... ).  
  
> [!TIP]
>  Per informazioni su come scrivere frammenti di codice più facilmente, cercare nel sito Web CodePlex strumenti della community, ad esempio [Snippet Editor](http://go.microsoft.com/fwlink/?LinkId=251033).  
  
## <a name="snippet-template"></a>Modello di frammento  
 Di seguito è illustrato il modello di frammento di base:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CodeSnippets  
    xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title></Title>  
        </Header>  
        <Snippet>  
            <Code Language="">  
                <![CDATA[]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
  
```  
  
### <a name="to-create-a-code-snippet"></a>Per creare un frammento di codice  
  
1.  Creare un nuovo file XML in Visual Studio e aggiungere il modello come illustrato in precedenza.  
  
2.  Compilare il titolo del frammento, ad esempio "Hello World VB", nell'elemento Title.  
  
3.  Compilare il linguaggio del frammento nell'attributo Languages dell'elemento Code. In questo esempio usare "VB".  
  
4.  Aggiungere il codice nella sezione CDATA all'interno dell'elemento Code, ad esempio:  
  
    ```  
    <Code Language="VB">  
        <![CDATA[Console.WriteLine("Hello, World!")]]>  
    </Code>  
  
    ```  
  
5.  Salvare il frammento come VBCodeSnippet.snippet.  
  
### <a name="to-add-a-code-snippet-to-visual-studio"></a>Per aggiungere un frammento di codice a Visual Studio  
  
1.  È possibile aggiungere frammenti di codice personalizzati all'installazione di Visual Studio tramite Gestione frammenti di codice. Aprire Gestione frammenti di codice (**Strumenti**, Gestione frammenti di codice...).  
  
2.  Fare clic sul pulsante **Importa**.  
  
3.  Scegliere il percorso in cui è stato salvato il frammento di codice nella procedura precedente, selezionarlo e fare clic su **Apri**.  
  
4.  Si aprirà la finestra di dialogo **Importa frammento di codice** in cui viene chiesto di scegliere il punto in cui aggiungere il frammento tra le opzioni nel riquadro di destra. Una delle opzioni possibili è **Frammenti di codice**. Selezionare l'opzione e fare clic su **Fine** e poi su **OK**.  
  
5.  Il frammento viene copiato nel percorso seguente:  
  
     `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippets`  
  
6.  Testare il frammento aprendo un progetto di Visual Basic e un file di codice. Nel file fare clic su **Inserisci frammento** nel menu di scelta rapida, quindi **frammenti di codice**. Verrà visualizzato un frammento denominato **My Visual Basic Code Snippet** (Frammento di codice Visual Basic). Fare doppio clic.  
  
7.  Dovrebbe essere `Console.WriteLine("Hello, World!")` inserito nel codice.  
  
### <a name="adding-description-and-shortcut-fields"></a>Aggiunta di campi di descrizione e collegamento  
  
1.  I campi di descrizione contengono informazioni dettagliate sul frammento di codice quando viene visualizzato in Gestione frammenti di codice. Il collegamento è un tag che gli utenti possono digitare per inserire il frammento. Modificare il frammento aggiunto aprendo il file `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet`.  
  
2.  Aggiungere gli elementi Author e Description all'elemento Header e compilarli.  
  
3.  L'elemento Header dovrebbe essere simile al seguente:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
    </Header>  
  
    ```  
  
4.  Aprire Gestione frammenti di codice e selezionare il frammento di codice. Nel riquadro di destra i campi Descrizione e Autore saranno ora visualizzati popolati.  
  
5.  Per aggiungere un collegamento, aggiungere un elemento Shortcut insieme agli elementi Author e Description:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
        <Shortcut>hello</Shortcut>  
    </Header>  
  
    ```  
  
6.  Salvare di nuovo il file del frammento.  
  
7.  Per testare il collegamento, aprire un progetto Visual Basic e aprire un file di codice. Tipo `hello` nel file e premere TAB. Deve essere inserito il frammento di codice.  
  
### <a name="to-add-references-and-imports"></a>Per aggiungere riferimenti e importazioni  
  
1.  Con i frammenti di Visual Basic è possibile aggiungere un riferimento a un progetto usando l'elemento References e aggiungere una dichiarazione importazioni tramite l'elemento Imports. (Frammenti di codice in altri linguaggi non è questa funzionalità). Ad esempio, se si modifica `Console.WriteLine` nell'esempio di codice in `MessageBox.Show`, è possibile che sia necessario aggiungere l'assembly System.Windows.Forms.dll al progetto.  
  
2.  Aprire il frammento.  
  
3.  Aggiungere l'elemento References sotto l'elemento Snippet:  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Windows.Forms.dll</Assembly>  
        </Reference>  
    </References>  
  
    ```  
  
4.  Aggiungere l'elemento Imports sotto l'elemento Snippet:  
  
    ```  
    <Imports>  
        <Import>  
           <Namespace>System.Windows.Forms</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
5.  Modificare la sezione CDATA nel modo seguente:  
  
    ```  
    <![CDATA[MessageBox.Show("Hello, World!")]]>  
    ```  
  
6.  Salvare il frammento.  
  
7.  Aprire un progetto Visual Basic e aggiungere il frammento.  
  
8.  Sarà visualizzata un'istruzione Imports nella parte superiore del file di codice:  
  
    ```  
    Imports System.Windows.Forms  
  
    ```  
  
9. Considerare le proprietà del progetto. La scheda Riferimenti contiene un riferimento a System.Windows.Forms.dll.  
  
### <a name="adding-replacements"></a>Aggiunta di sostituzioni  
  
1.  È possibile che si vogliano sostituire alcune parti dei frammenti di codice, ad esempio nel caso in cui venga aggiunta una variabile e la si voglia sostituire con una del progetto corrente. È possibile specificare due tipi di sostituzioni, vale a dire valori letterali e oggetti. I valori letterali sono stringhe di un certo tipo, ad esempio valori letterali stringa, nomi di variabile o rappresentazioni di stringa di valori numerici. Gli oggetti sono istanze di un certo tipo diverso da una stringa. Questa procedura consente di dichiarare la sostituzione di un valore letterale o di un oggetto e modificare il codice in modo che faccia riferimento a queste sostituzioni.  
  
2.  Aprire il frammento.  
  
3.  In questo esempio viene usata una stringa di connessione SQL. È quindi necessario modificare gli elementi Imports e References per aggiungere i riferimenti appropriati:  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Data.dll</Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>System.Xml.dll</Assembly>  
        </Reference>  
    </References>  
    <Imports>  
        <Import>  
            <Namespace>System.Data</Namespace>  
        </Import>  
        <Import>  
            <Namespace>System.Data.SqlClient</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
4.  Per dichiarare la sostituzione di un valore letterale della stringa di connessione SQL, aggiungere un elemento Declarations sotto l'elemento Snippet e qui aggiungere un elemento Literal con sottoelementi per l'ID, la descrizione comando e il valore predefinito per la sostituzione:  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
    </Declarations>  
  
    ```  
  
5.  Per dichiarare la sostituzione di un oggetto per la connessione SQL, aggiungere un elemento Object all'interno dell'elemento Declarations e aggiungere sottoelementi per l'ID, il tipo di oggetto, la descrizione comando e il valore predefinito. L'elemento Declarations risultante sarà simile al seguente:  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
        <Object>  
            <ID>SqlConnection</ID>  
            <Type>System.Data.SqlClient.SqlConnection</Type>  
            <ToolTip>Replace with a connection object in your application.</ToolTip>  
            <Default>dcConnection</Default>  
        </Object>  
    </Declarations>  
    ```  
  
6.  Nella sezione di codice si fa riferimento alle sostituzioni delimitandole con i segni $, ad esempio `$replacement$`:  
  
    ```  
    <Code Language="VB" Kind="method body">  
        <![CDATA[Dim daCustomers As SqlDataAdapter  
            Dim selectCommand As SqlCommand  
  
            daCustomers = New SqlClient.SqlDataAdapter()  
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)  
            daCustomers.SelectCommand = selectCommand  
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>  
    </Code>  
    ```  
  
7.  Salvare il frammento.  
  
8.  Aprire un progetto Visual Basic e aggiungere il frammento.  
  
9. Il codice sarà essere simile al seguente, dove le sostituzioni `SQL connection string` e `dcConnection` sono evidenziate in arancione chiaro. Premere TAB per passare da uno a altro.  
  
    ```  
    Dim daCustomers As SqlDataAdapter  
    Dim selectCommand As SqlCommand  
  
    daCustomers = New SqlClient.SqlDataAdapter()  
    selectCommand = New SqlClient.SqlCommand("SQL connection string")  
    daCustomers.SelectCommand = selectCommand  
    daCustomers.SelectCommand.Connection = dcConnection  
  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento dello schema dei frammenti di codice](../ide/code-snippets-schema-reference.md)
