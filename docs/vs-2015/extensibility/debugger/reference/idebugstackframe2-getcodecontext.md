---
title: IDebugStackFrame2::GetCodeContext | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame2::GetCodeContext
helpviewer_keywords:
- IDebugStackFrame2::GetCodeContext
ms.assetid: 93d66159-a41d-49ef-982f-91bb4d073b74
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 61adef2f68041bffda4e0b53b92282b9a2ba55de
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729449"
---
# <a name="idebugstackframe2getcodecontext"></a>IDebugStackFrame2::GetCodeContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il contesto del codice per questo stack frame.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetCodeContext (   
   IDebugCodeContext2** ppCodeCxt  
);  
```  
  
```csharp  
int GetCodeContext (   
   out IDebugCodeContext2 ppCodeCxt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppCodeCxt`  
 [out] Restituisce un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) oggetto che rappresenta il puntatore all'istruzione corrente in questo stack frame.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)

