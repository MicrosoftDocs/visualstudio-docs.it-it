---
title: Esecuzione tabella Document | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4a49a5267fcccbde60e194e3fc58b0f6b6ea7552
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="running-document-table"></a>Tabella documenti in esecuzione
L'IDE gestisce l'elenco di tutti i documenti attualmente aperti in una struttura interna denominata tabella document (RDT) in esecuzione. Questo elenco include tutti i documenti aperti in memoria, indipendentemente dal fatto che tali documenti sono in corso di modifica. Un documento è un elemento in modo permanente, inclusi i file in un progetto o file di progetto principale (ad esempio, un file con estensione vcxproj).  
  
## <a name="elements-of-the-running-document-table"></a>Elementi della tabella Document in esecuzione  
 La tabella document in esecuzione che contiene le voci seguenti.  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Moniker del documento|Stringa che identifica in modo univoco l'oggetto dati del documento. Potrebbe essere il percorso di file assoluto per un sistema di progetto che gestisce i file (ad esempio, C:\MyProject\MyFile). Questa stringa viene utilizzata anche per i progetti salvati in archivi diverso dal file System, ad esempio stored procedure in un database. In questo caso, il sistema del progetto di creare una stringa univoca che possa riconoscere e possibilmente analizzare per determinare come archiviare il documento.|  
|Proprietario di gerarchia|Oggetto gerarchia a cui appartiene il documento, come rappresentato da un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia.|  
|ID elemento|Identificatore dell'elemento di un elemento specifico all'interno della gerarchia. Questo valore è univoco tra tutti i documenti nella gerarchia proprietario di questo documento, ma questo valore non deve necessariamente essere univoco in gerarchie diverse.|  
|Oggetto dati del documento|Come minimo, si tratta di un `IUnknown`<br /><br /> . L'IDE non richiede alcuna particolare interfaccia oltre il `IUnknown` interfaccia per l'oggetto dati del documento dell'editor personalizzato. Tuttavia, per un editor standard, implementazione dell'editor del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaccia necessaria per gestire le chiamate di persistenza di file dal progetto. Per ulteriori informazioni, vedere [il salvataggio di un documento Standard](../../extensibility/internals/saving-a-standard-document.md).|  
|Flag|Flag che controllano se il documento viene salvato, se viene applicato un blocco di lettura o di modifica e così via, può essere specificati quando vengono aggiunte voci di RDT. Per altre informazioni, vedere l'enumerazione <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.|  
|Conteggio dei blocchi di modifica|Conteggio dei blocchi di modifica. Un blocco di modifica indica che alcuni editor aperto il documento per la modifica. Quando si esegue la transizione a zero il conteggio dei blocchi di modifica, l'utente viene richiesto di salvare il documento, se è stato modificato. Ad esempio, ogni volta che si apre un documento in un editor utilizzando il **nuova finestra** comando, viene aggiunto un blocco di modifica per il documento nel RDT. Affinché un blocco di modifica da impostare, il documento deve avere una gerarchia o ID elemento|  
|Conteggio dei blocchi in lettura|Conteggio dei blocchi in lettura. Un blocco di lettura indica che il documento viene letto tramite un meccanismo, ad esempio una procedura guidata. Un blocco di lettura contiene un documento attivo nella RDT continuando a indicare che il documento non può essere modificato. È possibile impostare un blocco di lettura, anche se il documento non dispone di una gerarchia o ID elemento Questa funzionalità consente di aprire un documento in memoria e immetterlo nel RDT senza il documento da proprietà di qualsiasi gerarchia. Questa funzionalità viene utilizzata raramente.|  
|Proprietario di blocco|Un'istanza di un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaccia. Il detentore del blocco viene implementato dalle funzionalità, quali procedure guidate che aprono e modificano i documenti all'esterno di un editor. Un proprietario di blocco consente la funzionalità aggiungere un blocco di modifica al documento per impedire che il documento sia stato chiuso mentre è in corso di modifica. In genere, modificare i blocchi vengono aggiunti solo per le finestre di documento (ovvero, Editor).|  
  
 Ogni voce di RDT ha una gerarchia univoca o ID elemento associato, che corrisponde in genere a un nodo del progetto. In genere sono di proprietà disponibili per la modifica di tutti i documenti da una gerarchia. Voci di RDT controllano quale progetto, o, in modo più accurato, gerarchia, in cui appartiene l'oggetto dati del documento in fase di modifica. Utilizzando le informazioni di RDT, l'IDE può impedire un documento viene aperto da più progetti contemporaneamente.  
  
 La gerarchia anche controlla la persistenza dei dati e utilizza le informazioni di RDT per aggiornare il **salvare** e **Salva con nome** finestre di dialogo. Quando l'utente modifica un documento e quindi scegliere il **uscita** comando il **File** menu, l'IDE richiede l'immissione con il **Salva modifiche** la finestra di dialogo per visualizzare tutti i progetti e gli elementi di progetto che attualmente vengono modificati. Ciò consente agli utenti di scegliere quale di questi documenti da salvare. L'elenco dei documenti per salvare (ovvero, i documenti che sono state apportate modifiche) viene generato dal RDT. Tutti gli elementi che si prevedono di vedere nel **Salva modifiche** la finestra di dialogo dopo l'uscita dell'applicazione deve avere i record nel RDT. Il RDT coordina i documenti vengono salvati e se viene chiesto all'utente su un salvataggio operazione utilizzando i valori specificati nella voce del flag per ogni documento. Per ulteriori informazioni sui flag di RDT, vedere il <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> enumerazione.  
  
