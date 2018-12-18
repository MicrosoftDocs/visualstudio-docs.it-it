---
title: SafeControl (elemento) | Documenti Microsoft
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
helpviewer_keywords: SafeControl element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7458120d7a130de96a1a271c83e5376fe94481f3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="safecontrol-element"></a>Elemento SafeControl
  Rappresenta un controllo ASPX o una Web Part che è designato come protetto per qualsiasi utente di accedere in qualsiasi pagina ASPX nel sito di SharePoint.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|**Assembly**|Parametro facoltativo **xs: String** attributo.<br /><br /> Il nome dell'assembly in cui è definito il controllo ASPX o una Web Part. Per impostazione predefinita, questo attributo viene utilizzato il **$SharePoint.Project.AssemblyFullName$** parametro sostituibile per il nome dell'assembly. Per ulteriori informazioni, vedere [parametri sostituibili](../sharepoint/replaceable-parameters.md).|  
|**IsSafe**|Parametro facoltativo **xs: Boolean** attributo.<br /><br /> Specifica se il controllo ASPX o una Web Part è sicuro per gli utenti non attendibili di accedere.|  
|**IsSafeAgainstScript**|Parametro facoltativo **xs: Boolean** attributo.<br /><br /> Specifica se gli utenti non attendibili è possono visualizzare o modificare le proprietà del controllo ASPX o Web Part.|  
|**Name**|Parametro facoltativo **xs: String** attributo.<br /><br /> Il nome di questa voce di controllo sicure nella raccolta.|  
|**Spazio dei nomi**|Parametro facoltativo **xs: String** attributo.<br /><br /> Lo spazio dei nomi del controllo ASPX o Web Part.|  
|**TypeName**|Parametro facoltativo **xs: String** attributo.<br /><br /> Il nome del tipo di controllo ASPX o Web Part.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Rappresenta una raccolta di controlli ASPX e Web part che sono definiti come sicuri per tutti gli utenti di accedere in qualsiasi pagina ASPX nel sito di SharePoint.|  
  
## <a name="remarks"></a>Note  
 Per ulteriori informazioni sui controlli sicuri, vedere [che fornisce informazioni sui pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informazioni sull'elemento  
  
|||  
|-|-|  
|**Spazio dei nomi**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nome dello schema**|Schema di elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo Schema elemento di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  