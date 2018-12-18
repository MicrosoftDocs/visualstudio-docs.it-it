---
title: 'Idiainjectedsource:: Get_source | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c58989c6958aa8a604f5e7c7a9ef5c4d3eb84f1f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idiainjectedsourcegetsource"></a>IDiaInjectedSource::get_source
Recupera i byte di codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cbData`  
 [in] Il numero di byte che rappresenta le dimensioni del buffer di dati.  
  
 `pcbData`  
 [out] Restituisce il numero di byte che rappresenta i byte. Se `data` è `NULL`, quindi `pcbData` è disponibile il numero totale di byte di dati.  
  
 `data[]`  
 [out] Un buffer che deve essere compilato con i byte di origine.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)