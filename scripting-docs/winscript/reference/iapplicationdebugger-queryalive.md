---
title: IApplicationDebugger::QueryAlive | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IApplicationDebugger.QueryAlive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::QueryAlive
ms.assetid: 41181ebb-a3bf-4e41-82af-d6c7348dc706
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48571476407c29b9af949bd6f626d14ea822f2e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggerqueryalive"></a>IApplicationDebugger::QueryAlive
Indica se il debugger è reattivo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT QueryAlive();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo indica se il debugger è reattivo. Le implementazioni di questo metodo devono sempre restituire `S_OK`.  
  
 Se il processo del debugger viene interrotto in modo imprevisto, COM restituisce un errore dal proxy di marshalling per le chiamate a questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)