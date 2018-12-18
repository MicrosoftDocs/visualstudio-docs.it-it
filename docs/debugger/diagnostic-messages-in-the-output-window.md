---
title: Inviare i messaggi diagnostici nella finestra di Output | Documenti Microsoft
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfe7cb6660d16c093889395a082c9fd58e5d0431
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="send-diagnostic-messages-to-the-output-window"></a>Inviare i messaggi diagnostici nella finestra di Output
È possibile scrivere messaggi in fase di esecuzione per il **Output** finestra tramite il `Debug` classe o `Trace` (classe), che fanno parte di <xref:System.Diagnostics> libreria di classi. Utilizzare la classe Debug se si desidera generare l'output solo nella versione di debug del programma e la classe Trace se si desidera generare l'output sia nella versione di debug che in quella di rilascio del programma.  
  
## <a name="output-methods"></a>Metodi di output  
 Le classi <xref:System.Diagnostics.Trace> e <xref:System.Diagnostics.Debug> forniscono i seguenti metodi di output:  
  
-   Diversi metodi `Write`, che generano informazioni senza interrompere l'esecuzione. Questi metodi sostituiscono il metodo `Debug.Print` utilizzato nelle versioni precedenti di Visual Basic.  
  
-   I metodi <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> and <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, che interrompono l'esecuzione e generano informazioni se si verifica un errore relativo a una condizione specificata. Per impostazione predefinita, il metodo `Assert` visualizza le informazioni in una finestra di dialogo. Per ulteriori informazioni, vedere [asserzioni nel codice gestito](../debugger/assertions-in-managed-code.md).  
  
-   I metodi <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>, che interrompono sempre l'esecuzione e generano informazioni. Per impostazione predefinita, i metodi `Fail` visualizzano le informazioni in una finestra di dialogo.  
  
 Oltre a programma dall'applicazione, il **Output** finestra possono essere visualizzate le informazioni riguardanti:  
  
-   I moduli caricati o scaricati dal debugger.  
  
-   Le eccezioni generate.  
  
-   I processi chiusi.  
  
-   I thread chiusi.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Finestra di output](../ide/reference/output-window.md)   
 [Traccia e strumentazione di applicazioni](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debug di codice gestito](../debugger/debugging-managed-code.md)