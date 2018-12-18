---
title: Interfaccia IDebugPropertyEnumType_All | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All interface
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75de35bd42ea91e7d27523ba42c392650686041a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertyenumtypeall-interface"></a>Interfaccia IDebugPropertyEnumType_All
Il `IDebugPropertyEnumType` interfacce sono definite in modo che ognuno di loro IID può essere passato come un filtro per `IDebugProperty::EnumMembers` durante la richiesta l'enumeratore appropriato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Restituisce una stringa di testo che descrive il nome|  
  
 Le interfacce seguenti ereditano `IDebugPropertyEnumType_All`, e non dispone di alcun metodi aggiuntivi.  
  
```  
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)