---
title: '&lt;formRegion&gt; elemento (sviluppo per Office in Visual Studio) | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: af7dd4f3472692def9f05a937297d54d13c6f0d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion&gt; elemento (sviluppo per Office in Visual Studio)
  L'elemento `formRegion` dello spazio dei nomi `vstov4` identifica un'area del modulo di Microsoft Office Outlook associata a un componente aggiuntivo VSTO.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `formRegion` dello spazio dei nomi `vstov4` identifica un'area del modulo associata a un componente aggiuntivo VSTO di Outlook. È obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree del modulo.  
  
 Possono esserci più elementi `formRegion` definiti all'interno di un elemento `formRegions` per un componente aggiuntivo VSTO singolo.  
  
 L'elemento `formRegion` presenta l'attributo seguente:  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Obbligatorio. Identifica il nome dell'area del modulo.|  
  
 L'elemento `formRegion` ha gli elementi figlio seguenti.  
  
### <a name="messageclass"></a>messageClass  
 L'elemento `messageClass` identifica il modulo di Outlook associato all'area del modulo.  
  
 L'elemento `messageClass` presenta l'attributo seguente:  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Obbligatorio. Identifica il modulo associato all'area del modulo.|  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra un elemento `formRegion` in un manifesto dell'applicazione per un componente aggiuntivo VSTO di Outlook distribuito con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Esistono tre classi di messaggi associate a questa unica area del modulo. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstov4:formRegion  
    name="OutlookAddIn1.FormRegion1">  
  <vstov4:messageClass name="IPM.Note" />  
  <vstov4:messageClass name="IPM.Contact" />  
  <vstov4:messageClass name="IPM.Appointment" />  
</vstov4:formRegion>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  