---
title: Differenze tra creata mediante sandbox e soluzioni Farm | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2340e7001d159b34bba62e9ba4ef90c34845b156
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Differenze tra soluzioni create mediante sandbox e soluzioni farm
  Quando si compila una soluzione di SharePoint, distribuisce nel server SharePoint e collega un debugger per eseguire il debug. Il processo utilizzato per eseguire il debug della soluzione dipende dall'impostazione della proprietà soluzione creata mediante sandbox: soluzione creata mediante sandbox o soluzione farm.  
  
 Per ulteriori informazioni, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="farm-solutions"></a>Soluzioni farm  
 Soluzioni farm, che sono ospitate nel processo di lavoro IIS (W3WP.exe), eseguire il codice che può influenzare l'intera farm. Quando si esegue il debug di un progetto SharePoint la cui proprietà soluzione creata mediante sandbox è impostata su "soluzione farm", viene riciclato il pool di applicazioni IIS del sistema prima di SharePoint viene ritratta o distribuisce la funzionalità in modo da rilasciare qualsiasi file bloccato dal processo di lavoro IIS. Solo il pool di applicazioni IIS per l'URL del sito del progetto SharePoint viene riciclato.  
  
## <a name="sandboxed-solutions"></a>Soluzioni create mediante sandbox  
 Soluzioni create mediante sandbox, che sono ospitate nel processo di lavoro soluzione con codice di utente SharePoint (SPUCWorkerProcess.exe), eseguire il codice che influiscono solo la raccolta di siti della soluzione. Poiché nel processo di lavoro IIS non eseguire soluzioni create mediante sandbox, necessario riavviare il pool di applicazioni IIS né il server IIS. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Collega il debugger al processo SPUCWorkerProcess che il servizio SPUserCodeV4 in SharePoint e controlli. Non è necessario che il processo SPUCWorkerProcess riciclo per caricare la versione più recente della soluzione.  
  
## <a name="either-type-of-solution"></a>Dei tipi di soluzione  
 Con questi tipi di soluzioni, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] anche collega il debugger per il browser per abilitare il debug di script sul lato client. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Usa il motore per lo scopo di debug di script. Per abilitare il debug degli script, è necessario modificare le impostazioni del browser predefinito quando viene richiesto.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Collega il debugger solo per i processi W3WP o SPUCWorkerProcess in esecuzione il sito corrente. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Collega anche componenti gestiti COM Plus e flusso di lavoro motori di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug delle soluzioni SharePoint](../sharepoint/debugging-sharepoint-solutions.md)   
 [Compilazione e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md)  
  
  