---
title: Utilizzo in fase di esecuzione dei controlli senza la libreria di Run-Time C | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fc81dd57ca6a91cd748da82c792c2bbeca88bb25
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Utilizzo dei controlli runtime senza la libreria di runtime del linguaggio C
Se si collega il programma senza la libreria di runtime C, utilizzando **/NODEFAULTLIB**e si desidera utilizzare i controlli in fase di esecuzione, è necessario collegare con la libreria RunTmChk.lib.  
  
 `_RTC_Initialize` consente di inizializzare il programma per i controlli runtime. Se non si stabilisce il collegamento con la libreria di runtime del linguaggio C, è necessario verificare che il programma sia compilato con i controlli degli errori di runtime prima di chiamare `_RTC_Initialize`, come illustrato di seguito:  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 Se non si stabilisce il collegamento con la libreria di runtime del linguaggio C, è necessario definire anche una funzione chiamata `_CRT_RTC_INITW`. `_CRT_RTC_INITW` consente di installare la funzione definita dall'utente come funzione di segnalazione degli errori predefinita, come illustrato di seguito:  
  
```  
// C version:  
_RTC_error_fnW __cdecl _CRT_RTC_INITW(  
        void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler.  
    return &MyErrorFunc;   
}  
  
// C++ version:  
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(  
       void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler:  
    return &MyErrorFunc;  
}  
```  
  
 Dopo aver installato la funzione di segnalazione degli errori predefinita, sarà possibile installare altre funzioni di segnalazione degli errori con `_RTC_SetErrorFuncW`. Per ulteriori informazioni, vedere [RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Usare controlli runtime nativi](../debugger/how-to-use-native-run-time-checks.md)