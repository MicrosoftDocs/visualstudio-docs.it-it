---
title: IDebugProgramNode2::GetEngineInfo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 01a18b52a964d993be6328bf3057263ededd2320
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
Ottiene il nome e l'identificatore del motore di debug (DE) esegue un programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetEngineInfo (   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineInfo(  
   out string pbstrEngine,   
   out Guid pguidEngine  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrEngine`  
 [out] Restituisce il nome della DE esecuzione del programma (C++ specifiche: può trattarsi di un puntatore null, che indica che il chiamante non è interessato nel nome il motore).  
  
 `pguidEngine`  
 [out] Restituisce l'identificatore univoco globale della DE esecuzione del programma (C++ specifiche: può trattarsi di un puntatore null, che indica che il chiamante non è interessato il GUID del modulo di gestione).  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)