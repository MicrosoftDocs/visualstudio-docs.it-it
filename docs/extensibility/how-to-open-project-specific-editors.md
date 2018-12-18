---
title: 'Procedura: apertura degli editor specifici del progetto | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 66ac0837649b42dc238eac57829c713b2bf83e3a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-project-specific-editors"></a>Procedura: apertura degli editor specifici del progetto
Se un file di elemento aperto da un progetto è intrinsecamente associato a specifico editor per il progetto, il progetto è necessario aprire il file utilizzando un editor specifico del progetto. Il file non può essere delegato down il meccanismo dell'IDE per la selezione di un editor. Anziché utilizzare un editor di bitmap standard, ad esempio, è possibile utilizzare questa opzione editor specifici del progetto per specificare un editor di bitmap specifico che riconosce le informazioni nel file che è univoco per il progetto.  
  
 Le chiamate a IDE il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodo quando si determina che un file deve essere aperto da un progetto specifico. Per ulteriori informazioni, vedere [i file di visualizzazione utilizzando il comando File Apri](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Utilizzare le linee guida seguenti per implementare il `OpenItem` metodo per il progetto è aperto un file utilizzando un editor specifico del progetto.  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Per implementare il metodo OpenItem con un editor specifico del progetto  
  
1.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodo (RDT_EditLock) per determinare se il file (oggetto dati del documento) è già aperto.  
  
    > [!NOTE]
    >  Per ulteriori informazioni sui dati del documento e gli oggetti di visualizzazione di documenti, vedere [dati del documento e visualizzazione del documento in editor personalizzati](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2.  Se il file è già aperto, il file di resurface chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metodo e specificando un valore di IDO_ActivateIfOpen per il `grfIDO` parametro.  
  
     Se il file è aperto e il documento è di proprietà di un progetto diverso dal progetto chiamante, verrà visualizzato un avviso all'utente che è l'editor viene aperto da un altro progetto. Finestra di dialogo file viene quindi esposto.  
  
3.  Se il buffer di testo (oggetto dati del documento) è già aperto e si desidera aggiungere un'altra visualizzazione, è responsabile per l'associazione di tale visualizzazione. L'approccio consigliato per creare un'istanza di una vista (oggetto visualizzazione del documento) dal progetto, è come segue:  
  
    1.  Chiamare `QueryService` sul <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> servizio per ottenere un puntatore per il <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> interfaccia.  
  
    2.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> metodo per creare un'istanza della classe di visualizzazione documento.  
  
4.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> metodo, specificando l'oggetto visualizzazione del documento.  
  
     Questo metodo siti l'oggetto visualizzazione del documento in una finestra del documento.  
  
5.  Eseguire le chiamate appropriate a uno di <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> metodi.  
  
     A questo punto, la vista deve essere completamente inizializzato e pronto per essere aperto.  
  
6.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodo per visualizzare e aprire la visualizzazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Apertura e salvataggio di elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procedura: apertura degli editor Standard](../extensibility/how-to-open-standard-editors.md)   
 [Procedura: Aprire gli editor per i documenti aperti](../extensibility/how-to-open-editors-for-open-documents.md)