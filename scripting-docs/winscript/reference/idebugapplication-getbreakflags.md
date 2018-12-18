---
title: IDebugApplication::GetBreakFlags | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.GetBreakFlags
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::GetBreakFlags
ms.assetid: 0532ba94-f791-46ad-88ae-5f6ba220b667
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3bdccefb3a679694360ed9a7c6fea35eae6bdb1b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationgetbreakflags"></a>IDebugApplication::GetBreakFlags
Restituisce i flag di interruzione corrente per l'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetBreakFlags(  
   APPBREAKFLAGS*                   pabf,  
   IRemoteDebugApplicationThread**  pprdatSteppingThread  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pabf`  
 [out] I flag di interruzione corrente per l'applicazione.  
  
 `pprdatSteppingThread`  
 [out] Il thread attualmente in esecuzione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce i flag di interruzione corrente per l'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Enumerazione APPBREAKFLAGS](../../winscript/reference/appbreakflags-enumeration.md)