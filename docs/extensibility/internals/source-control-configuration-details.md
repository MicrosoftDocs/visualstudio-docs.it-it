---
title: I dettagli di configurazione di controllo dell'origine | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2f8a2cc2f1c13c46b3ac4838d95ce588d0461347
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-configuration-details"></a>Dettagli di configurazione di controllo di origine
Per implementare il controllo del codice sorgente, è necessario configurare correttamente il sistema di progetto o un editor per eseguire le operazioni seguenti:  
  
-   Richiedere l'autorizzazione per la transizione allo stato modificato  
  
-   Richiedere l'autorizzazione per salvare un file  
  
-   Richiedere l'autorizzazione per aggiungere, rimuovere o rinominare i file del progetto  
  
## <a name="request-permission-to-transition-to-changed-state"></a>Richiedere l'autorizzazione per la transizione allo stato modificato  
 Un progetto o un editor deve richiedere l'autorizzazione per eseguire la transizione allo stato modificato (dirty) chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>. Ogni editor che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> deve chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e ricevere l'approvazione per modificare il documento dall'ambiente prima di restituire `True` per `M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`. Un progetto è essenzialmente un editor per un file di progetto e di conseguenza, ha la responsabilità stesso per l'implementazione del rilevamento dello stato modificato per il file di progetto come un editor di testo per i file. L'ambiente gestisce la modifica dello stato della soluzione, ma è necessario gestire la modifica dello stato di qualsiasi oggetto, la soluzione fa riferimento, ma non memorizzi, ad esempio un file di progetto o i relativi elementi. In generale, se il progetto o l'editor è responsabile della gestione della persistenza per un elemento, quindi è responsabile dell'implementazione del rilevamento dello stato modificato.  
  
 In risposta al `IVsQueryEditQuerySave2::QueryEditFiles` chiama, l'ambiente è possibile eseguire le operazioni seguenti:  
  
-   Rifiutare la chiamata per la modifica, nel qual caso l'editor o un progetto deve rimanere nello stato unchanged (parziale).  
  
-   Indica che i dati del documento devono essere ricaricati. Per un progetto, l'ambiente ricarica i dati per il progetto. Un editor deve ricaricare i dati dal disco tramite il relativo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementazione. In entrambi i casi, è possibile modificare il contesto del progetto o un editor quando vengano caricato di nuovo i dati.  
  
 È un'attività complessa e difficoltosa adattare appropriato `IVsQueryEditQuerySave2::QueryEditFiles` chiamate in una codebase esistente. Di conseguenza, queste chiamate devono essere integrate durante la creazione del progetto o dell'editor.  
  
## <a name="request-permission-to-save-a-file"></a>Richiedere l'autorizzazione per salvare un File  
 Prima di un progetto o l'editor consente di salvare un file, è necessario chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>. Per i file di progetto, queste chiamate vengono completate automaticamente per la soluzione, che conosce il momento di salvare un file di progetto. Editor sono responsabili per eseguire queste chiamate a meno che l'implementazione dell'editor di `IVsPersistDocData2` utilizza la funzione di supporto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>. Se l'editor implementa `IVsPersistDocData2` in questo modo, quindi la chiamata a `IVsQueryEditQuerySave2::QuerySaveFile` o `IVsQueryEditQuerySave2::QuerySaveFiles` viene effettuata automaticamente.  
  
> [!NOTE]
>  Sempre effettuare queste chiamate alla modalità preemptive, vale a dire alla volta quando l'editor è in grado di ricevere un annullamento.  
  
## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Richiedere l'autorizzazione per aggiungere, rimuovere o rinominare i file del progetto  
 Prima di un progetto può aggiungere, rinominare o rimuovere un file o directory, è necessario chiamare appropriata `IVsTrackProjectDocuments2::OnQuery*` metodo per richiedere l'autorizzazione dall'ambiente. Se l'autorizzazione viene concessa, quindi il progetto deve completare l'operazione e quindi chiamare appropriata `IVsTrackProjectDocuments2::OnAfter*` metodo per notificare l'ambiente che è stata completata l'operazione. Il progetto deve chiamare i metodi del <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfaccia per tutti i file (ad esempio, file speciali) e non solo i file padre. Chiamate di file sono obbligatori, ma le chiamate di directory sono facoltative. Se il progetto contiene le informazioni di directory, quindi deve chiamare appropriata <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> metodi, ma se non dispone di queste informazioni, l'ambiente verrà derivare informazioni di directory.  
  
 Il progetto non deve chiamare i metodi di `IVsTrackProjectDocuments2` nel progetto aprire o chiudere. I listener che si desiderano che queste informazioni all'avvio possono attendere il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> eventi ed eseguire l'iterazione attraverso la soluzione per trovare le informazioni necessarie. Al momento della chiusura, queste informazioni non sono necessarie. `IVsTrackProjectDocuments2`viene fornito dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.  
  
 Per ogni componente, ridenominazione e azione di rimozione, è disponibile un `OnQuery*` (metodo) e un `OnAfter*` metodo. Chiamare il `OnQuery*` metodo per richiedere l'autorizzazione per aggiungere, rinominare o rimuovere il file o directory. Chiamare il `OnAfter*` metodo dopo che il file o la directory è stato aggiunto, rinominare o rimosso e lo stato del progetto riflette il nuovo stato.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)