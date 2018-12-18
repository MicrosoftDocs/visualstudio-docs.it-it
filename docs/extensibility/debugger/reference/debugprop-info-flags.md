---
title: DEBUGPROP_INFO_FLAGS | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d9ecaab348ca69a792c39a8cb74e998d8f3a6aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
Specifica le informazioni da recuperare su un oggetto di proprietà di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
typedef DWORD DEBUGPROP_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membri  
 DEBUGPROP_INFO_FULLNAME  
 Inizializzazione/Usa il `bstrFullName` campo.  
  
 DEBUGPROP_INFO_NAME  
 Inizializzazione/Usa il `bstrName` campo.  
  
 DEBUGPROP_INFO_TYPE  
 Inizializzazione/Usa il `bstrType` campo.  
  
 DEBUGPROP_INFO_VALUE  
 Inizializzazione/Usa il `bstrValue` campo.  
  
 DEBUGPROP_INFO_ATTRIB  
 Inizializzazione/Usa il `dwAttrib` campo.  
  
 DEBUGPROP_INFO_PROP,  
 Inizializzazione/Usa il `pProperty` campo contenente un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaccia.  
  
 DEBUGPROP_INFO_VALUE_AUTOEXPAND  
 Specifica che il campo del valore deve contenere il valore di espansione automatica, se disponibile, per questo tipo di oggetto.  
  
 DEBUGPROP_INFO_VALUE_NOFUNCEVAL  
 Deprecato.  
  
 DEBUGPROP_INFO_VALUE_RAW  
 Non restituiscono i valori beautified o i membri (vale a dire non formattare i valori).  
  
 DEBUGPROP_INFO_VALUE_NO_TOSTRING  
 Non restituiscono valori sintetizzati speciali (ad esempio, non chiamare `ToString()` su un oggetto per produrre un valore).  
  
 DEBUGPROP_INFO_NONE  
 Specifica che nessun flag impostato.  
  
 DEBUGPROP_INFO_STANDARD  
 Inizializzazione/Usa il `dwAttrib`, `bstrName`, `bstrType`, e `bstrValue` campi.  
  
 DEBUGPROP_INFO_All  
 Indica una maschera di tutti i flag.  
  
## <a name="remarks"></a>Note  
 Questi valori vengono passati per la [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md), e [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) metodi per indicare i campi da inizializzare il [ DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struttura.  
  
 Questi valori vengono utilizzati anche per il `dwFields` appartenente il `DEBUG_PROPERTY_INFO` struttura per indicare quali campi della struttura sono validi e utilizzate quando viene restituita la struttura.  
  
 Questi valori possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)