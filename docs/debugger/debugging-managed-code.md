---
title: Debug di codice gestito | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 227dfcf82a179a83428900f75d0b5c9b85248479
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="debugging-managed-code"></a>Debug del codice gestito

In questa sezione vengono descritti alcuni problemi di debug comuni e vengono illustrate varie tecniche per le applicazioni gestite, ovvero scritte in linguaggi compatibili con Common Language Runtime, ad esempio Visual Basic, C# e C++. Le tecniche descritte sono di livello avanzato. Per ulteriori informazioni, vedere [utilizzando il Debugger](../debugger/debugger-basics.md).

## <a name="in-this-section"></a>In questa sezione

[Messaggi diagnostici nella finestra di output](../debugger/diagnostic-messages-in-the-output-window.md)  
Viene descritto il <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace> classi, con cui è possibile scrivere messaggi in fase di esecuzione per il **Output** finestra. Queste classi includono metodi di output che supportano l'output di informazioni senza interruzione dell'esecuzione e l'output di informazioni con interruzione dell'esecuzione se non viene rispettata una condizione specificata.

[Asserzioni nel codice gestito](../debugger/assertions-in-managed-code.md)  
Vengono descritte le asserzioni nel codice gestito, che verificano le condizioni specificate come argomenti per i metodi `Assert`. In questo argomento vengono anche forniti il codice di esempio, le informazioni sull'utilizzo dei metodi <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace>, le considerazioni sulle versioni di debug e di rilascio del codice, gli effetti secondari, gli argomenti assert, la personalizzazione del comportamento assert e i file di configurazione.

[Istruzioni Stop in Visual Basic](../debugger/stop-statements-in-visual-basic.md)  
Viene descritta l'istruzione `Stop`, che fornisce un'alternativa all'impostazione di un punto di interruzione. Sono inoltre disponibili esempi di codice e un confronto tra le istruzioni `Stop` ed `End` e tra le istruzioni `Stop` e `Assert`.

[Procedura dettagliata: debug di un Windows Form](../debugger/walkthrough-debugging-a-windows-form.md)  
Vengono date istruzioni dettagliate per la creazione di un Windows Form e per il debug di tale form. Un Windows Form, un componente standard di un'applicazione Windows gestita, è una delle applicazioni gestite più comuni. In questa procedura dettagliata vengono utilizzati Visual C# e Visual Basic, ma le tecniche per la creazione di un Windows Form con C++ sono simili.

[Debug del metodo OnStart](../debugger/how-to-debug-the-onstart-method.md)  
Vengono forniti codici di esempio per consentire il debug del metodo `OnStart` di un servizio Windows gestito. Per eseguire il debug del metodo `OnStart` di un servizio Windows, è necessario aggiungere alcune righe di codice per simulare il servizio.

[Debug in modalità mista](../debugger/debugging-mixed-mode-applications.md)  
Viene descritto il debug di applicazioni in modalità mista, ovvero qualsiasi applicazione nella quale vengono combinati codice nativo e codice gestito.

[Errore: impossibile eseguire il debug perché nel sistema è attivato un debugger del kernel](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)  
Viene descritto un messaggio di errore che si verifica se si tenta di eseguire il debug di codice gestito su un [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)], o il sistema di Windows NT che è stato avviato in modalità di debug.

[Debug e ottimizzazione JIT](../debugger/jit-optimization-and-debugging.md)  
Vengono descritti gli effetti dell'ottimizzazione JIT sul debug.

[Debug LINQ e DLINQ](../debugger/debugging-linq.md)  
Vengono illustrate le tecniche per il debug di query LINQ.

[Procedura dettagliata: debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)  
Viene descritto come utilizzare il **attività in parallelo** e **stack in parallelo** finestre degli strumenti di debug di un'applicazione parallela.

## <a name="related-sections"></a>Sezioni correlate

[IntelliTrace](../debugger/intellitrace.md) individuare i bug più veloci e semplici registrando la cronologia di esecuzione dell'app con IntelliTrace. Eseguire all'indietro e in avanti gli eventi registrati e le chiamate per esaminare lo stato dell'app in determinati momenti. Eseguire il debug del codice senza impostare molti punti di interruzione o riavviare l'app con frequenza. È necessario Visual Studio Enterprise.

[Traccia e strumentazione di applicazioni](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
Vengono descritte la traccia, che consente di monitorare l'esecuzione dell'applicazione, e la strumentazione, che prevede l'inserimento di istruzioni di traccia in corrispondenza di posizioni strategiche nel codice. In questo argomento vengono anche forniti collegamenti a un'introduzione all'instrumentazione e alla traccia, opzioni di traccia, listener di traccia, traccia del codice in un'applicazione, aggiunta di istruzioni di traccia al codice dell'applicazione e compilazione in modo condizionale con <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace>.

[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)  
Viene descritta un'opzione del linker che aggiunge <xref:System.Diagnostics.DebuggableAttribute> a codice scritto con C++. Questo attributo è necessario per l'utilizzo di funzionalità di debug, quali la connessione con C++.

[Il debug delle applicazioni di servizio Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)  
Vengono fornite considerazioni per il debug di applicazioni di servizio Windows, quali: impostazione, connessione al processo, debug del codice nel metodo `OnStart` del servizio e il codice nel metodo Main, impostazione di punti di interruzione e utilizzo di Services Control Manager per avviare, interrompere, arrestare e continuare il servizio.

[Debug e profilatura](/dotnet/framework/debug-trace-profile/index)  
Viene discusso il debug di applicazioni .NET Framework e i requisiti di configurazione.

[Debug di Script e applicazioni Web](../debugger/debugging-web-applications-and-script.md)  
Vengono presentati le tecniche di debug e i problemi più comuni riscontrabili durante il debug di script e applicazioni Web.

[Novità relative al Debugger di Visual Studio 2015](../debugger/what-s-new-for-the-debugger-in-visual-studio.md)  
Vengono descritte le nuove funzionalità di debug integrate in questa versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

[Debug in Visual Studio](../debugger/debugger-feature-tour.md)  
Vengono forniti collegamenti a sezioni più ampie della documentazione sul debug. Le informazioni fornite comprendono: novità del debugger, impostazioni e preparazione, punti di interruzione, gestione delle eccezioni, modifica e continuazione, debug di codice gestito, debug di progetti Visual C++, debug di COM e ActiveX, debug di DLL, debug di SQL e riferimenti per l'interfaccia utente.

## <a name="see-also"></a>Vedere anche

[Procedura dettagliata: Debug Windows Form personalizzati controlli in fase di progettazione](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
[sicurezza del Debugger](../debugger/debugger-security.md)
[debug in Visual Studio](../debugger/index.md) 
 [ Panoramica delle funzionalità del debugger](../debugger/debugger-feature-tour.md)