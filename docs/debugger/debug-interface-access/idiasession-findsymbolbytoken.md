---
title: IDiaSession::findSymbolByToken | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByToken method
ms.assetid: 3c92149c-6eef-454f-86be-66e89557b9e6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f7152a3953475ac2622033101ca739b0b8ee300
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasessionfindsymbolbytoken"></a>IDiaSession::findSymbolByToken
Recupera il simbolo che contiene un token di metadati specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT findSymbolByToken (   
   ULONG        token,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `token`  
 [in] Specifica il token.  
  
 `symtag`  
 [in] Tipo di simbolo da trovare. I valori vengono prelevati i [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md) enumerazione.  
  
 `ppSymbol`  
 [out] Restituisce un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) recuperare l'oggetto che rappresenta il simbolo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="example"></a>Esempio  
  
```C++  
IDiaSymbol* pFunc;  
pSession->findSymbolByToken( token, SymTagFunction, &pFunc );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md)