## <a name="edit-locks-and-read-locks"></a>Blocchi di modifica e blocchi di lettura  
 Blocchi di modifica e blocchi di lettura risiedono nel RDT. Di incrementi di finestra di documento e decrementa di bloccare la modifica. Pertanto, quando un utente apre una nuova finestra del documento, la modifica blocco conteggio viene incrementato di uno. Quando il numero di blocchi di modifica raggiunge lo zero, viene segnalata la gerarchia di rendere persistente o salvare i dati per il documento associato. La gerarchia può quindi rendere persistenti i dati in qualsiasi modo, incluso il salvataggio come file o come un elemento in un repository. È possibile utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> metodo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfaccia aggiunge i blocchi di modifica e leggere i blocchi e <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> metodo per rimuovere i blocchi.  
  
 In genere, quando viene creata un'istanza di questa finestra del documento per un editor, la cornice della finestra vengono automaticamente aggiunti un blocco di modifica per il documento di RDT. Tuttavia, se si crea una visualizzazione personalizzata di un documento che non utilizza una finestra del documento standard (ovvero, non implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaccia), è necessario impostare il proprio blocco di modifica. In una procedura guidata, ad esempio, un documento viene modificato senza viene aperto in un editor. Affinché i blocchi del documento deve essere aperto da procedure guidate e le entità simili, è necessario implementare queste entità di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaccia. Per registrare il detentore del blocco del documento, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> (metodo) e passare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implementazione. In questo modo il detentore del blocco di documento aggiunge il RDT. Un altro scenario per l'implementazione di un titolare di blocco del documento è se si apre un documento tramite una finestra degli strumenti speciale. In questo caso, non è possibile chiudere il documento per la finestra degli strumenti. Tuttavia, la registrazione di un titolare di blocco del documento nel RDT, l'IDE può chiamare l'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> metodo per la richiesta di chiusura del documento.  
  
## <a name="other-uses-of-the-running-document-table"></a>Altri usi della tabella Document in esecuzione  
 Altre entità nell'IDE di utilizzare il RDT per ottenere informazioni sui documenti. Ad esempio, il gestore di controllo di origine utilizza il RDT per indicare al sistema di ricaricare un documento nell'editor, dopo che ottiene la versione più recente del file. A tale scopo, il gestore di controllo di origine cerca i file in RDT per vedere se uno di essi è aperto. Se sono quindi la gestione del controllo origine verifica innanzitutto che implementa la gerarchia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodo. Se il progetto non implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (metodo), quindi l'origine controllare gestione controlli per un'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> metodo sull'oggetto dati documento direttamente.  
  
 L'IDE Usa anche il RDT a resurface (portare in primo piano) un documento aperto, se un utente richiede che il documento. Per ulteriori informazioni, vedere [i file di visualizzazione utilizzando il comando File Apri](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Per determinare se un file è aperto nel RDT, effettuare una delle seguenti.  
  
-   Query per il moniker del documento (ovvero, il percorso del documento completo) scoprire se l'elemento è aperto.  
  
-   Per porre il sistema di progetto per il percorso completo dei documenti e quindi cercare l'elemento nel RDT, utilizzare l'ID di gerarchia o un elemento.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)   
 [Salvataggio permanente e tabella documenti in esecuzione](../../extensibility/internals/persistence-and-the-running-document-table.md)