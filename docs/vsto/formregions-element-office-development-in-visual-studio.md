---
title: '&lt;formRegions&gt; elemento (sviluppo per Office in Visual Studio) | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c51b626c104d5342c00dbd45a2c565315c9c2225
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formRegions&gt; elemento (sviluppo per Office in Visual Studio)
  L'elemento `formRegions` dello spazio dei nomi `vstov4` contiene le aree del modulo di Microsoft Office Outlook associate a un componente aggiuntivo VSTO.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `formRegions` dello spazio dei nomi `vstov4` contiene tutti gli elementi `formRegion` per un componente aggiuntivo VSTO di Outlook. È obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree del modulo.  
  
 Può essere definito un solo elemento `formRegions` in un manifesto dell'applicazione.  
  
 L'elemento `formRegions` non ha attributi.  
  
 L'elemento `formRegions` presenta l'elemento seguente.  
  
### <a name="formregion"></a>formRegion  
 Obbligatorio per i componenti aggiuntivi VSTO di Outlook che includono aree del modulo. Il `formRegion` è definito l'elemento [ &#60;formRegion&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra un elemento `formRegions` in un manifesto dell'applicazione per una soluzione Office a livello di applicazione distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```  
<vstov4:formRegions>  
  <vstov4:formRegion  
      name="OutlookAddIn1.FormRegion1">  
    <vstov4:messageClass name="IPM.Note" />  
    <vstov4:messageClass name="IPM.Contact" />  
    <vstov4:messageClass name="IPM.Appointment" />  
  </vstov4:formRegion>  
</vstov4:formRegions>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  