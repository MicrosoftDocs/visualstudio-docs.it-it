---
title: 'Idiasession:: Put_loadaddress | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f4721ee818c4dc75d883c7accd2faa162521de13
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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