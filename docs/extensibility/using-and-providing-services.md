---
title: Utilizzo e fornisce servizi | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: "41"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fbba5070af77e1509ed3b3840a2045ae0f2c12b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="using-and-providing-services"></a>Utilizzando e servizi
Un servizio è un contratto tra due pacchetti VSPackage. Un VSPackage offre un set specifico di interfacce per un altro VSPackage da utilizzare. Ad esempio, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] offre il <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> del servizio a qualsiasi VSPackage carica. Questo servizio fornisce il <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaccia, che consente di scrivere nel log attività. Per ulteriori informazioni, vedere [procedura: utilizzare il registro attività](../extensibility/how-to-use-the-activity-log.md).  
  
 VSPackage possono offrire servizi di autonomamente usando il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interface...  
  
 Visual Studio offre servizi importanti, ad esempio le operazioni seguenti:  
  
|Servizio IDE|Descrizione|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Fornisce l'accesso all'IDE servizi di gestione con funzionalità di base, i pacchetti VSPackage e del Registro di sistema.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornisce la funzionalità correlate all'interfaccia utente nell'IDE, ad esempio la possibilità di creare strumenti e finestre di documento e windowing di base.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornisce funzionalità base associate alla soluzione, ad esempio la possibilità di enumerare i progetti, creare nuovi progetti e monitorare le modifiche del progetto.|  
  
## <a name="in-this-section"></a>In questa sezione  
 [Nozioni fondamentali sui servizi](../extensibility/internals/service-essentials.md)  
 Visualizza gli elementi importanti di un servizio di Visual Studio.  
  
 [Procedura: Ottenere un servizio](../extensibility/how-to-get-a-service.md)  
 Viene illustrato come richiedere (utilizzare) un servizio.  
  
 [Procedura: Fornire un servizio](../extensibility/how-to-provide-a-service.md)  
 Viene descritto come fornire un servizio.  
  
 [Procedura: Fornire un servizio asincrono di Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Viene descritto come fornire un servizio asincrono.  
  
 [Procedura: Risolvere i problemi relativi ai servizi](../extensibility/how-to-troubleshoot-services.md)  
 Vengono descritti i problemi comuni e vengono fornite soluzioni a essi.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)