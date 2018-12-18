---
title: Determinare quale Editor apre un File in un progetto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d8fe054fa8e630b2f6c54cb78ef75b6c10ff74d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Determinazione di un File in un progetto che verrà aperto l'Editor
Quando un utente apre un file in un progetto, l'ambiente passa attraverso un processo di polling, infine aprire l'editor appropriato o la finestra di progettazione per il file di. La procedura iniziale utilizzata dall'ambiente è uguale per gli editor standard e personalizzati. L'ambiente Usa una serie di criteri durante il polling quali editor da utilizzare per aprire un file e il pacchetto VSPackage deve coordinare con l'ambiente durante questo processo.  
  
 Ad esempio, quando un utente seleziona il **aprire** dal **File** dal menu e quindi sceglie `filename`. RTF (o qualsiasi altro file con estensione. RTF), l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implementazione per ogni progetto, infine ciclicamente tutte le istanze di progetto nella soluzione. Progetti di restituiscono un set di flag che specificano le attestazioni in un documento in base alla priorità. Usa la priorità più alta, l'ambiente chiama appropriata <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodo. Per ulteriori informazioni sul processo di polling, [aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Il progetto file esterni attestazioni tutti i file non richiesti da altri progetti. In questo modo, editor personalizzati possono aprire documenti prima di aprirli editor standard. Se un file le attestazioni di un progetto file esterni, l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo per aprire il file con un editor standard. L'ambiente controlla l'elenco interno di un editor registrato per uno che gestisce i file RTF. Questo elenco si trova nella seguente chiave del Registro di sistema:  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{<`editor factory guid`>} \Extensions]  
  
 L'ambiente controlla inoltre gli identificatori di classe nella chiave HKEY_CLASSES_ROOT\CLSID per tutti gli oggetti che hanno la sottochiave DocObject. Se viene trovata l'estensione di file, una versione incorporata dell'applicazione, ad esempio Microsoft Word, viene creata sul posto in Visual Studio. Questi oggetti documento devono essere un file compositi che implementano il <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> interfaccia o l'oggetto deve implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfaccia.  
  
 Se nessun factory editor per i file RTF nel Registro di sistema, quindi esegue la ricerca dell'ambiente nella chiave HKEY_CLASSES_ROOT \\chiave RTF e verrà aperto l'editor specificato non esiste. Se l'estensione di file non viene trovata in HKEY_CLASSES_ROOT, l'ambiente utilizza l'editor di testo principale di Visual Studio per aprire il file se è un file di testo.  
  
 Se l'editor di testo di base non riesce, che si verifica che se il file non è un file di testo, l'ambiente utilizza il relativo editor binario per il file.  
  
 Se l'ambiente di trovare un editor per l'estensione. RTF nel relativo Registro di sistema, carica il pacchetto VSPackage che implementa questa factory editor. L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodo nel nuovo pacchetto VSPackage. Le chiamate a VSPackage `QueryService` per `SID_SVsRegistorEditor`, usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metodo per registrare la factory editor con l'ambiente.  
  
 Ora l'ambiente controlla nuovamente l'elenco interno di editor registrato per trovare la factory editor appena registrato per i file RTF. L'ambiente chiama l'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> (metodo), passando il tipo di nome e la visualizzazione di file da creare.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>