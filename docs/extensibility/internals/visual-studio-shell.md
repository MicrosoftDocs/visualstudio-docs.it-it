---
title: Shell di Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 71b624cee0e55f95f90a86eac943828bbc26ac97
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell è l'agente primario di integrazione in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. La shell fornisce le funzionalità necessarie per permettere ai pacchetti VSPackage condividere i servizi comuni. Poiché l'obiettivo dell'architettura di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consiste principalmente la funzionalità di assegnazione in VSPackage, la shell è un framework per fornire funzionalità di base e supportare la comunicazione tra tra il componente del package VS.  
  
## <a name="shell-responsibilities"></a>Responsabilità della shell  
 La shell include le responsabilità principali seguenti:  
  
-   Supporto (tramite le interfacce COM) elementi di base dell'interfaccia utente (UI). Tra i menu predefiniti e le barre degli strumenti, le cornici della finestra di documento o finestre figlio di interfaccia a documenti multipli (MDI) e le cornici della finestra dello strumento e supporto di ancoraggio.  
  
-   Gestione di un elenco di tutti i documenti attualmente aperti in una tabella documenti in esecuzione (RDT) per coordinare la persistenza dei documenti e per garantire che di un documento non è aperto in più modo o in modalità incompatibile.  
  
-   Che supporta l'interfaccia di gestione dei comandi e di routing dei comandi, `IOleCommandTarget`.  
  
-   Durante il caricamento di pacchetti VSPackage in momenti appropriati. Caricamento ritardato un VSPackage è necessario per migliorare le prestazioni della shell.  
  
-   Gestione di determinati i servizi condivisi, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, che fornisce funzionalità di base della shell, e <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, che fornisce funzionalità di windowing di base.  
  
-   Gestire i file della soluzione (sln). Soluzioni contengono gruppi di progetti correlati, simili al file di area di lavoro (con estensione DSW) in Visual C++ 6.0.  
  
-   Selezione della shell a livello di rilevamento, il contesto e valuta. La shell registra i seguenti tipi di elementi:  
  
    -   Il progetto corrente  
  
    -   L'elemento del progetto corrente o ItemID corrente <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   La selezione corrente per il **proprietà** finestra o `SelectionContainer`  
  
    -   Il contesto dell'interfaccia utente, ID o CmdUIGuids che controllano la visibilità dei comandi, menu e barre degli strumenti  
  
    -   Gli elementi attualmente attivi, ad esempio la finestra attiva, un documento e un gestore di annullamento  
  
    -   Gli attributi di contesto dell'utente che Guida dinamica  
  
 La shell consente di eseguire anche la comunicazione tra pacchetti VSPackage installati e i servizi correnti. Supporta le funzionalità di base della shell e li rende disponibili per tutti i pacchetti VSPackage integrati in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Queste funzionalità di base includono i seguenti elementi:  
  
-   **Sulle** schermata iniziale e finestra di dialogo  
  
-   **Aggiungere nuovo e Aggiungi elemento esistente** finestre di dialogo  
  
-   **Visualizzazione classi-** finestra e **Visualizzatore oggetti**  
  
-   **Riferimenti** finestra di dialogo  
  
-   **Struttura documento** finestra  
  
-   **Guida dinamica** finestra  
  
-   **Trovare** e **sostituire**  
  
-   **Apri progetto** e **Apri File** caselle di dialogo il **nuovo** menu  
  
-   **Le opzioni** della finestra di dialogo di **strumenti** menu  
  
-   **Proprietà** finestra  
  
-   **Esplora soluzioni**  
  
-   **Elenco attività** finestra  
  
-   **Casella degli strumenti**  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)