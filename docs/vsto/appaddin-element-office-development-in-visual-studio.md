---
title: '&lt;appAddin&gt; elemento (sviluppo per Office in Visual Studio) | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9def97d044af74f02a2064703691333ec9f176aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin&gt; elemento (sviluppo per Office in Visual Studio)
  L'elemento `appAddin` dello spazio dei nomi `vstov4` archivia informazioni specifiche della personalizzazione per i componenti aggiuntivi VSTO.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<appAddin  
  application  
  loadBehavior  
  keyName>  
  <friendlyName>  
  <description>  
  <formRegions></formRegions>  
</appAddin>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `appAddin` è obbligatorio e si trova nello spazio dei nomi `vstov4` . Viene definito un solo elemento `appAddin` in un manifesto dell'applicazione.  
  
 L'elemento `appAddin` presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`application`|Obbligatorio. Identifica l'applicazione di Microsoft Office. Il valore può essere uno dei seguenti: Excel, InfoPath, Outlook, PowerPoint, Project, Visio o Word.|  
|`loadBehavior`|Facoltativo. Per impostazione predefinita, `loadBehavior` è abilitato impostando questo valore. Per il debug, il componente aggiuntivo VSTO può essere disabilitato impostando il valore su due. Per altre informazioni, vedere la tabella intitolata Valori di LoadBehavior in [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).|  
|`keyName`|Obbligatorio. Questo valore corrisponde al nome della chiave del Registro di sistema che verrà usata dall'applicazione per il caricamento del componente aggiuntivo VSTO. Per altre informazioni, vedere [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).|  
  
 L'elemento `appAddin` ha gli elementi figlio seguenti.  
  
### <a name="friendlyname"></a>friendlyName  
 Facoltativo. Il `friendlyName` elemento è descritto nel [ &#60;friendlyName&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).  
  
### <a name="description"></a>Descrizione  
 Facoltativo. Il `description` elemento è descritto nel [ &#60;descrizione&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).  
  
### <a name="formregions"></a>formRegions  
 Obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree di modulo. Il `formRegions` elemento è descritto nel [ &#60;formRegions&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra gli elementi `appAddin` presenti in una soluzione Outlook distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```  
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
```  
  
## <a name="see-also"></a>Vedere anche  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  