---
title: IDebugApplication::HandleBreakPoint | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.HandleBreakPoint
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16b05533c566cb90529766d81fb7197dbc284664
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Causa il blocco del thread corrente e invia una notifica del punto di interruzione nel debugger IDE.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `br`  
 [in] Il motivo per l'interruzione.  
  
 `pbra`  
 [out] Azione da intraprendere quando il debugger consente di riprendere l'applicazione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Un motore di linguaggio chiama questo metodo nel contesto di un thread che raggiunge un punto di interruzione. Questo metodo blocca il thread corrente e invia una notifica di punto di interruzione nel debugger IDE. Quando il debugger consente di riprendere l'applicazione, il `pbra` parametro specifica l'azione da intraprendere.  
  
> [!NOTE]
>  Il motore di lingua può essere chiamato dal thread di esecuzione delle attività, ad esempio enumerare stack frame o valutare le espressioni durante il punto di interruzione.  
  
 Questo metodo determina `IApplicationDebugger::onHandleBreakPoint` da chiamare.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [Enumerazione BREAKREASON](../../winscript/reference/breakreason-enumeration.md)   
 [Enumerazione BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)