---
title: IEnumDebugApplicationNodes::Next | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IEnumDebugApplicationNodes.Next
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumDebugApplicationNodes::Next
ms.assetid: 925511c8-4f11-423d-ba2d-01589457050c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61bc2b677f12106c9bd8e6c8bec57ae1f7a09605
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugapplicationnodesnext"></a>IEnumDebugApplicationNodes::Next
Recupera un numero di segmenti nella sequenza di enumerazione specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Next(  
   ULONG                    celt,  
   IDebugApplicationNode**  pprddp,  
   ULONG*                   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 [in] Il numero di segmenti da recuperare.  
  
 `pprddp`  
 [out] Restituisce una matrice di `IDebugApplicationNode` interfacce che rappresenta i segmenti in corso il recupero.  
  
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
 [Interfaccia IEnumDebugApplicationNodes](../../winscript/reference/ienumdebugapplicationnodes-interface.md)