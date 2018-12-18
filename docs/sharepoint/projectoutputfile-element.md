---
title: ProjectOutputFile (elemento) | Documenti Microsoft
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
helpviewer_keywords: ProjectOutputFile element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5b57f00960629d65f264f22532a16202d6ae5d7a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="projectoutputfile-element"></a>Elemento ProjectOutputFile
  Rappresenta l'output di un progetto separato per includere l'elemento di progetto quando viene distribuito in SharePoint.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## <a name="type"></a>Tipo  
 **ProjectOutputFileType**  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|**ID progetto**|Richiesto **xs: String** attributo.<br /><br /> Il GUID del progetto dipendente che è l'output a cui si desidera includere. Corrisponde alla **ProjectGuid** elemento nel file di progetto dipendente.|  
|**ProjectPath**|Richiesto **xs: String** attributo.<br /><br /> Il percorso relativo, incluso il nome di file di progetto, del progetto dipendente che è l'output a cui che si desidera includere. Questo percorso è relativo alla cartella radice del progetto SharePoint che contiene l'elemento di progetto SharePoint.|  
|**Destinazione**|Parametro facoltativo **xs: String** attributo.<br /><br /> Il percorso in cui l'output del progetto dipendente da distribuire nel server SharePoint, rispetto alla cartella radice di distribuzione. Cartella radice di distribuzione è determinata dal tipo di distribuzione specificato per il **tipo** attributo.<br /><br /> Per ulteriori informazioni, vedere le descrizioni per il **percorso distribuzione** e **radice distribuzione** gli elementi nel progetto di proprietà di SharePoint [lo sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Richiesto **xs: String** attributo.<br /><br /> Il tipo di distribuzione da utilizzare per l'output del progetto dipendente. Per ulteriori informazioni sui possibili valori, vedere la descrizione per il **tipo di distribuzione** proprietà degli elementi di progetto SharePoint in [lo sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[File](../sharepoint/files-element.md)|Specifica i file da includere con l'elemento di progetto SharePoint quando viene distribuito in SharePoint.|  
  
## <a name="remarks"></a>Note  
 Utilizzare il **ProjectOutputFile** elemento da includere nella distribuzione dell'elemento di progetto SharePoint, l'output di un progetto. È possibile specificare un altro progetto o il progetto stesso che contiene l'elemento del progetto. Per ulteriori informazioni, vedere [che fornisce informazioni sui pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informazioni sull'elemento  
  
|||  
|-|-|  
|**Spazio dei nomi**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nome dello schema**|Schema di elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo Schema elemento di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Fornisce informazioni sui pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  