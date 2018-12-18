---
title: Elemento CommandPlacement | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a6a5c8d9220b0cd2c0dddfee283d222f4efb9ab8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="commandplacement-element"></a>Elemento CommandPlacement
L'elemento CommandPlacement consente pulsanti, gruppi e menu da includere in più di un gruppo o un menu. Tramite l'elemento CommandPlacement, non è necessario ridefinire completamente questi elementi per modificare l'aspetto di un'interfaccia utente.  
  
 Per ulteriori informazioni, vedere [creazione riutilizzabile gruppi di pulsanti](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. Il guid del set di comandi, come definito nel [elemento simboli](../extensibility/symbols-element.md).|  
|ID|Obbligatorio. L'id del menu, gruppo o comando per essere inserito, come definito nel `Symbols Element`.|  
|priority|Obbligatorio. Determina la posizione dell'elemento visiva nel relativo elemento padre.|  
|Condizione|Facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Padre|Obbligatorio. Il menu o un gruppo che contiene l'elemento da inserire.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Specifica i gruppi di elementi CommandPlacements e CommandPlacement.|  
  
## <a name="example"></a>Esempio  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento CommandPlacements](../extensibility/commandplacements-element.md)   
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)