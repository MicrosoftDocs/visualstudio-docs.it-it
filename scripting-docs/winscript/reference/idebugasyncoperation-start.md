---
title: IDebugAsyncOperation::Start | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugAsyncOperation.Start
apilocation: pdm.dll
helpviewer_keywords: IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd39053e86dce95fa52ba8576814962d13d8b050
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Fa sì che l'operazione asincrona iniziare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `padocb`  
 L'interfaccia di callback che riceve gli eventi di stato da questa operazione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_UNEXPECTED`|Un'operazione è già in sospeso.|  
  
## <a name="remarks"></a>Note  
 Questo metodo determina `IDebugSyncOperation::Execute` da chiamare in modo asincrono nel thread ottenuto da `IDebugSyncOperation::GetTargetThread`. Questo metodo deve essere chiamato solo da entro il thread del debugger. in caso contrario, non verrà restituito fino al completamento dell'operazione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [Interfaccia IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)