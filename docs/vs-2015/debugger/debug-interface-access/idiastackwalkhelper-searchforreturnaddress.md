---
title: IDiaStackWalkHelper::searchForReturnAddress | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::searchForReturnAddress method
ms.assetid: 904223b1-6e26-4980-b310-d0b222cdbbbd
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 935621b6a9eff8fdef53b76be95065fa6ed050fc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520021"
---
# <a name="idiastackwalkhelpersearchforreturnaddress"></a>IDiaStackWalkHelper::searchForReturnAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDiaStackWalkHelper::searchForReturnAddress](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress).  
  
Cerca stack frame specificato per l'indirizzo del mittente (funzione) più vicino.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT searchForReturnAddress(   
   IDiaFrameData*  frame,  
   ULONGLONG*      returnAddress  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `frame`  
 [in] Un' [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) oggetto che rappresenta lo stack frame corrente.  
  
 `returnAddress`  
 [out] Restituisce l'indirizzo del mittente (funzione) più vicino.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



