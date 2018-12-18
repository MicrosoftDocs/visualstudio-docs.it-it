---
title: 'Metodo ijsdebug:: OpenVirtualProcess | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJSDebug.OpenVirtualProcess
apilocation: jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5acb137337e46a6e84f7d68c9330a3ca847f2e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugopenvirtualprocess-method"></a>Metodo IJsDebug::OpenVirtualProcess
Metodo factory utilizzato per creare un nuovo oggetto processo virtuale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
 HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `processId`  
 [in] Id del processo per connettere il debugger.  
  
 `runtimeJsBaseAddress`  
 [in] L'indirizzo di base in cui il runtime di JavaScript caricato nel processo di destinazione.  
  
 `pDataTarget`  
 [in] Interfaccia fornita per eseguire query sullo stato del processo del debugger.  
  
 `ppProcess`  
 [out] Nuovo oggetto processo di debug  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce E_JsDEBUG_MISMATCHED_RUNTIME se Jscript9diag e Jscript9 non corrispondono.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebug](../../winscript/reference/ijsdebug-interface.md)