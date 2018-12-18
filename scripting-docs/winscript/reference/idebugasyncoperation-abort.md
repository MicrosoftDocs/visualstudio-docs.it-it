---
title: IDebugAsyncOperation::Abort | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugAsyncOperation.Abort
apilocation: pdm.dll
helpviewer_keywords: IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 274f09ae2a8851b897a825c32f18091c2f4250d0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
Annulla un'operazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|S_OK|Il metodo è riuscito.|  
|E_NOTIMPL|Le operazioni non possono essere annullate.|  
  
## <a name="remarks"></a>Note  
 In genere, questo metodo viene chiamato dall'interno del thread del debugger per annullare un'operazione che non risponda. Questo metodo determina la `InProgressAbort` metodo il `IDebugSyncOperation` oggetto da chiamare.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)