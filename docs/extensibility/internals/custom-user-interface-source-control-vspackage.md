---
title: Interfaccia utente personalizzata (origine controllo VSPackage) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3d3c223b45d0228781779a73f057ef3518374344
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="custom-user-interface-source-control-vspackage"></a>Interfaccia utente personalizzata (origine controllo VSPackage)
Un pacchetto VSPackage dichiara le voci di menu e i relativi stati predefinito tramite il file di Visual Studio Command Table (vsct). Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) consente di visualizzare le voci di menu negli stati predefiniti finché non viene caricato il pacchetto VSPackage. Successivamente, il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo viene chiamato per abilitare o disabilitare le voci di menu.  
  
 Un pacchetto VSPackage può impostare una chiave del Registro di sistema in modo che il pacchetto VSPackage può essere caricato automaticamente in base a un contesto dell'interfaccia utente di comando, sebbene in genere un controllo origine pacchetto VSPackage deve caricare su richiesta anziché solo il passaggio a un particolare contesto dell'interfaccia utente. Per ulteriori informazioni sulla chiave del Registro di sistema AutoLoadPackages, vedere [gestione VSPackage](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>Interfaccia utente di VSPackage  
 Un pacchetto di controllo di origine viene implementato come un pacchetto VSPackage e non utilizzare qualsiasi interfaccia utente da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ogni controllo del codice sorgente VSPackage è necessario specificare i proprio elementi dell'interfaccia utente, ad esempio voci di menu, gruppi di menu, finestre degli strumenti, barre degli strumenti e qualsiasi interfaccia utente obbligatoria per impostare le opzioni specifiche per il controllo del codice sorgente VSPackage. Questi elementi dell'interfaccia utente possono essere abilitati in modo statico o dinamico. Elementi dell'interfaccia utente statici sono definiti in un file con estensione vsct e vengono visualizzati se viene caricato il pacchetto VSPackage o non. Elementi dell'interfaccia utente dinamici potrebbero essere visibili a seconda del contesto dell'interfaccia utente un comando specifico, ad esempio <xref:EnvDTE.Constants.vsContextNoSolution>, o come risultato di una chiamata al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo. La visibilità degli elementi dell'interfaccia utente dinamici è conforme con la strategia per il caricamento ritardato di VSPackage.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Vincoli di interfaccia utente su VSPackage di controllo di origine  
 Poiché non è possibile rimuovere il controllo del codice sorgente VSPackage dall'IDE di dopo essere stato caricato, il pacchetto VSPackage deve essere in grado di passare uno stato inattivo. Quando un pacchetto VSPackage riceve una notifica che non è più attivo, il pacchetto VSPackage disabilita la relativa interfaccia utente e ignora qualsiasi interazione con l'IDE esterno. L'implementazione di VSPackage il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo deve nascondere i comandi quando il pacchetto VSPackage non è attivo.  
  
 Ogni controllo del codice sorgente pacchetto VSPackage deve implementare il `IVsSccProvider` interfaccia. Due metodi sull'interfaccia e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, deve essere implementata dal pacchetto VSPackage.  
  
 Il pacchetto VSPackage può sottoscritti a vari eventi dell'IDE, implementati dal controllo del codice sorgente di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>e così via. Inoltre, il pacchetto VSPackage possibile abbia implementato interfacce di callback abilitato del Registro di sistema, ad esempio il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>. Questi devono tutti essere ignorati quando è inattivo.  
  
 L'elenco seguente mostra le interfacce interessate lo stato attivo su un controllo del codice sorgente VSPackage:  
  
-   Rilevare gli eventi di documenti di progetto.  
  
-   Eventi della soluzione.  
  
-   Interfacce di persistenza di soluzione. Quando è inattivo, pacchetti non dovrebbero scrivere in file con estensione sln e suo.  
  
-   Estensioni della proprietà.  
  
 Obbligatorio <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, e anche eventuali interfacce facoltative associate al controllo del codice sorgente, non vengono chiamati quando il controllo del codice sorgente VSPackage è inattivo.  
  
 Quando il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] avvio IDE, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] imposta il contesto del comando dell'interfaccia utente per l'ID del controllo origine predefinita corrente ID del pacchetto VSPackage. In questo modo l'interfaccia utente statico del controllo origine attiva VSPackage venga visualizzato nell'IDE senza effettivamente caricare il pacchetto VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]viene sospeso per il pacchetto VSPackage registrare con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> prima delle chiamate a VSPackage.  
  
 La tabella seguente descrive i dettagli specifici su come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE nasconde gli elementi dell'interfaccia utente diversi.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|-------------|-----------------|  
|Menu e barre degli strumenti|Il package del controllo del codice sorgente è necessario impostare gli stati di visibilità iniziali dal menu e barra degli strumenti con l'ID di pacchetto di controllo di origine nel [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) sezione del file con estensione vsct. In questo modo il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE impostare lo stato delle voci di menu in modo corretto senza caricare il pacchetto VSPackage e la chiamata di un'implementazione del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo.|  
|Finestre degli strumenti|Il controllo del codice sorgente VSPackage nasconde tutte le finestre di che sua proprietà quando viene reso inattivo.|  
|Pagine delle opzioni di controllo del codice sorgente specifiche VSPackage|La chiave del Registro di sistema HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts consente a un pacchetto VSPackage di impostare i contesti in cui richiede le pagine di opzioni da visualizzare. Una voce del Registro di sistema in questa chiave dovranno essere creato utilizzando il servizio ID (SID) del servizio di controllo di origine e assegnarle un valore DWORD pari a 1. Ogni volta che l'interfaccia utente si verifica un evento in un contesto VSPackage è registrato con il controllo del codice sorgente, verrà chiamato il pacchetto VSPackage se è attiva.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [Gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md)