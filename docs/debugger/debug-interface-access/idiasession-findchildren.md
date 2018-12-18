---
title: 'Idiasession:: Findchildren | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cc9b9aabf920fa33828d86e2f0c3ac96f7e6dbdb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
Recupera tutti gli elementi figlio di un identificatore padre specificato che corrispondano al tipo di nome e il simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `parent`  
 [in] Un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che rappresenta l'elemento padre. Se questo simbolo padre è una funzione, un modulo o un blocco, quindi vengono restituiti i figli lessicali in `ppResult`. Se il simbolo padre è un tipo, vengono restituiti i figli di classe. Se questo parametro è `NULL`, quindi `symtag` deve essere impostato su `SymTagExe` o `SymTagNull`, che restituisce l'ambito globale (file .exe).  
  
 `symtag`  
 [in] Specifica il tag symbol degli elementi figlio da recuperare. I valori vengono prelevati i [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md) enumerazione. Impostare su `SymTagNull` per recuperare tutti gli elementi figlio.  
  
 `name`  
 [in] Specifica il nome degli elementi figlio da recuperare. Impostare su `NULL` per tutti gli elementi figlio da recuperare.  
  
 `compareFlags`  
 [in] Specifica le opzioni di confronto applicate al nome corrispondente. I valori di [NameSearchOptions (enumerazione)](../../debugger/debug-interface-access/namesearchoptions.md) enumerazione può essere utilizzato da solo o in combinazione.  
  
 `ppResult`  
 [out] Restituisce un [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) recuperare l'oggetto che contiene l'elenco di simboli figlio.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come trovare le variabili locali della funzione `pFunc` nome corrispondenza `szVarName`.  
  
```C++  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions (enumerazione)](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md)