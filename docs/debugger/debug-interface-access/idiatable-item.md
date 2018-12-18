---
title: 'Idiatable:: Item | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd734d287a4740a25840d93b4724b45396c7dd87
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiatableitem"></a>IDiaTable::Item
Recupera un riferimento alla voce specificata nella tabella.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `index`  
 [in] L'indice della voce di tabella nell'intervallo da 0 a `count`-1, dove `count` restituito dal [idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md)metodo.  
  
 `element`  
 [out] Restituisce un `IUnknown` oggetto che rappresenta la voce della tabella specificata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Una tabella rappresenta una raccolta di oggetti. In base a tali oggetti, è possibile eseguire il cast del parametro di elemento per l'interfaccia appropriata. Ad esempio, se una tabella contiene [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) oggetti, quindi il parametro dell'elemento può essere convertito nel `IDiaSegment` interfaccia.  
  
 È un approccio più comune per chiamare il `QueryInterface` metodo il [IDiaTable](../../debugger/debug-interface-access/idiatable.md) l'interfaccia per l'interfaccia di enumeratore appropriato e utilizzare i metodi specifici dell'enumeratore per accedere al contenuto della tabella. Vedere il [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interfaccia per un esempio.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [Idiatable](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)