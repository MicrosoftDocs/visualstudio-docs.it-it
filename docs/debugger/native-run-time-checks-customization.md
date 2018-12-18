---
title: Personalizzazione dei controlli runtime nativo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a9483983b6cbd5644827af8f647425cce61502ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="native-run-time-checks-customization"></a>Personalizzazione dei controlli runtime nativi
Quando esegue la compilazione con **/RTC** (controlli in fase di esecuzione) oppure utilizzare il `runtime_checks` pragma, la libreria di run-time C fornisce i controlli runtime nativi. In alcuni casi può essere necessario personalizzare il controllo runtime:  
  
-   Per indirizzare i messaggi del controllo runtime a un file o una destinazione diversa da quella predefinita.  
  
-   Per specificare una destinazione di output dei messaggi del controllo runtime in un debugger di altri produttori.  
  
-   Per segnalare i messaggi del controllo runtime provenienti da un programma compilato con una versione di rilascio della libreria di runtime del linguaggio C. Nelle versioni di rilascio della libreria per segnalare gli errori di runtime non viene utilizzato `_CrtDbgReportW` Viene invece visualizzata una **Assert** la finestra di dialogo per ogni errore di run-time.  
  
 Per personalizzare il controllo degli errori di runtime, è possibile utilizzare uno degli accorgimenti seguenti:  
  
-   Scrivere una funzione per la segnalazione degli errori di runtime. Per ulteriori informazioni, vedere [procedura: scrivere una funzione di segnalazione errore di Run-Time](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
-   Personalizzare la destinazione dei messaggi di errore.  
  
-   Eseguire una query per ottenere informazioni sugli errori rilevati dai controlli runtime.  
  
## <a name="customize-the-error-message-destination"></a>Personalizzare la destinazione dei messaggi di errore  
 Se si utilizza `_CrtDbgReportW` per la segnalazione degli errori, è possibile utilizzare `_CrtSetReportMode` per specificare la destinazione dei messaggi di errore.  
  
 Se si utilizza una funzione di segnalazione degli errori personalizzata, utilizzare `_RTC_SetErrorType` per associare un tipo di report a ciascun errore.  
  
## <a name="query-for-information-about-run-time-checks"></a>Eseguire una query per ottenere informazioni sui controlli runtime  
 `_RTC_NumErrors` restituisce il numero di tipi di errore rilevati dai controlli degli errori di runtime. Per ottenere una breve descrizione di ciascun errore, è possibile creare un ciclo da 0 al valore restituito da `_RTC_NumErrors` passando il valore di iterazione a `_RTC_GetErrDesc` in ciascun ciclo. Per ulteriori informazioni, vedere [RTC_NumErrors](/cpp/c-runtime-library/reference/rtc-numerrors) e [RTC_GetErrDesc](/cpp/c-runtime-library/reference/rtc-geterrdesc).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: utilizzare controlli runtime nativi](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](/cpp/preprocessor/runtime-checks)   
 [_CrtDbgReport, _CrtDbgReportW](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)