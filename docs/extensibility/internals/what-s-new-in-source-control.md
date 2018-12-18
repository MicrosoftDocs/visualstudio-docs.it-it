---
title: "Novità &#39; s New in controllo del codice sorgente | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9fc1c5956a4d3c20f8b9abec36d554f3ec56c8c9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="what39s-new-in-source-control"></a>Novità &#39; s New in controllo del codice sorgente
In [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] è possibile fornire una soluzione di controllo del codice sorgente integrato eccessivamente mediante l'implementazione di un controllo del codice sorgente VSPackage. In questa sezione vengono descritte le funzionalità di controllo del codice sorgente VSPackage e viene fornita una panoramica dei passaggi di implementazione.  
  
## <a name="the-source-control-vspackage"></a>Il controllo di origine pacchetto VSPackage  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]supporta due tipi di soluzioni di controllo di origine. Tutte le versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è comunque possibile integrare un API plug-in controllo di origine basato su un plug-in. È inoltre possibile creare un pacchetto VSPackage per controllo del codice sorgente che fornisce una profonda integrazione con, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] percorso adatto per le soluzioni di controllo di origine che richiedono un elevato livello di complessità e autonomia.  
  
 Un VSPackage può aggiungere qualsiasi tipo di funzionalità per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Un controllo del codice sorgente VSPackage fornisce una funzionalità di controllo completo di origine per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], dall'interfaccia utente presentato all'utente per le comunicazioni back-end con il controllo del codice sorgente.  
  
 L'implementazione di un controllo del codice sorgente VSPackage richiede una strategia di "tutto o niente". L'autore di un controllo del codice sorgente VSPackage necessario investire una quantità significativa di lavoro richiesto nell'implementazione di un numero di interfacce di controllo di origine e di nuovi elementi dell'interfaccia utente (finestre di dialogo, menu e barre degli strumenti) per coprire l'intero controllo del codice sorgente, nonché le interfacce necessarie per integrare correttamente con qualsiasi pacchetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 La procedura seguente offre una panoramica generale di ciò che è necessario per implementare un package del controllo del codice sorgente. Per informazioni dettagliate, vedere [creando un pacchetto VSPackage controllo origine](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1.  Creare un VSPackage che proffers un servizio di controllo origine privata.  
  
2.  Implementare le interfacce in servizi correlati al controllo codice sorgente che vengono offerti da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (ad esempio, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interface).  
  
3.  Registrare il controllo del codice sorgente VSPackage.  
  
4.  Implementare tutte controllo del codice sorgente dell'interfaccia utente, incluse le voci di menu, finestre di dialogo, barre degli strumenti e menu di scelta rapida.  
  
5.  Tutti gli eventi relativi al controllo origine vengono passati al controllo del codice sorgente VSackage quando è attiva e devono essere gestita dal pacchetto VSPackage.  
  
6.  Controllo del codice sorgente VSPackage deve essere in ascolto degli eventi, ad esempio quelli implementazione il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> interfaccia nonché gli eventi di traccia progetto documento Trusted (come implementato dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfaccia) e intraprendere le azioni necessarie.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Panoramica](../../extensibility/internals/source-control-integration-overview.md)   
 [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)