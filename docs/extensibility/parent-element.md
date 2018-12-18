---
title: Elemento padre | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 795654925a92f3e9ac0718e070e85c0f4f7f21c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="parent-element"></a>Elemento padre
L'elemento padre di una pulsante o una casella combinata può essere solo un gruppo. L'elemento padre di un menu o un gruppo può essere qualsiasi altro menu o gruppo. In un [elemento CommandPlacement](../extensibility/commandplacement-element.md), questo elemento è obbligatorio; in tutte le altre istanze è facoltativa. Se questo elemento viene omesso, l'elemento padre di `Group_Undefined:0` verrà implicita.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. Identificatore di comando di GUID/ID GUID.|  
|ID|Obbligatorio. Identificatore di comando ID GUID/ID.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi che un pacchetto VSPackage fornisce all'ambiente di sviluppo integrato (IDE). Ad esempio, le voci di menu, menu, barre degli strumenti e caselle combinate.|  
|[Elemento Buttons](../extensibility/buttons-element.md)|Gruppi [elemento Button](../extensibility/button-element.md) elementi.|  
|[Elemento Menus](../extensibility/menus-element.md)|Definisce tutti i menu che implementa un pacchetto VSPackage.|  
|[Elemento Groups](../extensibility/groups-element.md)|Contiene le voci che definiscono i gruppi di comando di un VSPackage.|  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)