---
title: JIT debug e ottimizzazione | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2c3dcd57568bdfaac3ba0f7aff33cefca8a0ee32
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="jit-optimization-and-debugging"></a>Debug e ottimizzazione JIT
Quando si esegue il debug di un'applicazione gestita, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] disattivata l'ottimizzazione del codice di just-in-time (JIT) per impostazione predefinita. Viene pertanto eseguito il debug di codice non ottimizzato. L'esecuzione di codice non ottimizzato è più lenta, ma il debug è più completo. Il debug di codice ottimizzato è più complesso ed è consigliabile eseguirlo solo se un problema si verifica nel codice ottimizzato ma non può essere riprodotto nella versione non ottimizzata.  
  
 L'ottimizzazione JIT è controllata in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dal **disattivare l'ottimizzazione JIT al caricamento del modulo** opzione. Questa opzione è disponibile nel **generale** pagina il **debug** nodo il **opzioni** la finestra di dialogo.  
  
 Se si deseleziona la **disattivare l'ottimizzazione JIT al caricamento del modulo** opzione, è possibile eseguire il debug del codice JIT ottimizzato, ma la possibilità di eseguire il debug può risultare limitata poiché il codice ottimizzato non corrisponde al codice sorgente. Di conseguenza, finestre del debugger, ad esempio il **variabili locali** e **Auto** che non vengano visualizzate le informazioni presenti quando si esegue il debug di codice non ottimizzato.  
  
 Un'altra differenza importante riguarda il debug con Just My Code. Se si esegue il debug con Just My Code, il codice ottimizzato è ritenuto dal debugger codice non utente, che non deve essere visualizzato durante il debug. Se viene eseguito il debug di codice ottimizzato JIT, pertanto, è utile disattivare Just My Code. Per ulteriori informazioni, vedere [limitare l'accesso a Just My Code](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).  
  
 Tenere presente che il **disattivare l'ottimizzazione JIT al caricamento del modulo** opzione Disattiva l'ottimizzazione del codice quando vengono caricati i moduli. Se ci si connette a un processo già in esecuzione, è possibile che contenga codice già caricato, compilato tramite JIT e ottimizzato. Il **disattivare l'ottimizzazione JIT al caricamento del modulo** opzione ha effetto su tale codice, ma verrà effetto sui moduli caricati dopo la connessione. Inoltre, il **disattivare l'ottimizzazione JIT al caricamento del modulo** non influisce sulle moduli, ad esempio WinForms. dll, che vengono creati con NGEN.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Collegare a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Processo di esecuzione gestita](/dotnet/standard/managed-execution-process)