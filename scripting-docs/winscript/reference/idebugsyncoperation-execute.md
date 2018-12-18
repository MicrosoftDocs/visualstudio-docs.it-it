---
title: IDebugSyncOperation::Execute | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugSyncOperation.Execute
apilocation: jscript.dll
helpviewer_keywords: IDebugSyncOperation::Execute
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 69e07c646bfa176f5e2dc07539f301a8ef5c5273
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
In modo sincrono, esegue l'operazione e restituisce.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppunkResult`  
 [out] Il parametro dell'oggetto restituito dall'operazione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_ABORT`|L'operazione è stata interrotta chiamando il `IDebugSyncOperation::InProgressAbort` metodo.|  
  
## <a name="remarks"></a>Note  
 Il gestore di eseguire il Debug di processi nelle chiamate di thread di destinazione di `Execute` metodo in modo sincrono.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)