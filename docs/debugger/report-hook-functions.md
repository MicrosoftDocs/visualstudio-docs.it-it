---
title: Funzioni hook per la creazione di report | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 958c33c623830af509185b3d35ef8a8b5956aaae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="report-hook-functions"></a>Funzioni hook per la creazione di rapporti
Una funzione hook di report, installata mediante [CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), viene chiamato ogni volta [CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) genera un report di debug. È possibile utilizzare tale funzione, ad esempio, per filtrare i report in modo da concentrarsi su tipi specifici di allocazioni. Una funzione hook per la creazione di report deve avere un prototipo analogo al seguente:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Il puntatore passato a **CrtSetReportHook** è di tipo **CRT_REPORT_HOOK**, come definito in CRTDBG. H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Quando la libreria di runtime chiama la funzione hook, il *nRptType* argomento contiene la categoria del report (**CRT_WARN**, **CRT_ERROR**, o **_CRT Assert**), *szMsg* contiene un puntatore a una stringa di messaggio di report completa, e *retVal* specifica se `_CrtDbgReport` deve continuare l'esecuzione normale Dopo aver generato il report o avviare il debugger. (A *retVal* valore zero l'esecuzione continua, il valore 1 viene avviato il debugger.)  
  
 Se la funzione hook gestisce il messaggio in questione completamente, in modo che sia necessario alcun report ulteriore, deve restituire **TRUE**. Se restituisce **FALSE**, `_CrtDbgReport` visualizzerà il messaggio normalmente.  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di funzioni Hook di debug](../debugger/debug-hook-function-writing.md)   
 [Esempio crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)