---
title: 'Idiaenumsectioncontribs:: Item | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 00b60f0915ca4e9a4f56cabca05122a5cdebbd6d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
Recupera i contributi di sezione tramite un indice.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 indice  
 [in] Indice del [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) oggetto da recuperare. L'indice è compreso nell'intervallo da 0 a `count`-1, dove `count` restituito dal [IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) metodo.  
  
 section  
 [out] Restituisce un [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) oggetto che rappresenta il contributo di sezione desiderata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Idiaenumsectioncontribs](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)