---
title: 'Idiasymbol:: Get_lexicalparent | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lexicalParent method
ms.assetid: 4d119965-33a8-474c-9c64-95c5218c389c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8180b9110aeb0010398eea5e19efed34fefc921
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetlexicalparent"></a>IDiaSymbol::get_lexicalParent
Recupera un riferimento all'elemento padre lessicale del simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_lexicalParent (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che rappresenta il padre lessicale del simbolo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Note  
 L'elemento lessicale padre di un simbolo è la funzione o il modulo contenitore. Ad esempio, lessicale padre di un parametro di funzione o una variabile locale è la funzione stessa mentre lessicale padre della funzione è il modulo in cui è definito.  
  
 I simboli possibili che possono essere visualizzati come elementi lessicali padre sono documentati in [gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md).  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)