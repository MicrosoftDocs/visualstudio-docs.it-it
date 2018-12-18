---
title: 'Idiasession:: Put_loadaddress | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0b04db800e5b61ef1598fe4c81a9ab362e375e3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
Imposta l'indirizzo di caricamento del file eseguibile che corrisponde ai simboli in questo archivio dei simboli.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `NewVal`  
 [in] Carica l'indirizzo del file eseguibile.  
  
## <a name="remarks"></a>Note  
 Proprietà dei simboli indirizzo virtuale (VA) vengono calcolate utilizzando il valore di questo metodo. Gli indirizzi virtuali non vengono calcolati a meno che questa proprietà è impostata su diverso da zero.  
  
> [!NOTE]
>  È necessario chiamare questo metodo quando si ottengono il [IDiaSession](../../debugger/debug-interface-access/idiasession.md) dell'oggetto e prima di iniziare a utilizzare l'oggetto se è necessario utilizzare le proprietà virtuali simboli.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)