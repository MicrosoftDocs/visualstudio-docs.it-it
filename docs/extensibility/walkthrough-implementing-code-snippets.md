---
title: 'Procedura dettagliata: Implementazione di frammenti di codice | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae260951160bc3d4ed3bb1535f47eb1f33649957
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-implementing-code-snippets"></a>Procedura dettagliata: Implementazione di frammenti di codice
È possibile creare frammenti di codice e includere in un'estensione di editor in modo che gli utenti dell'estensione per poter aggiungere il proprio codice.  
  
 Un frammento di codice è un frammento di codice o altro testo che può essere incorporato in un file. Per visualizzare tutti i frammenti di codice che è state registrate per determinati linguaggi di programmazione, il **strumenti** menu, fare clic su **Gestione frammenti di codice**. Per inserire un frammento di codice in un file, il pulsante destro del mouse in cui si desidera che il frammento, fare clic su **Inserisci frammento di codice** o **Racchiudi**, individuare il frammento di codice desiderato e quindi fare doppio clic. Premere TAB o MAIUSC + TAB per modificare le parti pertinenti del frammento di codice e quindi premere INVIO o ESC per accettarla. Per altre informazioni, vedere [Code Snippets](../ide/code-snippets.md) (Frammenti di codice).  
  
 Un frammento di codice è contenuto in un file XML con l'estensione del nome file con estensione snippet. Un frammento di codice può contenere i campi che vengono evidenziati dopo l'inserimento del frammento in modo che l'utente può trovare e modificarle. Un file di frammento fornisce anche informazioni per il **Gestione frammenti di codice** in modo da poter visualizzare il nome del frammento di codice nella categoria corretta. Per informazioni sullo schema del frammento di codice, vedere [riferimenti allo Schema dei frammenti di codice](../ide/code-snippets-schema-reference.md).  
  
 Questa procedura dettagliata illustra come eseguire queste attività:  
  
1.  Creare e registrare i frammenti di codice per una lingua specifica.  
  
2.  Aggiungere il **Inserisci frammento di codice** comando a un menu di scelta rapida.  
  
