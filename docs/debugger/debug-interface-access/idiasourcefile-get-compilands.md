---
title: IDiaSourceFile::get_compilands | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_compilands method
ms.assetid: 57deb50a-9c22-43ea-a80c-eab205997bc4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64e1d29f9f27dcbe2f85a7d9f4e015264d685be7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasourcefilegetcompilands"></a>IDiaSourceFile::get_compilands
Recupera un enumeratore dei moduli contenenti i numeri di riga che fa riferimento questo file.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_compilands (   
   IDiaEnumSymbols** ppRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppRetVal`  
 [out] Restituisce un [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) oggetto che contiene un elenco di tutti i moduli che hanno numeri di riga che fa riferimento questo file.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)