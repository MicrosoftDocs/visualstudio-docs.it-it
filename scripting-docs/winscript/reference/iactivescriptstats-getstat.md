---
title: IActiveScriptStats::GetStat | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStat
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35e791661de6d360f747f8d823ad073c2eb81115
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Restituisce una delle statistiche script standard.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `stid`  
 [in] Specifica quale statistica da restituire. Il valore deve essere:  
  
|Costante|Valore|Descrizione|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Restituisce il numero di istruzioni eseguite dallo script di avvio o la reimpostazione delle statistiche.|  
  
 `pluHi`  
 [out] 32 bit alti di un intero senza segno a 64 bit che rappresenta la statistica.  
  
 `pluLo`  
 [out] 32 bit bassi di un intero senza segno a 64 bit che rappresenta la statistica.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati ai valori nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce una delle statistiche script standard.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [Interfaccia IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)