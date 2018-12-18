---
title: 'Elenco di controllo: Creazione di un servizio di linguaggio Legacy | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad407d85213bf640b8631e9fbcb12b681ac87406
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="checklist-creating-a-legacy-language-service"></a>Elenco di controllo: Creazione di un servizio di linguaggio Legacy
L'elenco di controllo seguente sono riepilogati i passaggi di base è necessario eseguire per creare un servizio di linguaggio per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor principale. Per integrare il servizio di linguaggio in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è necessario creare un analizzatore di espressioni di debug. Per ulteriori informazioni, vedere [la scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) nel [estensibilità di Visual Studio Debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="steps-for-creating-a-language-service"></a>Passaggi per la creazione di un servizio di linguaggio  
  
1.  Implementare l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  
  
    -   Nel pacchetto VSPackage, implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaccia per fornire il servizio di linguaggio.  
  
    -   Rendere il servizio di linguaggio disponibili per l'ambiente di sviluppo integrato (IDE) nei <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementazione.  
  
2.  Implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> un'interfaccia della classe di servizio lingua principale.  
  
     Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaccia è il punto iniziale dell'interazione tra l'editor di componenti di base e il servizio di linguaggio.  
  
### <a name="optional-features"></a>Funzionalità facoltative  
 Le funzionalità seguenti sono facoltative e possono essere implementate in qualsiasi ordine. Queste funzionalità aumentano le funzionalità del servizio di linguaggio.  
  
-   Colorazione della sintassi  
  
     Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. L'implementazione di questa interfaccia deve essere le informazioni di parser per restituire le informazioni di colore appropriato.  
  
     Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodo restituisce il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaccia. Un'istanza separata di rappresentazione viene creata per ogni buffer di testo, quindi è necessario implementare la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaccia separatamente. Per ulteriori informazioni, vedere [colorazione della sintassi in un servizio di linguaggio Legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
-   Finestra del codice  
  
     Implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfaccia per abilitare il servizio di linguaggio ricevere una notifica di creazione di una nuova finestra del codice.  
  
     Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metodo restituisce il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfaccia. Il servizio di linguaggio possa quindi aggiungere speciale dell'interfaccia utente alla finestra del codice in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>. Il servizio di linguaggio possa anche eseguire qualsiasi elaborazione speciale, ad esempio l'aggiunta di un filtro di visualizzazione di testo in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.  
  
-   Filtro di visualizzazione di testo  
  
     Per garantire il completamento delle istruzioni in un servizio di linguaggio, è necessario intercettare alcuni comandi di gestire in altro modo la visualizzazione del testo. Per intercettare questi comandi, completare i passaggi seguenti:  
  
    -   Implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> partecipare i comandi dell'editor catena e handle di comando.  
  
    -   Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> (metodo) e passare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementazione.  
  
    -   Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> metodo quando si scollega dalla vista in modo che questi comandi non vengono passati all'utente.  
  
     I comandi che devono essere gestiti dipendono dai servizi forniti. Per ulteriori informazioni, vedere [comandi importanti per i filtri di servizio di linguaggio](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
    > [!NOTE]
    >  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interfaccia deve essere implementata per l'oggetto stesso come il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia.  
  
-   Completamento istruzioni  
  
     Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.  
  
     Supporta il comando di completamento istruzione (vale a dire <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) e chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo nel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia, passando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaccia. Per ulteriori informazioni, vedere [il completamento delle istruzioni in un servizio di linguaggio Legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
-   Suggerimenti (metodo)  
  
     Implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaccia per fornire dati per la finestra di suggerimento di metodo.  
  
     Installare il filtro di visualizzazione di testo per gestire i comandi in modo appropriato, in modo da sapere quando visualizzare una finestra del suggerimento dati (metodo). Per ulteriori informazioni, vedere [informazioni sul parametro in un servizio di linguaggio Legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
-   Marcatori di errore  
  
     Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.  
  
     Creazione di oggetti di marcatore che implementano l'errore di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia e chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> , passando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia dell'oggetto indicatore di errore.  
  
     Ogni indicatore di errore in genere gestisce un elemento nella finestra Elenco attività.  
  
-   Elementi dell'elenco attività  
  
     Implementare una classe elemento di attività fornisce il <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> interfaccia.  
  
     Implementare una classe del provider di attività fornisce il <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> interfaccia e <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> interfaccia.  
  
     Implementare una classe di enumeratore attività fornendo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> interfaccia.  
  
     Registrare il provider di attività con l'elenco di attività <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> metodo.  
  
     Ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interfaccia chiamando il provider di servizi del servizio di linguaggio con il GUID del servizio <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.  
  
     Creare oggetti di elementi di attività e chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> metodo nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interfaccia quando sono presenti nuove o aggiornate di attività.  
  
-   Elementi di attività di commento  
  
     Utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interfaccia e <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interfaccia per ottenere i token di attività di commento.  
  
     Ottenere un <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interfaccia dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> servizio.  
  
     Ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interfaccia dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> metodo.  
  
     Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> interfaccia per attendere le modifiche nell'elenco dei token.  
  
-   struttura  
  
     Esistono diverse opzioni per il supporto di struttura. Ad esempio, è possibile supportare la **Comprimi alle definizioni** comando, fornire aree della struttura controllata editor o supportare le aree di gestito dal client. Per ulteriori informazioni, vedere [procedura: fornire supporto espanso struttura in un servizio di linguaggio Legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
-   Registrazione del servizio di linguaggio  
  
     Per ulteriori informazioni su come registrare un servizio di linguaggio, vedere [la registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service2.md) e [gestione VSPackage](../../extensibility/managing-vspackages.md).  
  
-   Guida sensibile al contesto  
  
     Fornire contesto all'editor in uno dei modi seguenti:  
  
    -   Fornire contesto per i marcatori di testo mediante l'implementazione di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfaccia.  
  
 Fornire tutto il contesto utente implementando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un servizio di linguaggio Legacy](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)