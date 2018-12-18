---
title: IDebugStackFrame::GetLanguageString | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugStackFrame.GetLanguageString
apilocation: jscript.dll
helpviewer_keywords: IDebugStackFrame::GetLanguageString
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 724ca98278eb8885d29aad1799f822ac57251597
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
Restituisce una descrizione testuale lungo o breve della lingua.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `fLong`  
 [in] Flag, in cui `TRUE` restituisce una descrizione lunga e `FALSE` restituisce una breve descrizione.  
  
 `pbstrLanguage`  
 [out] Descrizione della lingua.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 In genere, se `fLong` è `FALSE`, questo metodo fornisce solo il nome della lingua associata a uno stack frame. Quando `fLong` è `TRUE`, questo metodo può fornire una descrizione completa del prodotto.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)