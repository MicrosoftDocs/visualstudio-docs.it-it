---
title: '&lt;documento&gt; elemento (sviluppo per Office in Visual Studio) | Documenti Microsoft'
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
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 38b03c2a4980891d9a6841b24365db32ee555de4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;documento&gt; elemento (sviluppo per Office in Visual Studio)
  Il `document` elemento il `vstov4` dello spazio dei nomi archivia informazioni specifiche della personalizzazione per le personalizzazioni a livello di documento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<document solutionId />  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Obbligatorio solo per le personalizzazioni a livello di documento. Il `document` elemento è incluso il `vstov4` dello spazio dei nomi. Il `document` dispone degli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`solutionId`|Obbligatorio. Il GUID utilizzato da Visual Studio Tools per Office runtime per identificare in modo univoco una soluzione a livello di documento. Questo valore viene memorizzato come proprietà AssemblyLocation personalizzate del documento. Per altre informazioni, vedere [Custom Document Properties Overview](../vsto/custom-document-properties-overview.md).|  
  
 `document`non include elementi figlio.  
  
## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento  
  
### <a name="description"></a>Descrizione  
 Nell'esempio di codice seguente viene illustrato il `document` elemento in una soluzione Office a livello di documento distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```  
<vstov4:document   
  solutionId="73e" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  