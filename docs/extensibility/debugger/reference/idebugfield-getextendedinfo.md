---
title: IDebugField::GetExtendedInfo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::GetExtendedInfo
helpviewer_keywords: IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c6b2aaa953e47366e7a99fb5a821f530d37ed66e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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