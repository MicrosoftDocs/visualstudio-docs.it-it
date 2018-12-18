---
title: Blocco titolare gestione dei documenti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: df782cd974adcd589824e8a47cd0249842bd8d48
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="document-lock-holder-management"></a>Gestione dei documenti blocco titolare
La tabella di documento in esecuzione (RDT) mantiene un conteggio di documenti aperti e presentano i blocchi di modifica. È possibile inserire un blocco di modifica su un documento di RDT quando viene modificata a livello di codice in background senza visualizzare un documento aperto in una finestra del documento. Questa funzionalità viene spesso utilizzata nelle finestre di progettazione che modificano più file tramite un'interfaccia utente grafica.  
  
## <a name="document-lock-holder-scenarios"></a>Scenari di blocco titolare del documento  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>File di una dipendenza dal File "a" con "b"  
 Si consideri una situazione in cui si implementa un editor standard "A" per il tipo di file "a" e tutti i file di tipo "a" è un riferimento a dipendenza (o) un file di tipo "b". Un editor standard "B" non esiste per i file di tipo "b". Quando viene aperto l'editor "A" file "a" it recupera il riferimento al file corrispondente "b". File "b" non è visualizzato, ma può modificarlo editor "A". Editor "A" Ottiene un riferimento ai dati del documento del file "b" dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodo e viene inoltre gestito un blocco di modifica nel file "b". Al termine dell'editor "A" modifica il file "b" è possibile diminuire il blocco di modifica count nei file "b" chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> metodo. È possibile omettere questo passaggio se è stato chiamato il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> (metodo) con il parametro `dwRDTLockType` impostato su <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>"B" viene aperto da un altro Editor  
 Nel caso in cui il file "b" è già aperto da editor "B" quando "A" editor tenta di aprirlo, esistono due scenari separati per gestire:  
  
-   Se il file "b" è aperto in un editor compatibile, è necessario disporre dell'editor "A" Registra un blocco di modifica del documento nel file "b" utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metodo. Dopo l'editor "A" modifica il file "b", annullare la registrazione del documento Modifica blocco usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> metodo.  
  
-   Se il file "b" è aperto in una modalità incompatibile, è possibile consentire il tentativo di apertura del file "b" Editor "A" hanno esito negativo oppure è possibile consentire la visualizzazione associata a editor "A" parzialmente aprirà e visualizza un messaggio di errore appropriato. Il messaggio di errore è necessario indicare all'utente di chiudere il file "b" in editor non compatibile e quindi aprire nuovamente i file "a" tramite l'editor "A". È anche possibile implementare il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> per richiedere all'utente di chiudere il file "b" che viene aperto nell'editor non compatibile. Se l'utente chiude il file "b", l'apertura del file "a" in "A" di editor proseguirà normalmente.  
  
## <a name="additional-document-edit-lock-considerations"></a>Blocco considerazioni sulla modifica di documenti aggiuntive  
 Si verifica un comportamento diverso se editor "A" è l'unico editor che dispone di un documento Modifica blocco nel file "b", quello che si avrebbe se editor "B" contiene inoltre un documento edit blocco nel file "b". In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **Progettazione classi** è un esempio di una finestra di progettazione visiva che non dispone di un blocco di modifica per il file di codice associato. Ovvero, se l'utente dispone di un diagramma classi aprire in visualizzazione progettazione e contemporaneamente aprire il file di codice associato e se l'utente modifica il file di codice, ma non salvare le modifiche, le modifiche vanno inoltre perdute al file di diagramma (con estensione CD) della classe. Se il **Progettazione classi** è l'unico documento Modifica blocco per il file di codice, l'utente non viene chiesto di salvare le modifiche quando si chiude il file di codice. L'IDE chiede di salvare le modifiche solo dopo che l'utente chiude il **Progettazione classi**. Le modifiche salvate vengono riflesse in entrambi i file. Se entrambi i **Progettazione classi** e l'editor di file di codice mantenuti attivi i blocchi di modifica del documento nel file di codice, quindi l'utente viene richiesto di salvare quando si chiude il file di codice o il modulo. A questo punto le modifiche salvate vengono riflesse nel modulo sia il file di codice. Per ulteriori informazioni sui diagrammi classi, vedere [utilizzo dei diagrammi classi (Progettazione classi)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Si noti che se è necessario inserire un blocco di modifica per un documento per un editor diverso, è necessario implementare la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaccia.  
  
 Numero di volte un progettista dell'interfaccia utente che modifica i file di codice a livello di codice apporta modifiche a più di un file. In questi casi il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> metodo gestisce il salvataggio di uno o più documenti tramite il **si desidera salvare le modifiche agli elementi seguenti?** la finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabella documenti in esecuzione](../extensibility/internals/running-document-table.md)   
 [Salvataggio permanente e tabella documenti in esecuzione](../extensibility/internals/persistence-and-the-running-document-table.md)