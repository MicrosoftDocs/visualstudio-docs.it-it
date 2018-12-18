---
title: IDiaSectionContrib::get_comdat | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_comdat method
ms.assetid: 8bd9be8d-59ee-4698-b055-daba354b8dcc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 578314d0771d156fe66bdfbf661ffca98844207f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasectioncontribgetcomdat"></a>IDiaSectionContrib::get_comdat
Recupera un flag che indica se la sezione è un record COMDAT.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_comdat (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce `TRUE` se la sezione è un record COMDAT; in caso contrario, restituisce `FALSE`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un record COMDAT è un record comuni oggetto COFF (File Format) che rende visibili al linker funzioni incluse nel pacchetto.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)