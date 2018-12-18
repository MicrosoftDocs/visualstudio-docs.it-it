---
title: IDiaStackWalkFrame::searchForReturnAddress | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::searchForReturnAddress method
ms.assetid: 1a54c50d-94af-4a43-ac4e-d80c5df156c3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47eeea9e72989454c0b9f22a1f3196f61128571d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiastackwalkframesearchforreturnaddress"></a>IDiaStackWalkFrame::searchForReturnAddress
Cerca il frame dello stack specificato per l'indirizzo restituito della funzione più vicino.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT searchForReturnAddress (   
   IDiaFrameData* frame,  
   ULONGLONG*     returnAddress  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `frame`  
 [in] Un [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) oggetto che rappresenta lo stack frame corrente.  
  
 `returnAddress`  
 [out] Restituisce l'indirizzo restituito di funzione più vicino.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)