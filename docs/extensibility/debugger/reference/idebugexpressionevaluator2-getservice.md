---
title: IDebugExpressionEvaluator2::GetService | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1ff102b35e7492a47833fbbac710509711eac471
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Recupera un oggetto servizio dato il relativo identificatore univoco.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetService (  
   GUID        uid,  
   IUnknown ** ppService  
);  
```  
  
```csharp  
int GetService (  
   Guid       uid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `uid`  
 [in] Identificatore univoco del servizio da recuperare.  
  
 `ppService`  
 [out] Restituisce un oggetto che rappresenta il servizio.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo può essere utilizzato da un analizzatore di espressioni di terze parti per ottenere servizi dall'analizzatore di espressioni di un altro. Ad esempio, questo metodo può essere utilizzato per ottenere l'interfaccia per il servizio Visualizzatore dall'analizzatore di espressioni predefinito. Gli analizzatori di espressioni di terze parti sono improbabile che devono implementare questa interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)