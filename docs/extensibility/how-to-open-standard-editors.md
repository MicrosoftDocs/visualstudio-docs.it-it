---
title: 'Procedura: apertura degli editor Standard | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dcf36dc8f4ef818a84719bc534a09ecf30baf76f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-standard-editors"></a>Procedura: apertura degli editor Standard
Quando si apre un editor standard, è consentire l'IDE di determinare un editor standard per un tipo di file, anziché specificare un editor specifico del progetto per il file.  
  
 Completare la procedura seguente per implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodo. Si aprirà un file di progetto in un editor standard.  
  
### <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Per implementare il metodo OpenItem con un editor standard  
  
1.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> (`RDT_EditLock`) per determinare se il file di dati oggetto del documento è già aperto.  
  
2.  Se il file è già aperto, il file di resurface chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metodo, specificando un valore di `IDO_ActivateIfOpen` per il `grfIDO` parametro.  
  
     Se il file è aperto e il documento è di proprietà di un progetto diverso rispetto al progetto chiamante, il progetto riceve un avviso che è l'editor viene aperto da un altro progetto. Finestra di dialogo file viene quindi esposto.  
  
3.  Se il documento non è aperto o non in esecuzione tabella document, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo (`OSE_ChooseBestStdEditor`) per aprire un editor standard per il file.  
  
     Quando si chiama il metodo, l'IDE esegue le attività seguenti:  
  
    1.  L'IDE analizza gli editor / {guidEditorType} / sottochiave Extensions nel Registro di sistema per determinare quale editor è possibile aprire il file e ha la priorità più alta per eseguire questa operazione.  
  
    2.  Dopo l'IDE ha determinato quale editor è possibile aprire il file, l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>. Implementazione dell'editor di questo metodo restituisce le informazioni necessarie per l'ambiente IDE chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> e del sito il documento appena aperto.  
  
    3.  Infine, l'IDE carica il documento tramite l'interfaccia di solito persistenza, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.  
  
    4.  Se l'IDE ha rilevato in precedenza che la gerarchia o un elemento della gerarchia è disponibile, l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> metodo sul progetto per ottenere un contesto a livello di progetto <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> puntatore passare di nuovo in con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> chiamata al metodo.  
  
4.  Restituire un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> puntatore all'IDE quando si chiama l'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> al progetto se si desidera che il contesto di get editor dal progetto.  
  
     I servizi aggiuntivi di offerta di progetto per l'editor consente di eseguire questo passaggio.  
  
     Se la visualizzazione del documento o un oggetto visualizzazione del documento è stato individuato correttamente in una cornice di finestra, l'oggetto viene inizializzato con i relativi dati chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Apertura e salvataggio di elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procedura: apertura degli editor specifici del progetto](../extensibility/how-to-open-project-specific-editors.md)   
 [Procedura: apertura degli editor di documenti aperti](../extensibility/how-to-open-editors-for-open-documents.md)   
 [Visualizzazione di file tramite il comando Apri file](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)