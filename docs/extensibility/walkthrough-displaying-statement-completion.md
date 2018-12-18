---
title: 'Procedura dettagliata: Visualizzazione di completamento delle istruzioni | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bbdc79275dd99c502533c82665741b84620be928
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-displaying-statement-completion"></a>Procedura dettagliata: Visualizzazione di completamento istruzioni
È possibile implementare il completamento delle istruzioni basata su linguaggio definendo gli identificatori per il quale si desidera fornire completamento e quindi attivare una sessione di completamento. È possibile definire il completamento delle istruzioni nel contesto di un servizio di linguaggio, definire la propria estensione di file e il tipo di contenuto e quindi visualizzare il completamento per quel tipo o è possibile attivare il completamento per un tipo di contenuto esistente, ad esempio, "normale". Questa procedura dettagliata viene illustrato come attivare il completamento del tipo di contenuto "normale", ovvero il tipo di contenuto dei file di testo. Il tipo di contenuto "text" è il predecessore di tutti gli altri tipi contenuti, inclusi codice e file XML.  
  
 Completamento delle istruzioni viene in genere attivato digitando alcuni caratteri, ad esempio, digitando l'inizio di un identificatore, ad esempio "using". In genere viene chiuso premendo il tasto barra spaziatrice, Tab o INVIO per eseguire il commit di una selezione. È possibile implementare le funzionalità di IntelliSense che vengono attivate digitando un carattere utilizzando un gestore del comando per la sequenza di tasti (il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface) e un gestore provider che implementa il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaccia. Per creare l'origine di completamento, ovvero l'elenco degli identificatori che fanno parte di completamento, implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interfaccia e un provider di origine di completamento (il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interface). I provider sono parti componente Managed Extensibility Framework (MEF). Sono responsabili per le classi di origine e il controller di esportazione e importazione di servizi e istanze di Service Broker, ad esempio, il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, che consente la navigazione nel buffer di testo e <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, che avvia la sessione di completamento.  
  
 Questa procedura dettagliata viene illustrato come implementare il completamento per un set di identificatori. In implementazioni complete, il servizio di linguaggio e la documentazione del linguaggio sono responsabili per fornire tale contenuto.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF  
  
1.  Creare un progetto VSIX in c#. (Nel **nuovo progetto** finestra di dialogo Seleziona **Visual c# / Extensibility**, quindi **progetto VSIX**.) Denominare la soluzione `CompletionTest`.  
  
2.  Aggiungere un modello di elemento di classificatore Editor al progetto. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
4.  Aggiungere i riferimenti seguenti al progetto e verificare che **CopyLocal** è impostato su `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Interop  
  
     14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-the-completion-source"></a>Implementazione dell'origine di completamento  
 L'origine di completamento è responsabile per la raccolta di set di identificatori e aggiungendo il contenuto nella finestra di completamento quando un utente digita un trigger di completamento, ad esempio le prime lettere di un identificatore. In questo esempio, gli identificatori e le relative descrizioni sono hardcoded nel <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodo. Nella maggior parte dei casi reali, utilizzare il parser del linguaggio per ottenere i token per popolare l'elenco di completamento.  
  
#### <a name="to-implement-the-completion-source"></a>Per implementare l'origine di completamento  
  
1.  Aggiungere un file di classe e assegnargli il nome `TestCompletionSource`.  
  
2.  Aggiungere queste importazioni:  
  
     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  Modificare la dichiarazione di classe per `TestCompletionSource` in modo che implementi <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  Aggiungere campi privati per il provider di origine, il buffer di testo e un elenco di <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> oggetti (che corrispondono agli identificatori che farà parte della sessione di completamento):  
  
     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  Aggiungere un costruttore che imposta il buffer e il provider di origine. La `TestCompletionSourceProvider` classe è definita nei passaggi successivi:  
  
     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodo mediante l'aggiunta di un set di completamento che contiene i completamenti si desidera fornire nel contesto. Ogni set di completamento contiene un set di <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> completamenti e corrisponde a una scheda della finestra di completamento. (Denominate nei progetti di Visual Basic, le schede della finestra completamento **comuni** e **tutti**.) Il metodo FindTokenSpanAtPosition è definito nel passaggio successivo.  
  
     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  Il metodo seguente viene utilizzato per trovare la parola corrente dalla posizione del cursore:  
  
     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  Implementare il `Dispose()` metodo:  
  
     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## <a name="implementing-the-completion-source-provider"></a>Implementazione del Provider di origine di completamento  
 Il provider di origine di completamento è la parte del componente MEF che crea un'istanza di origine di completamento.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Per implementare il provider di origine di completamento  
  
1.  Aggiungere una classe denominata `TestCompletionSourceProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Esportazione di questa classe con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di testo "normale" e un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "completamento del test".  
  
     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  Importa un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, che consente di trovare la parola corrente dell'origine di completamento.  
  
     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> metodo per creare un'istanza di origine di completamento.  
  
     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Implementazione del Provider di gestore di comandi di completamento  
 Provider del gestore di comandi di completamento è derivato da un <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, che è in attesa di un evento di creazione di visualizzazione di testo e converte la visualizzazione da un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, che consente di aggiungere il comando per la catena di comando di shell di Visual Studio, per un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Poiché questa classe è un'esportazione MEF, si può anche essere utilizzato per importare i servizi necessari per il gestore del comando.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Per implementare il provider di gestore di comandi di completamento  
  
