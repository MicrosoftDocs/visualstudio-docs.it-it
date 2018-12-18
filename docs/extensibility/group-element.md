---
title: Elemento Group | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 184bb709d25c55adcc34e73b6df1ac5f4a2448bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="group-element"></a>Elemento Group
Definisce un gruppo di comando di VSPackage.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">  
  <Parent>... </Parent>  
</Group>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. GUID dell'identificatore di comando/ID GUID.|  
|ID|Obbligatorio. ID dell'identificatore di comando/ID GUID.|  
|priority|Facoltativo. Un valore numerico che specifica la priorità.|  
|Condizione|Facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Padre|Facoltativo. L'elemento padre del pulsante.|  
|Annotazione|Commento facoltativo.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Groups](../extensibility/groups-element.md)|Contiene le voci che definiscono i gruppi di comando di un VSPackage.|  
  
## <a name="example"></a>Esempio  
  
```  
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
  <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>  
</Group>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)