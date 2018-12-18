---
title: IDiaInjectedSource::get_filename | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_filename method
ms.assetid: 20f4fc68-335a-4971-b3a6-76501f0e8b19
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ff17132635f2170e8636d86d4e989368c05778b8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiainjectedsourcegetfilename"></a>IDiaInjectedSource::get_filename
Recupera il nome del file per l'origine.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_filename (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pRetVal  
 [out] Restituisce il nome del file per l'origine.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)