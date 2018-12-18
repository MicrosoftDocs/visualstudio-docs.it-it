---
title: IDebugSyncOperation::InProgressAbort | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.InProgressAbort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1df0b0ca1d775d4d99e1da5f88a207bd4f78f99b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Annulla un'operazione in corso in un altro thread.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|L'operazione non può essere annullata.|  
|`E_ABORT`|Non è stato possibile completare l'operazione.|  
  
## <a name="remarks"></a>Note  
 Il gestore di processi di Debug chiama questo metodo dall'interno del thread del debugger per annullare un'operazione in corso in un altro thread.  
  
 Se il `InProgressAbort` (metodo) non è possibile completare l'operazione, viene restituito `E_ABORT` appena possibile. Questo metodo può restituire `E_NOTIMPL` se l'operazione non può essere annullata.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)