---
title: Configurazione di progetto per la Gestione distribuzione | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4859e47f8a7ade34a920e4d8e2fac3be58508de3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="project-configuration-for-managing-deployment"></a>Configurazione di progetto per la distribuzione di gestione
Distribuzione indica l'azione fisicamente lo spostamento di elementi di output da un processo di compilazione nella posizione prevista per il debug e l'installazione. Ad esempio, un'applicazione Web potrebbe essere compilata in un computer locale e quindi inserita nel server.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]supporta due metodi che proietta può essere coinvolto nella distribuzione:  
  
-   L'oggetto del processo di distribuzione.  
  
-   Come la gestione del processo di distribuzione.  
  
 Prima di possono distribuire soluzioni, è innanzitutto necessario aggiungere un progetto di distribuzione per configurare le opzioni di distribuzione. Se il progetto di distribuzione non esiste già, viene chiesto se si desidera crearne uno quando si seleziona **Distribuisci soluzione** dal **compilare** menu o una soluzione rapida. Fare clic su **Sì** apre il **Aggiungi nuovo progetto** la finestra di dialogo con il **remoto distribuzione guidata** progetto selezionato.  
  
 La distribuzione guidata remoto viene richiesto per il tipo di applicazione (Windows o Web), gruppi di output del progetto da includere, eventuali file aggiuntivi da includere e il computer remoto che si desidera distribuire. L'ultima pagina della procedura guidata visualizza un riepilogo delle opzioni selezionate.  
  
 I progetti che sono soggetti a un processo di distribuzione di generare elementi di output che devono essere spostati in un ambiente alternativo. Questi elementi sono descritti come parametri per l'output di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> interfaccia, il cui primario scopo se si desidera consentire agli output di gruppo di progetti. Per ulteriori informazioni sull'implementazione di `IVsProjectCfg2`, vedere [configurazione per l'Output del progetto](../../extensibility/internals/project-configuration-for-output.md).  
  
 Progetti di distribuzione, che gestisce il processo di distribuzione, abilitare il comando Distribuisci e rispondono quando si seleziona questo comando. Implementano progetti di distribuzione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaccia per eseguire la distribuzione e di effettuare chiamate al <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> interfaccia report eventi dello stato di distribuzione.  
  
 Le configurazioni è possono specificare le dipendenze che interessano le operazioni di compilazione o distribuzione. Compilare o distribuire le dipendenze sono progetti che devono essere compilati o distribuiti prima o dopo le configurazioni stessi vengono compilate o distribuite. Vengono descritti le dipendenze di compilazione tra progetti con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> l'interfaccia e distribuire le dipendenze con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfaccia. Per ulteriori informazioni, vedere [configurazione di progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)   
 [Configurazione di progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)   
 [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)