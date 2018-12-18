---
title: IDebugAsyncOperation::GetResult | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugAsyncOperation.GetResult
apilocation: pdm.dll
helpviewer_keywords: IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60181904408010f35fa4d99d182216e665583aab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Fornisce il valore restituito e il parametro dell'oggetto restituito dall'operazione di debug sincrono.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `phrResult`  
 [out] Se l'operazione è stata completata, `phrResult` è il valore restituito di `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 [out] Se l'operazione è stata completata, `ppunkResult` è il parametro dell'oggetto restituito dall'operazione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_PENDING`|L'operazione non completata.|  
  
## <a name="remarks"></a>Note  
 Se l'operazione è stata completata, questo metodo restituisce il `HRESULT` e oggetto parametro da `IDebugSyncOperation::Execute`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)