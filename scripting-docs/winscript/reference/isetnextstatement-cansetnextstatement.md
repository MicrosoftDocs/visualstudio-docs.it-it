---
title: ISetNextStatement::CanSetNextStatement | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ISetNextStatement.CanSetNextStatement
apilocation: scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bd32ddf73076f9e29ca3377186ff64be256b8fc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="isetnextstatementcansetnextstatement"></a>ISetNextStatement::CanSetNextStatement
Questo metodo determina se il punto di esecuzione, che determina la successiva istruzione del codice da eseguire, è possibile impostare nel percorso specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>Parametri  
 `pStackFrame`  
 [in] Puntatore a un oggetto stack frame.  
  
 `pCodeContext`  
 [in] Puntatore a un oggetto di contesto del codice.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|L'istruzione successiva può essere aggiornato nel contesto del codice specificato.|  
|`S_FALSE`|Impossibile aggiornare l'istruzione successiva nel contesto del codice specificato.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)