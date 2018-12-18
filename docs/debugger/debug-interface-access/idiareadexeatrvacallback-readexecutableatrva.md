---
title: IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 71dd19f15d631c58e99a826ab1ff274b993afd5e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Legge il numero specificato di byte a partire specificato indirizzo virtuale relativo (RVA) dal file eseguibile.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `relativeVirtualAddress`  
 [in] RVA nel file eseguibile per iniziare la lettura.  
  
 `cbData`  
 [in] Numero di byte da leggere.  
  
 `pcbData`  
 [out] Restituisce il numero di byte letti.  
  
 `data[]`  
 [in, out] Matrice che viene riempita con byte letti dal file.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato dal codice di supporto di DIA per caricare i byte di dati da un eseguibile usando un indirizzo virtuale relativo. Questo metodo viene chiamato supportano il [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)