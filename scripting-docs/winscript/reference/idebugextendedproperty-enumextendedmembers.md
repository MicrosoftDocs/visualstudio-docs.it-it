---
title: IDebugExtendedProperty::EnumExtendedMembers | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExtendedProperty.EnumExtendedMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExtendedProperty::EnumExtendedMembers
ms.assetid: 27cdb091-da4e-44d2-a631-31ae00468b98
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81b1cbb9b36d7ae237551aad2677f9480c615b88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugextendedpropertyenumextendedmembers"></a>IDebugExtendedProperty::EnumExtendedMembers
Enumera i membri di una proprietà estesa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT EnumExtendedMembers(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   IEnumDebugExtendedPropertyInfo**  ppeepi  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFieldSpec`  
 [in] Specifica le costanti EX_DBGPROP_INFO_FLAGS che determinano che i campi in enumerati estesi strutture delle proprietà debug devono essere compilati.  
  
 `nRadix`  
 [in] Base per essere utilizzato per interpretare le informazioni numeriche.  
  
 `ppeepi`  
 [out] Restituisce il `IEnumDebugExtendedPropertyInfo` interfaccia che enumera le proprietà del membro.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un oggetto valido `HRESULT`, in genere `S_OK`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [Struttura ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)