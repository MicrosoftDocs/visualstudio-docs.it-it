---
title: IDebugProgramNode2::GetEngineInfo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramNode2::GetEngineInfo
helpviewer_keywords: IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 02eaa45746b50da76702e724c700bac166f03017
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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