3.  Implementare l'espansione del frammento di codice.  
  
 Questa procedura dettagliata è basata su [procedura dettagliata: visualizzazione di completamento delle istruzioni](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-and-registering-code-snippets"></a>Creazione e registrazione di frammenti di codice  
 In genere, i frammenti di codice sono associati a un servizio di linguaggio registrato. Tuttavia, non è necessario implementare un <xref:Microsoft.VisualStudio.Package.LanguageService> per registrare i frammenti di codice. Al contrario, specificare solo un GUID nel file di indice del frammento di codice e quindi utilizzare lo stesso GUID nel <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> aggiunti al progetto.  
  
 La procedura seguente viene illustrato come creare frammenti di codice e associarli a un GUID specifico.  
  
1.  Creare la struttura di directory seguente:  
  
     **%INSTALLDIR%\TestSnippets\Snippets\1033\\**  
  
     dove *% InstallDir %* è la cartella di installazione di Visual Studio. (Anche se questo percorso è in genere utilizzato per installare i frammenti di codice, è possibile specificare qualsiasi percorso.)  
  
2.  Nella cartella \1033\, creare un file XML e denominarlo **TestSnippets.xml**. (Anche se questo nome viene utilizzato in genere per un file di indice del frammento di codice, è possibile specificare qualsiasi nome, purché ha un'estensione di file XML.) Aggiungere il testo seguente, quindi eliminare il segnaposto GUID e aggiungere la propria.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <SnippetCollection>  
        <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">  
            <SnippetDir>  
                <OnOff>On</OnOff>  
                <Installed>true</Installed>  
                <Locale>1033</Locale>  
                <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>  
                <LocalizedName>Snippets</LocalizedName>  
            </SnippetDir>  
        </Language>  
    </SnippetCollection>  
    ```  
  
3.  Creare un file nella cartella frammento, denominarlo **test**`.snippet`, quindi aggiungere il testo seguente:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
        <CodeSnippet Format="1.0.0">  
            <Header>  
                <Title>Test replacement fields</Title>  
                <Shortcut>test</Shortcut>  
                <Description>Code snippet for testing replacement fields</Description>  
                <Author>MSIT</Author>  
                <SnippetTypes>  
                    <SnippetType>Expansion</SnippetType>  
                </SnippetTypes>  
            </Header>  
            <Snippet>  
                <Declarations>  
                    <Literal>  
                      <ID>param1</ID>  
                        <ToolTip>First field</ToolTip>  
                        <Default>first</Default>  
                    </Literal>  
                    <Literal>  
                        <ID>param2</ID>  
                        <ToolTip>Second field</ToolTip>  
                        <Default>second</Default>  
                    </Literal>  
                </Declarations>  
                <References>  
                   <Reference>  
                       <Assembly>System.Windows.Forms.dll</Assembly>  
                   </Reference>  
                </References>  
                <Code Language="TestSnippets">  
                    <![CDATA[MessageBox.Show("$param1$");  
         MessageBox.Show("$param2$");]]>  
                </Code>    
            </Snippet>  
        </CodeSnippet>  
    </CodeSnippets>  
    ```  
  
 La procedura seguente viene illustrato come registrare i frammenti di codice.  
  
#### <a name="to-register-code-snippets-for-a-specific-guid"></a>Per registrare i frammenti di codice per un GUID specifico  
  
1.  Aprire il **CompletionTest** progetto. Per informazioni su come creare questo progetto, vedere [procedura dettagliata: visualizzazione di completamento delle istruzioni](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2.  Nel progetto, aggiungere riferimenti agli assembly riportati di seguito:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   Microsoft.MSXML  
  
3.  Nel progetto, aprire il file vsixmanifest.  
  
4.  Assicurarsi che il **asset** scheda contiene un **VsPackage** tipo e che il contenuto **progetto** è impostato sul nome del progetto.  
  
5.  Selezionare il progetto CompletionTest e nella finestra Proprietà impostare **genera Pkgdef File** a **true**. Salvare il progetto.  
  
6.  Aggiungere un valore statico `SnippetUtilities` classe al progetto.  
  
     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  Nella classe SnippetUtilities, definire un GUID e assegnargli il valore utilizzato nel file SnippetsIndex.xml.  
  
     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  Aggiungere il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> per la `TestCompletionHandler` classe. Questo attributo può essere aggiunto a qualsiasi classe (non statici) interna o pubblica nel progetto. (Potrebbe essere necessario aggiungere un `using` istruzione dello spazio dei nomi Microsoft.VisualStudio.Shell.)  
  
     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. Compilare ed eseguire il progetto. Nell'istanza sperimentale di Visual Studio che viene avviato quando viene eseguito il progetto, il frammento di codice appena registrato deve essere visualizzato nel **Gestione frammenti di codice** sotto il **TestSnippets** language.  
  
## <a name="adding-the-insert-snippet-command-to-the-shortcut-menu"></a>Aggiunge il comando di frammento di inserimento al menu di scelta rapida  
 Il **Inserisci frammento di codice** comando non è incluso nel menu di scelta rapida per un file di testo. Pertanto, è necessario abilitare il comando.  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Per aggiungere il comando Inserisci frammento di codice al menu di scelta rapida  
  
1.  Aprire il `TestCompletionCommandHandler` file di classe.  
  
     Poiché questa classe implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, è possibile attivare il **Inserisci frammento di codice** comando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo. Prima di abilitare il comando, verificare che questo metodo non è viene chiamato all'interno di una funzione di automazione perché quando il **Inserisci frammento di codice** si fa clic sul comando, visualizzerà l'interfaccia utente di selezione frammento di codice (UI).  
  
     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  Compilare ed eseguire il progetto. Nell'istanza sperimentale, aprire un file con estensione zzz e quindi fare clic in essa contenuti. Il **Inserisci frammento di codice** comando deve essere visualizzato nel menu di scelta rapida.  
  
## <a name="implementing-snippet-expansion-in-the-snippet-picker-ui"></a>Implementazione di frammento espansione in selezione frammento di codice dell'interfaccia utente  
 In questa sezione viene illustrato come implementare espansione frammento di codice in modo che la selezione frammento di codice dell'interfaccia utente viene visualizzato quando **Inserisci frammento di codice** si fa clic sul menu di scelta rapida. Un frammento di codice viene espanso anche quando un utente digita il collegamento al frammento di codice e quindi preme TAB.  
  
 Per visualizzare selezione frammento di codice dell'interfaccia utente e per abilitare la navigazione e l'accettazione di post-inserimento frammento, utilizzare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo. Dell'operazione di inserimento è gestito dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metodo.  
  
 L'implementazione di espansione di frammento di codice utilizza legacy <xref:Microsoft.VisualStudio.TextManager.Interop> interfacce. Quando si traducono dalle classi editor corrente al codice legacy, tenere presente che le interfacce legacy utilizzano una combinazione di numeri di riga e colonna per specificare i percorsi in un buffer di testo, ma le classi corrente utilizzano un indice. Pertanto, se un buffer con tre righe, ognuna delle quali contiene dieci caratteri (più di una nuova riga, che viene conteggiato come 1 carattere), il quarto carattere nella terza riga si trova in posizione 27 nell'implementazione corrente, ma si trova a riga 2, posizione 3 nell'implementazione precedente.  
  
#### <a name="to-implement-snippet-expansion"></a>Per implementare l'espansione del frammento di codice  
  
1.  Il file che contiene il `TestCompletionCommandHandler` classe, aggiungere le seguenti `using` istruzioni.  
  
     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  Rendere il `TestCompletionCommandHandler` classe implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfaccia.  
  
     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  Nel `TestCompletionCommandHandlerProvider` classe, importare il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.  
  
     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  Aggiungere alcuni campi privati per le interfacce di espansione del codice e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  Nel costruttore del `TestCompletionCommandHandler` , impostare i campi seguenti.  
  
     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  Per visualizzare selezione frammento di codice quando l'utente fa clic il **Inserisci frammento di codice** comando, aggiungere il codice seguente per il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo. (Per rendere più leggibili la spiegazione, non viene visualizzato il codice Exec () che viene utilizzato per il completamento delle istruzioni, invece, vengono aggiunti i blocchi di codice al metodo esistente). Aggiungere il blocco di codice seguente dopo il codice che verifica la presenza di un carattere.  
  
     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  Se un frammento di codice presenta i campi che possono essere esplorati, la sessione di espansione viene mantenuta aperta finché l'espansione in modo esplicito è accettata. Se il frammento di codice non contiene campi, la sessione viene chiusa e viene restituita come `null` dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> metodo. Nel <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> (metodo), dopo la selezione frammento di codice dell'interfaccia utente che è stato aggiunto nel passaggio precedente, aggiungere il codice seguente per gestire la navigazione frammento (quando l'utente preme TAB o MAIUSC + TAB dopo l'inserimento di frammenti).  
  
     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  Per inserire il frammento di codice quando l'utente digita la scelta rapida corrispondente e quindi preme TAB, aggiungere codice per il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo. Verrà visualizzato il metodo privato che inserisce il frammento di codice in un passaggio successivo. Aggiungere il codice seguente dopo il codice di navigazione che è stato aggiunto nel passaggio precedente.  
  
     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. Implementare i metodi del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfaccia. In questa implementazione, sono gli unici metodi di interesse <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Gli altri metodi devono restituire semplicemente <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. Implementare il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Il metodo helper che effettivamente inserisce le espansioni verrà trattato in un passaggio successivo. Il <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> fornisce informazioni di riga e colonna, che è possibile ottenere dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. Il metodo privato seguente consente di inserire un frammento di codice, in base il collegamento o il titolo e il percorso. Chiama quindi il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> metodo con il frammento di codice.  
  
     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## <a name="building-and-testing-code-snippet-expansion"></a>Creare e testare l'espansione di frammento di codice  
 È possibile verificare se l'espansione del frammento di codice funziona nel progetto.  
  
1.  Compilare la soluzione. Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
2.  Aprire un file di testo e digitare del testo.  
  
3.  Fare doppio clic su un punto qualsiasi nel testo e quindi fare clic su **Inserisci frammento di codice**.  
  
4.  Selezione frammento di codice dell'interfaccia utente deve essere visualizzato con una finestra popup che indica che **testare i campi di sostituzione**. Fare doppio clic sulla finestra a comparsa.  
  
     Deve essere inserito il frammento di codice seguente.  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     Premere INVIO o ESC.  
  
5.  Premere TAB e MAIUSC + TAB per passare tra "first" e "secondo".  
  
6.  Accettare l'inserimento premendo INVIO o ESC.  
  
7.  In un'altra parte del testo, digitare "test" e quindi premere TAB. Poiché "test" è il collegamento al frammento di codice, il frammento di codice deve essere inserito nuovamente.  
  
## <a name="next-steps"></a>Passaggi successivi