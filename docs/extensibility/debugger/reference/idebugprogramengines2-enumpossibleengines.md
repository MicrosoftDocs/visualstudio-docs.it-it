---
title: IDebugProgramEngines2::EnumPossibleEngines | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords: IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 81765959c0735080141ba8974387d592a461df25
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Restituisce il GUID per tutti i possibili motori di debug (DE) che è possono eseguire il debug di questo programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```csharp  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celtBuffer`  
 [in] Il numero di GUID DE da restituire. Specifica anche la dimensione massima del `rgguidEngines` matrice.  
  
 `rgguidEngines`  
 [in, out] Una matrice di GUID DE da compilare.  
  
 `pceltEngines`  
 [out] Restituisce il numero effettivo di GUID DE che vengono restituiti.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` o [c#] 0x8007007A se il buffer non è sufficientemente grande.  
  
## <a name="remarks"></a>Note  
 Per determinare il numero di motori, chiamare questo metodo una volta con il `celtBuffer` parametro impostato su 0 e `rgguidEngines` parametro impostato su un valore null. Restituisce `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A per c#) e `pceltEngines` parametro restituisce le dimensioni del buffer necessarie.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)