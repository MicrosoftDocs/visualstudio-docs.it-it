---
title: IDebugField::GetExtendedInfo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 63bf182e4e8b17133fbefd4f4a19c4b8b4a458e9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Questo metodo ottiene estesi informazioni su un campo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```csharp  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guidExtendedInfo`  
 [in] Seleziona le informazioni da restituire. I valori validi sono:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`guidConstantValue`|Il valore come una sequenza di byte.|  
|`guidConstantType`|Il tipo come una firma di tipo.|  
  
 `prgBuffer`  
 [out] Restituisce le informazioni estese.  
  
 `pdwLen`  
 [in, out] Restituisce le dimensioni delle informazioni estese, in byte.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Attualmente, questo metodo restituisce solo il tipo o valore di una costante. Il chiamante deve liberare il buffer restituito `prgBuffer` chiamando il metodo COM `CoTaskMemFree` funzione (C++) o <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (c#).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)