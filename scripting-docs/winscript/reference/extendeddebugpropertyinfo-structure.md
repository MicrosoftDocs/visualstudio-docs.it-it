---
title: Struttura ExtendedDebugPropertyInfo | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee06b0ace93f068e0530a3aa62b8c28d11069f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="extendeddebugpropertyinfo-structure"></a>Struttura ExtendedDebugPropertyInfo
Estende il `DebugPropertyInfo` struttura con membri aggiuntivi per caratterizzare la proprietà estesa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>Membri  
 `dwValidFields`  
 Un tipo di dati enumerati utilizzato per specificare quali campi vengono inizializzati.  
  
 `bstrName`  
 Il nome della proprietà all'interno di un contesto.  
  
 `bstrType`  
 Il tipo della proprietà come stringa formattata.  
  
 `bstrValue`  
 Il valore della proprietà come una stringa formattata.  
  
 `bstrFullName`  
 Nome completo della proprietà.  
  
 `dwAttrib`  
 Enumerazione che specifica i flag per gli attributi della proprietà di debug.  
  
 `pDebugProp`  
 `IDebugProperty`oggetto corrispondente a tale `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 Id dispatch.  
  
 `nType`  
 Il tipo della proprietà estesa.  
  
 `varValue`  
 Il valore della proprietà estesa può essere inclusa in VARIANT.  
  
 `plbValue`  
 I byte di dati effettivi del valore della proprietà.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty`oggetto corrispondente a tale `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>Vedere anche  
 [Struttura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)   
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [Interfaccia IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)