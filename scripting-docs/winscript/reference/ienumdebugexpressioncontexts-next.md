---
title: IEnumDebugExpressionContexts::Next | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IEnumDebugExpressionContexts.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugExpressionContexts::Next
ms.assetid: aa223b0b-f7c1-4368-a59e-677e60133baf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56b27d74d5677d41535b0f2dfbc2adcb898af789
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugexpressioncontextsnext"></a>IEnumDebugExpressionContexts::Next
Recupera un numero di segmenti nella sequenza di enumerazione specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Next(  
   ULONG                      celt,  
   IDebugExpressionContext**  ppdec,  
   ULONG*                     pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 [in] Il numero di segmenti da recuperare.  
  
 `ppdec`  
 [out] Restituisce una matrice di `IDebugExpressionContext` interfacce che rappresenta i segmenti in corso il recupero.  
  
 `pceltFetched`  
 [out] Il numero effettivo di segmenti recuperati dall'enumeratore.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo recupera un numero di segmenti nella sequenza di enumerazione specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IEnumDebugExpressionContexts](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)