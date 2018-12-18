---
title: Debug del codice nativo | Documenti Microsoft
ms.custom: 
ms.date: 04/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94f3d0cfd57f4d907bab758e52e0499b63941236
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-native-code"></a>Debug del codice nativo
In questa sezione vengono discussi alcuni problemi di debug comuni, nonché varie tecniche per le applicazioni native. Le tecniche illustrate in questa sezione sono di alto livello. Per informazioni sulle modalità di utilizzo del debugger di Visual Studio, vedere [Debugger Roadmap](../debugger/debugger-basics.md).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Procedura: Eseguire il debug di codice ottimizzato](../debugger/how-to-debug-optimized-code.md)  
 Vengono forniti suggerimenti per il debug del codice ottimizzato, in particolare sull'opportunità di eseguire il debug di una versione non ottimizzata del programma, sulle impostazioni di ottimizzazione predefinite per le configurazioni di debug e di rilascio e suggerimenti per la ricerca di bug visualizzati solo nel codice ottimizzato, attivando l'ottimizzazione nella configurazione di una build di debug.  
  
 [DebugBreak e __debugbreak](../debugger/debugbreak-and-debugbreak.md)  
 Viene descritta la funzione `DebugBreak` Win32 e viene fornito un collegamento all'argomento di riferimento in Platform SDK. Viene inoltre descritta la funzione intrinseca `__debugbreak`.  
  
 [Asserzioni C/C++](../debugger/c-cpp-assertions.md)  
 Vengono discusse le istruzioni di asserzione, il loro funzionamento, i vantaggi derivanti dal loro utilizzo (rilevamento di errori logici, controllo dei risultati di un'operazione e verifica delle condizioni di errore), l'interazione con `_DEBUG` e i tipi di asserzioni supportati in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 [Procedura: Eseguire il debug di codice assembly inline](../debugger/how-to-debug-inline-assembly-code.md)  
 Vengono fornite brevi istruzioni sull'utilizzo della finestra Disassembly per visualizzare le istruzioni di assembly e della finestra Registri per visualizzare il contenuto del Registro di sistema e vengono forniti collegamenti agli argomenti relativi a tali finestre.  
  
 [Tecniche di debug MFC](../debugger/mfc-debugging-techniques.md)  
 È possibile collegarsi alle tecniche di debug per programmi MFC, tra cui: afxDebugBreak, la macro TRACE, rilevamento di perdite di memoria in MFC, asserzioni MFC e riduzione della dimensione delle build di debug MFC.  
  
 [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md)  
 È possibile collegarsi alle tecniche di debug per la libreria di runtime del linguaggio C, tra cui: utilizzo della libreria di debug CRT, macro per la creazione di report, differenze tra malloc e _malloc_dbg, scrittura di funzioni hook di debug e heap di debug CRT.  
  
 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)  
 Vengono fornite risposte alle domande frequenti sul debug di programmi Visual C++.  
  
 [Debug di COM e ActiveX](../debugger/com-and-activex-debugging.md)  
 Vengono fornite informazioni sul debug delle applicazioni COM e ActiveX, inclusi gli strumenti da utilizzare al riguardo.  
  
 [Procedura: Eseguire il debug di codice inserito](../debugger/how-to-debug-injected-code.md)  
 Viene fornito materiale sussidiario sul debug del codice che utilizza gli attributi. Sono incluse istruzioni per l'attivazione del codice sorgente, la visualizzazione del codice inserito e del codice disassembly in corrispondenza del punto di esecuzione corrente.  
  
 [Procedura dettagliata: debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Viene descritto come utilizzare il **attività in parallelo** e **stack in parallelo** finestre degli strumenti di debug di un'applicazione parallela.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Tipi di progetto Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)  
 Vengono forniti collegamenti ad argomenti che descrivono le modalità di debug dei tipi di progetto nativi creati mediante i modelli di progetto di Visual C++.  

 [Debug di progetti DLL](../debugger/debugging-dll-projects.md) fornisce informazioni su come eseguire il debug di DLL native e gestite.
  
 [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)  
 Vengono forniti collegamenti a sezioni più ampie della documentazione sul debug. Vengono fornite informazioni sui seguenti argomenti: novità del debugger, impostazione e preparazione, punti di interruzione, gestione delle eccezioni, modifica e continuazione, debug di codice nativo, debug di SQL e riferimenti all'interfaccia utente.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)  
 [Debug in Visual Studio](../debugger/index.md) [Tour delle funzionalità del Debugger](../debugger/debugger-feature-tour.md)