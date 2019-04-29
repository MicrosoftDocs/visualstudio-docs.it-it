---
title: DBGPROP_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c63cf941bca1965fc4a2e3997f0c0b50ebc44035
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955302"
---
# <a name="dbgpropinfoflags"></a>DBGPROP_INFO_FLAGS
Consente di specificare `DebugPropertyInfo` campi  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
enum {  
   DBGPROP_INFO_NAME  =0x001,  
   DBGPROP_INFO_TYPE  =0x002,  
   DBGPROP_INFO_VALUE  =0x004,  
   DBGPROP_INFO_FULLNAME  =0x020,  
   DBGPROP_INFO_ATTRIBUTES  =0x008,  
   DBGPROP_INFO_DEBUGPROP  =0x010,  
   DBGPROP_INFO_AUTOEXPAND  =0x8000000  
};  
```  
  
## <a name="members"></a>Membri  
 DBGPROP_INFO_NAME  
 Inizializza il `bstrName` campo.  
  
 DBGPROP_INFO_TYPE  
 Inizializza il `bstrType` campo.  
  
 DBGPROP_INFO_VALUE  
 Inizializza il `bstrValue` campo.  
  
 DBGPROP_INFO_FULLNAME  
 Inizializza il `bstrFullName` campo.  
  
 DBGPROP_INFO_ATTRIBUTES  
 Inizializza il `dwAttrib` campo.  
  
 DBGPROP_INFO_DEBUGPROP  
 Inizializza la `pDebugProp` campo che contiene un `IDebugProperty` interfaccia.  
  
 DBGPROP_INFO_AUTOEXPAND  
 Specifica che il campo del valore deve contenere il valore espanso automaticamente, se disponibile, per questo tipo di oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Struttura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)   
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)