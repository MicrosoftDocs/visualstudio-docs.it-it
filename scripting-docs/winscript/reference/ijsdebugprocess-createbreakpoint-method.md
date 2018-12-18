---
title: 'Metodo ijsdebugprocess:: CreateBreakpoint | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugProcess.CreateBreakPoint
apilocation: jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10d734f32d092d341dbb1b02a5cc7a0c127223a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>Metodo IJsDebugProcess::CreateBreakPoint
Imposta il punto di interruzione nella posizione del documento specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `documentId`  
 [in] Puntatore a IDebugDocumentText.  
  
 `characterOffset`  
 [in] Carattere offset dall'inizio del file.  
  
 `characterCount`  
 [in] Lunghezza del testo del documento all'interno del quale deve essere inserito il punto di interruzione.  
  
 `isEnabled`  
 [in] Specifica se il punto di interruzione è abilitato.  
  
 `ppDebugBreakPoint`  
 [out] Oggetto che rappresenta il punto di interruzione è stato creato.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)