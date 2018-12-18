---
title: Macro per la segnalazione | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5af21a708a05bfdc0338ca1c5b2bc038e192eb4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="macros-for-reporting"></a>Macro per la creazione di rapporti
È possibile utilizzare il **RPTn**, e **RPTFn** macro, definite in CRTDBG. H, per sostituire l'utilizzo di `printf` istruzioni per il debug. Queste macro vengono automaticamente eliminate nel rilascio di compilazione quando **debug** non è definito, pertanto non è necessario racchiuderle tra istruzioni **#ifdef**s.  
  
|Macro|Descrizione|  
|-----------|-----------------|  
|**RPT0**, **RPT1**, **RPT2**, **RPT3**, **RPT4**|Genera una stringa di messaggio e da zero a quattro argomenti. RPT1 a **RPT4**, la stringa di messaggio funge da stringa di formattazione per gli argomenti di tipo printf.|  
|**RPTF0**, **RPTF1**, **, RPTF2**, **RPTF4**|Uguale a **RPTn**, ma queste macro generano anche il numero di riga e il nome del file in cui si trova la macro.|  
  
 Si consideri l'esempio seguente:  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Questo codice restituisce i valori di `someVar` e `otherVar` a **stdout**. È possibile utilizzare la chiamata di `_RPTF2` che segue per restituire questi stessi valori nonché il nome file e il numero di riga:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Se si ritiene che una particolare applicazione necessiti di un tipo di report di debug che le macro fornite con la libreria di runtime del linguaggio C non offrono, sarà possibile scrivere una macro progettata appositamente per rispondere alle esigenze specifiche. In uno dei file di intestazione, ad esempio, è possibile includere codice simile al seguente per definire una macro denominata **ALERT_IF2**:  
  
```  
#ifndef _DEBUG                  /* For RELEASE builds */  
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)  
#else                           /* For DEBUG builds   */  
#define  ALERT_IF2(expr, msg, arg1, arg2) \  
    do { \  
        if ((expr) && \  
            (1 == _CrtDbgReport(_CRT_ERROR, \  
                __FILE__, __LINE__, msg, arg1, arg2))) \  
            _CrtDbgBreak( ); \  
    } while (0)  
#endif  
```  
  
 Una chiamata a **ALERT_IF2** è stato possibile eseguire tutte le funzioni del **printf** codice all'inizio di questo argomento:  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Dal momento che è possibile modificare facilmente una macro personalizzata in modo che invii un report con più o meno informazioni a diverse destinazioni (a seconda di ciò che risulta più comodo), questa tecnica può rivelarsi particolarmente utile con l'evolversi delle esigenze di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md)