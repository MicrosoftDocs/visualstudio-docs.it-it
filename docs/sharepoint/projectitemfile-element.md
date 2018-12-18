---
title: ProjectItemFile (elemento) | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cc9aa921c83bfe26c424e73fd53ad577e1aa527e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="projectitemfile-element"></a>Elemento ProjectItemFile
  Rappresenta un file di SharePoint, ad esempio file di elemento di funzionalità, per includere l'elemento di progetto quando viene distribuito in SharePoint.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## <a name="type"></a>Tipo  
 **ProjectItemFileType**  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|**Origine**|Richiesto **xs: String** attributo.<br /><br /> Il nome del file da distribuire con l'elemento del progetto.|  
|**Destinazione**|Parametro facoltativo **xs: String** attributo.<br /><br /> Il percorso in cui verrà distribuito il file in SharePoint, rispetto alla cartella radice di distribuzione. Cartella radice di distribuzione è determinata dal tipo di distribuzione specificato per il **tipo** attributo. Se il **destinazione** attributo non è specificato, il file verrà distribuito in una cartella con il nome specificato nella **origine** attributo.<br /><br /> Per ulteriori informazioni, vedere le descrizioni per il **percorso distribuzione** e **radice distribuzione** gli elementi nel progetto di proprietà di SharePoint [lo sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Richiesto **xs: String** attributo.<br /><br /> Il tipo di distribuzione per il file. Per ulteriori informazioni sui possibili valori, vedere la descrizione per il **tipo di distribuzione** proprietà degli elementi di progetto SharePoint in [lo sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[File](../sharepoint/files-element.md)|Specifica i file da includere con l'elemento di progetto SharePoint quando viene distribuito in SharePoint.|  
  
## <a name="remarks"></a>Note  
 I file di SharePoint a cui fa riferimento in genere in **ProjectItemFile** elementi includono i file di elemento di funzionalità (Elements), file di schema per le definizioni di elenco (Schema.xml) e file di definizione delle Web Part per le Web part (WebPart).  
  
## <a name="element-information"></a>Informazioni sull'elemento  
  
|||  
|-|-|  
|**Spazio dei nomi**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nome dello schema**|Schema di elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo schema degli elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  