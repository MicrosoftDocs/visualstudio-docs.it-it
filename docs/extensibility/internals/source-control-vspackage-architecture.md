---
title: Architettura di VSPackage del controllo origine | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 002dea54b63a78975d56464319614d369a9b2318
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-vspackage-architecture"></a>Architettura di VSPackage del controllo di origine
Un pacchetto di controllo del codice sorgente è un package VS che utilizza i servizi di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE sono disponibili. In cambio, un pacchetto di controllo del codice sorgente fornisce le sue funzionalità come un servizio di controllo di origine. Inoltre, un pacchetto di controllo del codice sorgente è un'alternativa più versatile rispetto a un plug-in per l'integrazione di controllo del codice sorgente in controllo del codice sorgente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Un controllo del codice sorgente plug-in che implementa l'API di plug-in controllo di origine sia supportata da un contratto di tipo strict. Ad esempio, un plug-in non è possibile sostituire il valore predefinito [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia utente (UI). Inoltre, l'API plug-in controllo di origine non consente un plug-in implementare il proprio modello di origine del controllo. Un pacchetto di controllo del codice sorgente, tuttavia, consente di superare entrambe queste limitazioni. Un pacchetto di controllo del codice sorgente ha il controllo completo dell'esperienza di controllo origine di un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utente. Inoltre, un pacchetto di controllo del codice sorgente è possibile utilizzare il proprio modello di controllo di origine e la logica e può definire tutte le interfacce utente correlate al controllo di origine.  
  
## <a name="source-control-package-components"></a>Controllo del codice sorgente componenti del pacchetto  
 Come illustrato nel diagramma dell'architettura, un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componente denominato lo Stub del controllo origine è un package VS che integra un pacchetto di controllo del codice sorgente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Origine controllo Stub gestisce le attività seguenti.  
  
-   Fornisce l'interfaccia utente comune che è necessario per la registrazione del pacchetto di controllo del codice sorgente.  
  
-   Carica un pacchetto di controllo del codice sorgente.  
  
-   Imposta un pacchetto di controllo del codice sorgente come attivo o inattivo.  
  
 Stub di controllo di origine per il servizio attivo per il pacchetto di controllo del codice sorgente e indirizza tutte le chiamate in ingresso del servizio dall'IDE di tale pacchetto.  
  
 Il pacchetto di scheda di controllo di origine è un controllo speciale di origine del pacchetto che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce. Questo pacchetto è il componente centrale per il supporto di origine plug-in del controllo in base alle API plug-in controllo di origine. Quando un plug-in controllo del codice sorgente è attivo plug-in, lo Stub del controllo origine invia gli eventi per il pacchetto di scheda di controllo di origine. A sua volta, il pacchetto di origine controllo scheda comunica con il plug-in controllo del codice sorgente tramite l'API plug-in controllo di origine e fornisce anche un'interfaccia utente che è comune per tutti i plug-in controllo codice sorgente predefinita.  
  
 Quando un pacchetto di controllo del codice sorgente è il pacchetto active, d'altra parte, lo Stub del controllo origine comunicare direttamente con il pacchetto utilizzando la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfacce di controllo del codice sorgente pacchetto. Il pacchetto di controllo del codice sorgente è responsabile per l'hosting di un proprio controllo del codice sorgente dell'interfaccia utente.  
  
 ![Rappresentazione grafica dell'architettura di controllo origine](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
 Per un pacchetto di controllo del codice sorgente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non fornisce alcun controllo codice sorgente o un'API per l'integrazione. Ciò si differenzia l'approccio descritto in [la creazione di un plug-in controllo origine](../../extensibility/internals/creating-a-source-control-plug-in.md) in cui il plug-in controllo del codice sorgente deve implementare un set di funzioni e i callback rigida.  
  
 Come qualsiasi VSPackage, un pacchetto di controllo del codice sorgente è un oggetto COM che può essere creato utilizzando `CoCreateInstance`. Il pacchetto VSPackage rende disponibile per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Dopo aver creata un'istanza, un pacchetto VSPackage riceve un puntatore di sito e un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaccia che fornisce l'accesso VSPackage ai servizi disponibili e interfacce nell'IDE.  
  
 La scrittura di un pacchetto VSPackage basato su controllo del codice sorgente richiede competenze di programmazione più avanzate rispetto alla scrittura di un API plug-in controllo di origine basato su un plug-in.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Introduzione](../../extensibility/internals/getting-started-with-source-control-vspackages.md)