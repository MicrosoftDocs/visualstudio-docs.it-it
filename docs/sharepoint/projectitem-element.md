---
title: ProjectItem (elemento) | Documenti Microsoft
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
helpviewer_keywords: ProjectItem element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 949aef0655db4536c8690080870a03f52f09fdf4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="projectitem-element"></a>Elemento ProjectItem
  Rappresenta un elemento di progetto SharePoint. Questo è l'elemento radice obbligatorio del file con estensione spdata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"  
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"  
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"  
    SupportedTrustLevels = "Trust levels that the project item supports"  
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"  
    Type="Identifier for the project item">  
  <Files>...</Files>  
  <ProjectItemFolder>...</ProjectItemFolder>  
  <SafeControls>...</SafeControls>  
  <FeatureProperties>...</FeatureProperties>  
  <ExtensionData>...</ExtensionData>  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|**DefaultFile**|Parametro facoltativo **xs: String** attributo.<br /><br /> Il percorso relativo, incluso il nome di file, del file che viene aperto nell'editor di Visual Studio quando si apre l'elemento di progetto SharePoint in **Esplora**. Il percorso è relativo rispetto alla cartella che contiene il file con estensione spdata.|  
|**FeatureReceiverClass**|Parametro facoltativo **xs: String** attributo.<br /><br /> Il nome completo di una classe del ricevitore di funzionalità per questo elemento di progetto SharePoint. Per ulteriori informazioni sui ricevitori di funzionalità, vedere [che fornisce informazioni sui pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|**FeatureReceiverAssembly**|Parametro facoltativo **xs: String** attributo.<br /><br /> Specifica il nome completo di un assembly che definisce un ricevitore di funzionalità per questo elemento di progetto SharePoint. Per ulteriori informazioni sui ricevitori di funzionalità, vedere [che fornisce informazioni sui pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Per ulteriori informazioni sui nomi di assembly completo, vedere [i nomi degli Assembly](/dotnet/framework/app-domains/assembly-names).|  
|**SupportedTrustLevels**|Parametro facoltativo **xs: String** attributo.<br /><br /> Specifica i livelli di attendibilità che supporta questo elemento di progetto SharePoint. Questo valore può essere una delle seguenti stringhe: in modalità sandbox, FullTrust, o tutti. Il valore All specifica sia Sandboxed e FullTrust.<br /><br /> In un tipo di elemento di progetto SharePoint personalizzato, il valore di questo attributo corrisponde al valore assegnato al <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> nell'implementazione di proprietà di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo. Se si specifica un valore diverso per questo attributo, Visual Studio sovrascrive il valore in modo che specifichi lo stesso livello di attendibilità specificato nella <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> proprietà.|  
|**SupportedDeploymentScopes**|Parametro facoltativo **xs: String** attributo.<br /><br /> Specifica gli ambiti di distribuzione che supporta questo elemento di progetto SharePoint. Questo valore è una stringa delimitata da virgole costituito da uno o più delle seguenti stringhe: Farm, sito, Web, WebApplication o pacchetto. Ad esempio, "Web, del sito".<br /><br /> In un tipo di elemento di progetto SharePoint personalizzato, il valore di questo attributo corrisponde al valore assegnato al <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> nell'implementazione di proprietà di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo. Se si specifica un valore diverso per questo attributo, Visual Studio sovrascrive il valore in modo che specifichi lo stesso livello di attendibilità specificato nella <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> proprietà.|  
|**Type**|Richiesto **xs: String** attributo.<br /><br /> L'identificatore per l'elemento di progetto SharePoint. In un tipo di elemento di progetto SharePoint personalizzato, l'identificatore è la stringa passata al <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Per ulteriori informazioni, vedere [procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Per un elenco di identificatori per gli elementi del progetto SharePoint predefiniti inclusi in Visual Studio, vedere [estensione di elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una raccolta di elementi di dati personalizzati associati all'elemento di progetto SharePoint.<br /><br /> È possibile includere una sola **ExtensionData** elemento.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una raccolta di valori di proprietà che sono inclusi in una funzione quando viene distribuito in SharePoint.<br /><br /> È possibile includere una sola **FeatureProperties** elemento.|  
|[File](../sharepoint/files-element.md)|Parametro facoltativo **FileCollectionType** elemento.<br /><br /> Specifica i file da distribuire con l'elemento del progetto SharePoint, ad esempio i file di elemento di funzionalità e l'output dei progetti SharePoint dipendenti.<br /><br /> È necessario includere un **file** o **ProjectItemFolder** elemento, ma non entrambi.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Parametro facoltativo **ProjectItemFolderType** elemento.<br /><br /> Rappresenta una cartella mappata.<br /><br /> È necessario includere un **file** o **ProjectItemFolder** elemento, ma non entrambi.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una raccolta di controlli ASPX e Web part che sono definiti come sicuri per tutti gli utenti di accedere in qualsiasi pagina ASPX nel sito di SharePoint.<br /><br /> È possibile includere una sola **SafeControls** elemento.|  
  
### <a name="parent-elements"></a>Elementi padre  
 Nessuno.  
  
## <a name="element-information"></a>Informazioni sull'elemento  
  
|||  
|-|-|  
|**Spazio dei nomi**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nome dello schema**|Schema di elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo schema degli elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  