1.  Aggiungere un file denominato `TestCompletionCommandHandler`.  
  
2.  Aggiungi queste istruzioni using:  
  
     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  Aggiungere una classe denominata `TestCompletionHandlerProvider` che implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Esportazione di questa classe con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "gestore di completamento token", un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "testo normale" e un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> di <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  Importazione di <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, che consente la conversione da un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>e un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> che consente l'accesso ai servizi di Visual Studio standard.  
  
     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  Implementare il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodo per creare il gestore del comando.  
  
     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## <a name="implementing-the-completion-command-handler"></a>Implementazione del gestore di comandi di completamento  
 Poiché il completamento delle istruzioni è attivato da sequenze di tasti, è necessario implementare la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia per ricevere ed elaborare le sequenze di tasti che trigger, eseguire il commit e chiudere la sessione di completamento.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Per implementare il gestore del comando di completamento  
  
1.  Aggiungere una classe denominata `TestCompletionCommandHandler` che implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
     [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
     [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2.  Aggiungere campi privati per il gestore del comando successivo (a cui passare il comando), la visualizzazione del testo, il provider del gestore di comando (che consente di accedere a vari servizi) e una sessione di completamento:  
  
     [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
     [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3.  Aggiungere un costruttore che imposta la visualizzazione del testo e i campi del provider e aggiunge il comando per la catena di comando:  
  
     [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
     [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4.  Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo passando il comando lungo:  
  
     [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
     [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5.  Implementare il metodo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Quando questo metodo riceve un tasto di scelta rapida, è necessario eseguire una di queste operazioni:  
  
    -   Consentire il carattere di essere scritti nel buffer e quindi attivare o filtrare il completamento. (I caratteri stampabili farlo.)  
  
    -   Eseguire il commit al completamento, ma non consentono il carattere da scrivere nel buffer. (Gli spazi vuoti, Tab ed Enter eseguita quando viene visualizzata una sessione di completamento.)  
  
    -   Consenti il comando da passare al gestore successivo. (Tutti gli altri comandi.)  
  
     Poiché questo metodo può visualizzare l'interfaccia utente, chiamare il metodo <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> per assicurarsi che non viene chiamato in un contesto di automazione:  
  
     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6.  Questo codice è un metodo privato che attiva la sessione di completamento:  
  
     [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
     [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7.  L'esempio successivo è un metodo privato che annulla la sottoscrizione dal <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> evento:  
  
     [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
     [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione CompletionTest ed eseguirlo nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Per compilare e testare la soluzione CompletionTest  
  
1.  Compilare la soluzione.  
  
2.  Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3.  Creare un file di testo e digitare un testo che include la parola "Aggiungi".  
  
4.  Mentre si digita prima "a" e quindi "d", verrà visualizzato un elenco che contiene "addition" e "adattamento". Si noti che inoltre sia selezionata. Quando si digita un altro "d", l'elenco deve contenere solo "inoltre" ora selezionata. È possibile eseguire il commit "addition" premendo il tasto barra spaziatrice, Tab o INVIO oppure chiudere l'elenco digitando Esc o qualsiasi altra chiave.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)