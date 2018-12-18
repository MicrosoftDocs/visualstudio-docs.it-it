---
title: Salvataggio di un documento Standard | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0cdfb4631420f6803e6434bd67b93bd713cfd1f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="saving-a-standard-document"></a>Salvataggio di un documento Standard
L'ambiente gestisce Save, Salva con nome e salvare tutti i comandi. Quando un utente seleziona **salvare**, **Salva con nome**, o **Salva tutto** dal **File** menu o chiude la soluzione, determinando un  **Salvare tutti**, verifica quanto segue.  
  
 ![Editor standard](../../extensibility/internals/media/public.gif "pubblica")  
Salvare, Salva con nome e la gestione di un editor standard del comando Salva tutto  
  
 Questa procedura è descritta nei passaggi seguenti:  
  
1.  Quando il **salvare** e **Salva con nome** comandi sono selezionati, l'ambiente utilizza il <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> del servizio per determinare la finestra del documento attivo e pertanto gli elementi che devono essere salvati. Una volta che è nota la finestra del documento attivo, l'ambiente trova il puntatore di gerarchia e l'identificatore dell'elemento (ID elemento) per il documento della tabella document in esecuzione. Per ulteriori informazioni, vedere [tabella documenti in esecuzione](../../extensibility/internals/running-document-table.md).  
  
     Quando il **Salva tutto** comando è selezionato, l'ambiente utilizza le informazioni nella tabella documenti in esecuzione per compilare l'elenco di tutti gli elementi da salvare.  
  
2.  Quando la soluzione riceve un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> chiamata, scorre il set di elementi selezionati (vale a dire le selezioni multiple esposte dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servizio).  
  
3.  Su ogni elemento nella selezione, la soluzione utilizza l'indicatore di misura di gerarchia per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> metodo per determinare se il **salvare** comando di menu deve essere abilitato. Se uno o più elementi sono dirty, il **salvare** command è abilitato. Se la gerarchia utilizza un editor standard, i delegati di gerarchia per l'esecuzione di query dirty stato all'editor chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metodo.  
  
4.  Ogni elemento selezionato è stato modificato, la soluzione utilizza l'indicatore di misura di gerarchia per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metodo sulle gerarchie appropriate.  
  
     È comune per la gerarchia di utilizzare un editor standard di modificare il documento. In questo caso, i dati del documento dell'oggetto per tale editor devono supportare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaccia. Al momento della ricezione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> chiamata al metodo, il progetto deve informare l'editor che viene salvato il documento chiamando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> metodo sull'oggetto dati di documento. L'editor può consentire l'ambiente gestire il **Salva con nome** nella finestra di dialogo chiamando `Query Service` per il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> interfaccia. Restituisce un puntatore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia. L'editor deve quindi chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> , passando un puntatore per l'editor <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> implementazione mediante la `pPersistFile` parametro. L'ambiente, quindi esegue l'operazione di salvataggio e fornisce il **Salva con nome** la finestra di dialogo per l'editor. L'ambiente richiama l'editor con <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.  
  
5.  Se l'utente sta tentando di salvare un documento senza nome (ovvero, un documento non sono stato salvato in precedenza), un comando Salva con nome viene effettivamente eseguito.  
  
6.  Per il comando Salva con nome, l'ambiente consente di visualizzare la finestra di dialogo Salva con nome, la richiesta all'utente un nome di file.  
  
     Se è stato modificato il nome del file, quindi la gerarchia è responsabile per l'aggiornamento della cornice di documento informazioni memorizzate nella cache chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).  
  
 Se il **Salva con nome** la gerarchia è importante per il percorso del documento, il comando Sposta la posizione del documento, quindi la gerarchia è responsabile per la consegna il proprietario della finestra di documento aperto in un'altra gerarchia. Ad esempio, ciò si verifica se il progetto rileva se il file è un file all'interno o esterno (File esterno) in relazione al progetto. Utilizzare la procedura seguente per modificare la proprietà di un file al progetto file esterni.  
  
## <a name="changing-file-ownership"></a>Modifica della proprietà di File  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Per modificare la proprietà di file al progetto file esterni  
  
1.  Eseguire una query del servizio per il <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> interfaccia.  
  
     Un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> viene restituito.  
  
2.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) metodo di trasferimento del documento nella nuova gerarchia. Gerarchia di cui eseguire il comando Salva con nome chiama questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)