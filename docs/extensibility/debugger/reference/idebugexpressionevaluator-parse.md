---
title: IDebugExpressionEvaluator::Parse | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpressionEvaluator::Parse
helpviewer_keywords: IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e64d7419973f0505a2413d7ea56be12a31d01a1c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Questo metodo converte una stringa di espressione in un'espressione analizzata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```csharp  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `upstrExpression`  
 [in] Stringa dell'espressione deve essere analizzato.  
  
 `dwFlags`  
 [in] Una raccolta di [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) costanti che determinano la modalità con cui l'espressione è da analizzare.  
  
 `nRadix`  
 [in] Base per essere utilizzato per interpretare le informazioni numeriche.  
  
 `pbstrError`  
 [out] Restituisce l'errore come testo leggibile.  
  
 `pichError`  
 [out] Restituisce la posizione del carattere dell'inizio dell'errore nella stringa di espressione.  
  
 `ppParsedExpression`  
 [out] Restituisce l'espressione analizzata in un [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo produce un'espressione analizzata, non è un valore effettivo. Un'espressione analizzata è pronta per essere valutata, convertita in un valore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)