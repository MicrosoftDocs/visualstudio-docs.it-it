---
title: DBGPROP_ATTRIB_FLAGS | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_ATTRIB_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS
ms.assetid: 90314496-527b-4357-9df8-125a360bf216
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43db6cd118e2097d857d5c41334341c595088302
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="dbgpropattribflags"></a>DBGPROP_ATTRIB_FLAGS
Descrive i vari attributi per `IDebugProperty`. Membro della struttura `DebugPropertyInfo`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
enum {  
DBGPROP_ATTRIB_NO_ATTRIB  =0x00000000,  
   DBGPROP_ATTRIB_VALUE_IS_INVALID  =0x00000008,  
   DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  =0x00000010,  
   DBGPROP_ATTRIB_VALUE_READONLY  =0x00000800,  
   DBGPROP_ATTRIB_ACCESS_PUBLIC  =0x00001000,  
   DBGPROP_ATTRIB_ACCESS_PRIVATE  =0x00002000,  
   DBGPROP_ATTRIB_ACCESS_PROTECTED  =0x00004000,  
   DBGPROP_ATTRIB_ACCESS_FINAL  =0x00008000,  
   DBGPROP_ATTRIB_STORAGE_GLOBAL  =0x00010000,  
   DBGPROP_ATTRIB_STORAGE_STATIC  =0x00020000,  
   DBGPROP_ATTRIB_STORAGE_FIELD  =0x00040000,  
   DBGPROP_ATTRIB_STORAGE_VIRTUAL  =0x00080000,  
   DBGPROP_ATTRIB_TYPE_IS_CONSTANT  =0x00100000,  
   DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  =0x00200000,  
   DBGPROP_ATTRIB_TYPE_IS_VOLATILE  =0x00400000,  
   DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  =0x00800000  
   DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  =0x08000000,  
};  
  
```  
  
## <a name="members"></a>Membri  
 DBGPROP_ATTRIB_NO_ATTRIB  
 Indica nessun attributo.  
  
 DBGPROP_ATTRIB_VALUE_IS_INVALID  
 Indica che il valore in `DebugPropertyInfo::bstrValue` non è valido.  
  
 DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  
 Indica che il riferimento o la proprietà contiene figli.  
  
 DBGPROP_ATTRIB_VALUE_READONLY  
 Indica che il valore è di sola lettura.  
  
 DBGPROP_ATTRIB_ACCESS_PUBLIC  
 Indica un oggetto con accesso pubblico.  
  
 DBGPROP_ATTRIB_ACCESS_PRIVATE  
 Indica un oggetto con accesso privato.  
  
 DBGPROP_ATTRIB_ACCESS_PROTECTED  
 Indica un oggetto con accesso protetto.  
  
 DBGPROP_ATTRIB_ACCESS_FINAL  
 Indica un oggetto con accesso finale.  
  
 DBGPROP_ATTRIB_STORAGE_GLOBAL  
 Indica l'archiviazione globale.  
  
 DBGPROP_ATTRIB_STORAGE_STATIC  
 Indica l'archiviazione statica.  
  
 DBGPROP_ATTRIB_STORAGE_FIELD  
 Indica un oggetto che è una proprietà.  
  
 DBGPROP_ATTRIB_STORAGE_VIRTUAL  
 Indica l'archiviazione virtuale.  
  
 DBGPROP_ATTRIB_TYPE_IS_CONSTANT  
 Indica che il tipo di oggetto è costante.  
  
 DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  
 Indica che questo slot è con sincronizzazione dei thread.  
  
 DBGPROP_ATTRIB_TYPE_IS_VOLATILE  
 Indica che questo slot è volatile per quanto riguarda l'archiviazione permanente.  
  
 DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  
 Indica che questo slot contiene attributi ben oltre questi bit predefiniti.  
  
 DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  
 Indica che il valore è un valore restituito da una funzione.  
  
## <a name="remarks"></a>Note  
 Questi flag vengono usanti anche per filtrare i figli di un oggetto. I valori possono essere combinati con un OR bit per bit.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [Struttura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)