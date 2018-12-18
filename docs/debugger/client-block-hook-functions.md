---
title: Funzioni Hook del blocco client | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eccc1781174394da333d2fc703fec0b4d31e522a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="client-block-hook-functions"></a>Funzioni hook del blocco client
Se si desidera convalidare o inserire in report il contenuto dei dati memorizzati in blocchi `_CLIENT_BLOCK`, sarà possibile scrivere una funzione specificamente per tale scopo. Tale funzione dovrà avere un prototipo analogo al seguente, come definito in CRTDBG.H:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 In altre parole, la funzione hook consiglia di accettare un **void** puntatore all'inizio del blocco di allocazione, insieme a un **size_t** tipo di valore che indica la dimensione dell'allocazione e restituire `void`. Non esistono altre limitazioni al contenuto.  
  
 Dopo aver installato la funzione hook mediante [CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), verrà chiamato ogni volta un `_CLIENT_BLOCK` il dump di blocco. È quindi possibile utilizzare [CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) per ottenere informazioni sul tipo o sottotipo dei blocchi di dump.  
  
 Puntatore alla funzione che viene passato a `_CrtSetDumpClient` è di tipo **CRT_DUMP_CLIENT**, come definito in CRTDBG. H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di funzioni Hook di debug](../debugger/debug-hook-function-writing.md)   
 [Esempio crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)