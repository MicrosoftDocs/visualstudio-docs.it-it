---
title: FeatureProperties (elemento) | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperties element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 991d2c57da8a1fc45fba266cdafe38000cd3d594
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="featureproperties-element"></a>Elemento FeatureProperties
  Rappresenta una raccolta di valori di proprietà che sono inclusi in una funzione quando viene distribuito in SharePoint. Dopo aver distribuita una funzionalità, è possibile accedere i valori delle proprietà nel codice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<FeatureProperties>  
  <FeatureProperty.../>  
</FeatureProperties>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una proprietà personalizzata, nel formato di chiave/valore.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento di progetto SharePoint. Questo è l'elemento radice obbligatorio del file con estensione spdata.|  
  
## <a name="remarks"></a>Note  
 Per ulteriori informazioni sulle proprietà di funzionalità, vedere [che fornisce informazioni sui pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informazioni sull'elemento  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|**Spazio dei nomi**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nome dello schema**|Schema di elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo Schema elemento di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  