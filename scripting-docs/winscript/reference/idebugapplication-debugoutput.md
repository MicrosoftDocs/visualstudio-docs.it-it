---
title: IDebugApplication::DebugOutput | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.DebugOutput
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::DebugOutput
ms.assetid: 6c02939c-3c2d-474a-ab15-49a37e22b4a7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfc956c7d2d65d20788a79c9f685e386aba97a80
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationdebugoutput"></a>IDebugApplication::DebugOutput
Fa sì che la stringa specificata deve essere visualizzato l'ambiente di sviluppo integrato (IDE) di debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT DebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstr`  
 [in] Stringa da visualizzare nel debugger.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo consente a un motore di linguaggio implementare il supporto output di debug specifiche della lingua. La stringa viene in genere visualizzata nella finestra di output del debugger.  
  
 Questo metodo determina `IApplicationDebugger::onDebugOutput` da chiamare.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)