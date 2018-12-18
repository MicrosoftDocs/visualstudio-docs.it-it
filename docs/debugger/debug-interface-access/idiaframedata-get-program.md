---
title: 'Idiaframedata:: Get_program | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2c78c6f1c2c6e8368efd86dc3ffa03a021e46da3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
Recupera la stringa viene utilizzata per calcolare il set prima della chiamata alla funzione corrente di registri.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce la stringa di programma.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 La stringa di programma è una sequenza di macro che viene interpretata per stabilire il prologo. Ad esempio, un frame di stack tipico potrebbe utilizzare la stringa di programma `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. Il formato è una notazione polacca inversa in cui gli operatori seguono gli operandi. `T0` rappresenta una variabile temporanea nello stack. Questo esempio viene eseguita la procedura seguente:  
  
1.  Spostare il contenuto del registro `ebp` a `T0`.  
  
2.  Aggiungere `4` al valore di `T0` per produrre un indirizzo, ottenere il valore da tale indirizzo e archiviare il valore nel registro `eip`.  
  
3.  Ottenere il valore dall'indirizzo archiviato in `T0` e il valore memorizzato nel registro `ebp`.  
  
4.  Aggiungere `8` al valore di `T0` e il valore memorizzato nel registro `esp`.  
  
 Si noti che la stringa del programma è specifica per la CPU e la convenzione di chiamata impostato per la funzione rappresentata dallo stack frame corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)