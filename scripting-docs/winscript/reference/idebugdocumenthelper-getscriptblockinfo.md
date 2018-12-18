---
title: IDebugDocumentHelper::GetScriptBlockInfo | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.GetScriptBlockInfo
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::GetScriptBlockInfo
ms.assetid: 332d7540-bbbe-4747-95ec-e47384d4f4e6
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e8dc63b8419424ed3fa01f67d3e77f0bc2b57f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelpergetscriptblockinfo"></a>IDebugDocumentHelper::GetScriptBlockInfo
Recupera l'intervallo di caratteri e il motore di script corrispondente a un blocco di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetScriptBlockInfo(  
   DWORD_PTR        dwSourceContext,  
   IActiveScript**  ppasd,  
   ULONG*           piCharPos,  
   ULONG*           pcChars  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwSourceContext`  
 [in] Il contesto di origine per il blocco di script.  
  
 `ppasd`  
 [out] Il motore di script per questo blocco di script.  
  
 `piCharPos`  
 [out] Posizione di inizio del blocco di script.  
  
 `cChars`  
 [out] Numero di caratteri nel blocco di script.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo recupera l'intervallo di caratteri e il motore di script corrispondente a un blocco di script.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)