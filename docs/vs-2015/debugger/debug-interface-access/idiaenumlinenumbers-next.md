---
title: Idiaenumlinenumbers | Microsoft Docs
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
- IDiaEnumLineNumbers::Next method
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd97750490220ecc83ab1581a19aa6f49ea1f0a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529107"
---
# <a name="idiaenumlinenumbersnext"></a>IDiaEnumLineNumbers::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Idiaenumlinenumbers](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumlinenumbers-next).  
  
Recupera un determinato numero di numeri di riga nella sequenza di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Next (   
   ULONG            celt,  
   IDiaLineNumber** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 celt  
 [in] Il numero di numeri di riga nell'enumeratore deve essere recuperato.  
  
 rgelt  
 [out] Restituisce una matrice di [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) gli oggetti che rappresentano i numeri di riga desiderato.  
  
 pceltFetched  
 [out] Restituisce il numero di numeri di riga nell'enumeratore recuperata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non esistono Nessun più numeri di riga. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)



