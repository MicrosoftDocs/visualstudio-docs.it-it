---
title: Struttura VSPackage (origine controllo VSPackage) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 168aa0f7b93d20afaa30924dc17f05e0cac465bb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struttura VSPackage (origine controllo VSPackage)
Origine controllo pacchetto SDK fornisce indicazioni per la creazione di un VSPackage che consentono a un implementatore di controllo di origine per integrare la propria funzionalità di controllo di origine con il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente. Un VSPackage è un componente COM che in genere viene caricato su richiesta per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) in base ai servizi che vengono annunciati dal pacchetto in relative voci del Registro di sistema. Ogni pacchetto VSPackage deve implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Un VSPackage in genere utilizza i servizi offerti dal [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE e proffers alcuni servizi propri.  
  
 Un pacchetto VSPackage dichiara le voci di menu e consente di stabilire un stato elemento predefinito tramite il file con estensione vsct. Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE visualizza le voci di menu in questo stato finché non viene caricato il pacchetto VSPackage. Successivamente, l'implementazione di VSPackage il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo viene chiamato per abilitare o disabilitare le voci di menu.  
  
## <a name="source-control-package-characteristics"></a>Caratteristiche di pacchetto di origine controllo  
 Pacchetto VSPackage è perfettamente integrato in un controllo del codice sorgente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 La semantica di VSPackage include:  
  
-   Interfaccia che deve essere implementata in quanto un VSPackage (il `IVsPackage` interfaccia)  
  
-   Implementazione del comando dell'interfaccia utente (file con estensione vsct e implementazione del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia)  
  
-   Registrazione del pacchetto VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Il controllo del codice sorgente VSPackage deve comunicare con queste altre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entità:  
  
-   Progetti  
  
-   Editor  
  
-   Soluzioni  
  
-   WINDOWS  
  
-   La tabella documenti in esecuzione  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Servizi dell'ambiente Visual Studio che possono essere utilizzati  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Servizio SVsRegisterScciProvider  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>Interfacce VSIP implementazione e la chiamata  
 Un pacchetto di controllo di origine è un pacchetto VSPackage e pertanto può interagire direttamente con altri pacchetti VSPackage che sono registrati con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Per garantire l'ampia gamma di controllo del codice sorgente, un controllo del codice sorgente VSPackage è possibile gestire con interfacce fornite da progetti o la shell.  
  
 Ogni progetto in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> venga riconosciuta come un progetto all'interno di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Tuttavia, questa interfaccia non specializzata sufficiente per controllo del codice sorgente. I progetti che si prevedono siano in origine controllano implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Questa interfaccia viene utilizzata per il controllo del codice sorgente VSPackage per eseguire query di un progetto per il relativo contenuto e fornire i glifi e informazioni di associazione (le informazioni necessarie per stabilire una connessione tra il percorso del server e il percorso del disco di un progetto che si trova sotto controllo del codice sorgente).  
  
 Il controllo del codice sorgente pacchetto VSPackage implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, che a sua volta consente ai progetti di registrarsi per controllo del codice sorgente e recuperare le icone di stato.  
  
 Per un elenco completo di interfacce necessario prendere in considerazione un controllo del codice sorgente VSPackage, vedere [servizi correlati e le interfacce](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Le interfacce e i servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)