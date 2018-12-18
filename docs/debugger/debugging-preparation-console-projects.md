---
title: 'Preparazione al debug: Progetti di Console | Documenti Microsoft'
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
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b864ed1a1c0a105a0ab5f441f6d7a9a935dc6dc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="debugging-preparation-console-projects"></a>Preparazione al debug: progetti di console
La preparazione per il debug di un progetto console è simile a quella di un progetto Windows, ma è necessario tenere presente alcune ulteriori considerazioni. Per ulteriori informazioni, vedere [applicazioni Windows Forms](../debugger/debugging-preparation-windows-forms-applications.md), e [preparazione al debug: applicazioni form Windows (.NET)](http://msdn.microsoft.com/en-us/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5). A causa delle similitudini esistenti tra tutte le applicazioni console, in questo argomento vengono trattati i seguenti tipi di progetto:  
  
-   Applicazione console C#  
  
-   Applicazione console Visual Basic  
  
-   Applicazione console C++ (.NET)  
  
-   Applicazione console C++ (Win32)  
  
 Potrebbe essere necessario specificare gli argomenti della riga di comando per l'applicazione console. Per ulteriori informazioni, vedere [le impostazioni di progetto per una configurazione di Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [le impostazioni di progetto per una configurazione di Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), o [le impostazioni di progetto per configurazioni di Debug c# ](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
 Come tutte le proprietà di progetto, questi argomenti sono persistenti tra le sessioni di debug e tra le sessioni di Visual Studio. Pertanto, se l'applicazione console è uno in precedenza è eseguito il debug, ricordare che potrebbero essere presenti gli argomenti da sessioni precedenti la  **\<progetto > pagine delle proprietà** la finestra di dialogo.  
  
 Un'applicazione console utilizza il **Console** finestra per accettare l'input e visualizzare i messaggi di output. Per scrivere il **Console** finestra, l'applicazione deve usare il **Console** oggetto anziché l'oggetto del Debug. Per scrivere il **Output di Visual Studio** finestra, utilizzare l'oggetto Debug come di consueto. Assicurarsi di conoscere la posizione di scrittura dell'applicazione per evitare di cercare i messaggi nella finestra errata. Per ulteriori informazioni, vedere [classe Console](/dotnet/api/system.console), [classe Debug](/dotnet/api/system.diagnostics.debug), e [finestra di Output](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Avvio dell'applicazione  
 Quando vengono avviate, alcune applicazioni console vengono eseguite fino al completamento, quindi si chiudono. Questo comportamento potrebbe non lasciare tempo sufficiente per interrompere l'esecuzione e per il debug. Per eseguire il debug di un'applicazione, utilizzare una delle procedure riportate di seguito per avviare l'applicazione:  
  
-   L'applicazione viene avviata l'esecuzione e viene eseguito finché raggiunge il punto di interruzione.  
  
-   L'applicazione viene avviata e immediatamente interrotta alla prima riga di codice sorgente.  
  
-   In una finestra del codice sorgente, fare doppio clic su una riga e selezionare **Esegui fino al cursore**.  
  
     L'applicazione viene avviata ed eseguita fino alla riga selezionata o a un punto di interruzione, se questo viene raggiunto prima della riga.  
  
 Durante il debug di un'applicazione console, può essere necessario avviare l'applicazione dal prompt dei comandi anziché da Visual Studio. In tal caso, è possibile avviare l'applicazione dal prompt dei comandi e connettervi il debugger di Visual Studio. Per ulteriori informazioni, vedere [connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Quando si avvia un'applicazione console da Visual Studio, il **Console** talvolta verrà visualizzata la finestra dietro la finestra di Visual Studio. Se si tenta di avviare l'applicazione console da Visual Studio senza alcun apparente risultato, provare a spostare la finestra di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug del codice nativo](../debugger/debugging-native-code.md)   
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Tipi di progetto di Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Impostazioni di progetto per una configurazione di Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)