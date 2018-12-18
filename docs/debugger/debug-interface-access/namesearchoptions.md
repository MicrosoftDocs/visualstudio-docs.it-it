---
title: NameSearchOptions | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f95d5ed2e91b847b99d063b6fcba485fb96c3290
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="namesearchoptions"></a>NameSearchOptions
Specifica le opzioni di ricerca per i nomi dei simboli e file.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## <a name="elements"></a>Elementi  
 `nsNone`  
 Non è stata specificata alcuna opzione.  
  
 `nsfCaseSensitive`  
 Si applica una corrispondenza tra maiuscole e minuscole di nome.  
  
 `nsfCaseInsensitive`  
 Si applica una corrispondenza tra maiuscole e minuscole di nome.  
  
 `nsfFNameExt`  
 Considera i nomi dei percorsi e applica una corrispondenza di nome nomefile. ext.  
  
 `nsfRegularExpression`  
 Si applica una corrispondenza tra maiuscole e minuscole nome utilizzando l'asterisco (*) e punti interrogativi (?) come carattere jolly.  
  
 `nsfUndecoratedName`  
 Si applica solo ai simboli che hanno non decorati e i nomi decorati.  
  
## <a name="remarks"></a>Note  
 I valori di questa enumerazione vengono passati ai metodi seguenti:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: dia2.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Idiasession](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)