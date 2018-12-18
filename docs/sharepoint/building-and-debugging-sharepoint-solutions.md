---
title: Compilazione e debug delle soluzioni SharePoint | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c74c65d091f170b19357058b1d8ae407b2125e77
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="building-and-debugging-sharepoint-solutions"></a>Compilazione e debug delle soluzioni SharePoint
  In generale, compilazione e debug delle soluzioni SharePoint è quella della compilazione e debug di altri tipi di progetti in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Gli argomenti di questa sezione illustrano le differenze esistenti.  
  
## <a name="project-output-for-sharepoint-solutions"></a>Output del progetto per le soluzioni SharePoint  
 Compilazione di soluzioni SharePoint crea un file di pacchetto (con estensione wsp) della soluzione e assembly. Nella tabella seguente mostra i percorsi dei file durante una compilazione.  
  
|Elemento di compilazione|Cartella di output|  
|----------------|-------------------|  
|Assembly, il database di programma (PDB) e i file con estensione wsp.|*NomeProgetto*\bin\debug o *ProjectName*\bin\Release.|  
|File di elemento di progetto SharePoint.|*NomeProgetto*\pkg\debug o *ProjectName*\pkg\release|  
|Compilare i file intermedi.|*NomeProgetto*\obj\debug o *ProjectName*\obj\release|  
|File intermedi di pacchetto.|*NomeProgetto*\pkgobj\debug o *ProjectName*\pkgobj\release|  
  
## <a name="building-sharepoint-solutions"></a>Compilazione di soluzioni SharePoint  
 Per compilare soluzioni SharePoint, il computer di sviluppo deve avere la versione corretta del server di SharePoint installato. In caso contrario, la creazione di soluzioni di SharePoint è lo stesso di quello di altri tipi di progetti in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per ulteriori informazioni, vedere [procedura: compilare soluzioni SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## <a name="debugging-and-testing-sharepoint-solutions"></a>Debug e test di soluzioni SharePoint  
 Prima del debug, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] copia il pacchetto con estensione wsp nel server SharePoint, viene attivato il sito e funzionalità con ambito Web e in alcuni casi, viene avviato il progetto. In altri casi, potrebbe essere necessario aprire manualmente il progetto. Per ulteriori informazioni, vedere [risoluzione dei problemi delle soluzioni di SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) e [debug delle soluzioni SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="debugging-and-verifying-sharepoint-solutions-by-using-alm-features"></a>Verifica e debug delle soluzioni di SharePoint utilizzando le funzionalità ALM  
 Con le funzionalità di Visual Studio ALM, ad esempio il testing unità e IntelliTrace, è possibile individuare con maggiore precisione i problemi delle soluzioni di SharePoint. Con la profilatura è possibile individuare e identificare aree problematiche delle prestazioni nelle soluzioni di SharePoint. Per ulteriori informazioni, vedere [verifica e debug del codice SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) e [profilatura delle prestazioni di applicazioni SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## <a name="security-during-the-build-process"></a>Sicurezza durante il processo di compilazione  
 Per creare un pacchetto o distribuire soluzioni di SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] deve disporre dell'autorizzazione per copiare i file nel server SharePoint. È necessario eseguire [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] come un processo con privilegi elevato e l'utente account deve essere un amministratore della raccolta siti nel server SharePoint. Inoltre, è necessario specificare se il progetto è una soluzione creata mediante sandbox o una soluzione farm. Per ulteriori informazioni, vedere [le differenze tra creata mediante sandbox e soluzioni Farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="using-the-clean-command"></a>Uso del comando Pulisci  
 Quando una soluzione SharePoint viene installata in un server SharePoint per il debug, il **Pulisci** comando non Disinstalla la soluzione. In alternativa, è necessario disattivare le funzionalità tramite la configurazione di SharePoint.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Esplorazione di connessioni di SharePoint tramite Esplora Server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  