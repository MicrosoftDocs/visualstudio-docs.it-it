---
title: 'Idiaaddressmap:: Get_addressmapenabled | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cacee6377eebcc4e73f8f650bff4f4d3e500af66
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Indica se una mappa di indirizzo è stata definita per una determinata sessione.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pRetVal  
 [out] Restituisce `TRUE` se è abilitato il mapping degli indirizzi.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Post-processori di eseguibile talvolta aggiornare il file eseguibile. DIA contiene un meccanismo per supportare la conversione dei simboli per il nuovo layout.  
  
 Applicazioni client possono impostare la mappa indirizzi per una determinata sessione ottenendo il [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) interfaccia dal [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interfaccia e la chiamata il [IDiaAddressMap::set_ addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metodo seguita da una chiamata al [idiaaddressmap:: Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) metodo. Il `get_addressMapEnabled` restituisce i risultati della chiamata di `put_addressMapEnabled` metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)