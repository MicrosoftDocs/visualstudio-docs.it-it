---
title: IEnumRemoteDebugApplicationThreads::Next | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumRemoteDebugApplicationThreads.Next
apilocation: pdm.dll
helpviewer_keywords: IEnumRemoteDebugApplicationThreads::Next
ms.assetid: d8d10d7e-3468-49be-acf9-d842db9940e7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8ce0dc7c77cd3b58f388ab63a9d5a3573c93419
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ienumremotedebugapplicationthreadsnext"></a>IEnumRemoteDebugApplicationThreads::Next
Il `Next` che consente di recuperare un numero di segmenti nella sequenza di enumerazione specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Next(  
   ULONG                            celt,  
   IRemoteDebugApplicationThread**  pprdat,  
   ULONG*                           pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 [in] Il numero di segmenti da recuperare.  
  
 `pprdat`  
 [out] Restituisce una matrice di `IRemoteDebugApplicationThread` interfacce che rappresenta i segmenti in corso il recupero.  
  
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
 [Interfaccia IEnumRemoteDebugApplicationThreads](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)