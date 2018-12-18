---
title: Riferimento allo Schema di progetto SharePoint elemento | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b039b1cf31a04a24819b03114c661a3ab1b108a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sharepoint-project-item-schema-reference"></a>Riferimento allo schema degli elementi di progetto SharePoint
  Per convalidare il contenuto dei file spdata, Visual Studio utilizza lo schema di elemento di progetto SharePoint. Un file con estensione spdata specifica il contenuto e il comportamento di un elemento di progetto SharePoint. Per ulteriori informazioni sul contenuto di elementi di progetto SharePoint, vedere [la creazione di modelli di elemento e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Lo schema di elemento di progetto SharePoint viene denominato ProjectItemModelSchema.xsd e viene installato per impostazione predefinita in % programmi (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas.  
  
 L'elemento radice è il [ProjectItem](../sharepoint/projectitem-element.md) elemento. Nella tabella seguente vengono descritti tutti gli elementi definiti nello schema.  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Rappresenta una raccolta di elementi di dati personalizzati associati all'elemento di progetto SharePoint.|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Rappresenta un elemento di dati personalizzato associato all'elemento di progetto SharePoint, nel formato di chiave/valore. La chiave e valore devono essere stringhe.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Rappresenta una raccolta di valori di proprietà che sono inclusi in una funzione quando viene distribuito in SharePoint. Dopo aver distribuita una funzionalità, è possibile accedere i valori delle proprietà nel codice.|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Rappresenta una proprietà personalizzata che è inclusa in una funzionalità quando viene distribuito in SharePoint. Dopo aver distribuita una funzionalità, è possibile accedere alla proprietà nel codice.|  
|[File](../sharepoint/files-element.md)|Specifica i file da distribuire con l'elemento di progetto SharePoint, ad esempio un file di elemento di funzionalità o l'output di un progetto.|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento di progetto SharePoint.|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Rappresenta un file di SharePoint, ad esempio file di elemento di funzionalità, per includere l'elemento di progetto quando viene distribuito in SharePoint.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Rappresenta una cartella mappata.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Rappresenta l'output di un progetto da includere nell'elemento di progetto quando viene distribuito in SharePoint.|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Rappresenta un controllo ASPX o una Web Part che è designato come protetto per qualsiasi utente di accedere in qualsiasi pagina ASPX nel sito di SharePoint.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Rappresenta una raccolta di controlli ASPX e Web part che sono definiti come sicuri per tutti gli utenti di accedere in qualsiasi pagina ASPX nel sito di SharePoint.|  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di modelli di elemento e di modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
  
  