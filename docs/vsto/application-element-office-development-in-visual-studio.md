---
title: '&lt;applicazione&gt; elemento (sviluppo per Office in Visual Studio) | Documenti Microsoft'
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
helpviewer_keywords: application manifests [Office development in Visual Studio], <application> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9f20c4c8e6d44c62282f68173ce980f650da2692
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="ltapplicationgt-element-office-development-in-visual-studio"></a>&lt;applicazione&gt; elemento (sviluppo per Office in Visual Studio)
  L'elemento `application` dello spazio dei nomi `vstav3` esegue il wrapping della descrizione delle soluzioni Office. Gli elementi figlio sono diversi per le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO.  
  
## <a name="syntax-for-document-level-customizations"></a>Sintassi per le personalizzazioni a livello di documento  
  
```  
<application>  
  <customization  
    id  
    <document  
      solutionId  
    />  
  </customization>  
</application>  
```  
  
## <a name="syntax-for-application-level-add-ins"></a>Sintassi per i componenti aggiuntivi a livello di applicazione  
  
```  
<application>  
  <customization  
    id  
    <appAddin  
      application  
      loadBehavior  
      keyName>  
    <friendlyName></friendlyName>  
    <description></description>  
    <formRegions></formRegions>  
  </customization>  
</application>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `application` dello spazio dei nomi `vstav3` è il nodo che esegue il wrapping di tutte le informazioni specifiche delle personalizzazioni contenute nello spazio dei nomi `vstov4` .  
  
 L'elemento `application` non ha attributi.  
  
 L'elemento `application` presenta l'elemento seguente.  
  
### <a name="customization"></a>personalizzazione  
 Il ruolo del `customization` elemento il `vstov3` dello spazio dei nomi è definito in [&#60; personalizzazione &#62; Elemento &#40; sviluppo per Office in Visual Studio &#41; ](../vsto/customization-element-office-development-in-visual-studio.md).  
  
## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra un elemento `application` in una soluzione Office a livello di documento distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```  
<vstav3:application>  
  <vstov4:customizations   
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
    <vstov4:customization>  
      <vstov4:document   
        solutionId="73e" />  
    </vstov4:customization>  
  </vstov4:customizations>  
</vstav3:application>  
```  
  
## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra un elemento `application` in una soluzione Office a livello di applicazione distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```  
<vstav3:application>  
  <vstov4:customizations   
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
    <vstov4:customization>  
      <vstov4:appAddIn   
        application="Outlook"   
        loadBehavior="3"   
        keyName="ContosoOutlookAddIn">  
        <vstov4:friendlyName>  
          ContosoOutlookAddIn  
        </vstov4:friendlyName>  
        <vstov4:description>  
          ContosoOutlookAddIn - Outlook VSTO Add-in   
          created with Visual Studio Tools for Office  
        </vstov4:description>  
        <vstov4:formRegions>  
          <vstov4:formRegion  
              name="OutlookAddIn1.FormRegion1">  
            <vstov4:messageClass name="IPM.Note" />  
            <vstov4:messageClass name="IPM.Contact" />  
            <vstov4:messageClass name="IPM.Appointment" />  
          </vstov4:formRegion>  
        </vstov4:formRegions>  
      </vstov4:appAddIn>  
    </vstov4:customization>  
  </vstov4:customizations>  
</vstav3:application>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  