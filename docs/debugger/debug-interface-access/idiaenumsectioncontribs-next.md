---
title: 'Idiaenumsectioncontribs:: Next | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f700ef7160cff643c2a60007d7b1f83ecbe4eeb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
Recupera un numero specificato di contributi di sezione nella sequenza di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Next(   
   ULONG                celt,   
   IDiaSectionContrib** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 celt  
 [in] Il numero dei contributi di sezione nell'enumeratore deve essere recuperato.  
  
 rgelt  
 [out] Matrice che deve essere compilato con la [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) gli oggetti che rappresentano i contributi di sezione desiderata.  
  
 pceltFetched  
 [out] Restituisce il numero dei contributi di sezione nell'enumeratore recuperata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non esistono alcun ulteriori contributi di sezione. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)