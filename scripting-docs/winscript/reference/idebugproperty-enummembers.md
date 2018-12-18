---
title: IDebugProperty::EnumMembers | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugProperty.EnumMembers
apilocation: scrobj.dll
helpviewer_keywords: IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9cb57f2609fcd9a80e2a9e0dfd63637e6f700047
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Enumera i membri di una proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFieldSpec`  
 [in] Specifica il `DBGPROP_INFO_FLAGS` costanti che determinano quali campi nelle strutture di proprietà di debug enumerato sono da compilare.  
  
 `nRadix`  
 [in] Base per essere utilizzato per interpretare le informazioni numeriche.  
  
 `refiid`  
 [in] Questo IID viene passato per il filtro dell'enumeratore. L'IID fa parte di `IDebugPropertyEnumType` interfacce da cui ereditare `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 [out] Restituisce il `IEnumDebugPropertyInfo` interfaccia che enumera le proprietà del membro.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un oggetto valido `HRESULT`, in genere `S_OK`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [Interfaccia IDebugPropertyEnumType_All](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [Interfaccia IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)