---
title: Debug di applicazioni multithreading in Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 09/05/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd789bf9b820e13a265cceffbf3c6000ab4f0331
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debug di applicazioni multithreading in Visual Studio
Un thread è una sequenza di istruzioni in base alla quale il sistema operativo esegue l'allocazione del tempo processore. Ogni processo in esecuzione nel sistema operativo è composto da almeno un thread. I processi composti da più di un thread sono detti multithreading.  
  
I computer multiprocessore, i processori multicore e i processi hyperthreading sono in grado di eseguire contemporaneamente più thread. Se da un lato l'elaborazione parallela di più thread può migliorare notevolmente le prestazioni dei programmi, dall'altro può rendere il debug più difficoltoso poiché introduce la necessità di tenere traccia di più thread.  
  
Il multithreading introduce inoltre nuovi tipi di possibili bug. Accade spesso, ad esempio, che due o più thread debbano accedere alla stessa risorsa, alla quale però può accedere un solo thread alla volta. Deve necessariamente esistere una qualche forma di esclusione reciproca per garantire l'accesso alla risorsa di un solo thread alla volta. Se l'esclusione reciproca viene eseguita in modo non corretto, è possibile creare un *deadlock* condizione in cui è possibile eseguire alcun thread. I deadlock possono rappresentare un problema particolarmente difficile da risolvere con il debug.

Visual Studio fornisce diversi strumenti per eseguire il debug di applicazioni multithreading.

- Per i thread sono i principali strumenti per il debug dei thread di **thread** (finestra), gli indicatori dei thread nelle finestre di origine, **stack in parallelo** finestra **espressioni di controllo parallelo** finestra e il **posizione di Debug** barra degli strumenti. Per apprendere la **thread** finestra e **posizione di Debug** sulla barra degli strumenti, vedere [procedura dettagliata: eseguire il Debug utilizzando la finestra thread](../debugger/how-to-use-the-threads-window.md). Per informazioni su come utilizzare il **stack in parallelo** e **espressioni di controllo parallelo** windows, vedere [Introduzione al debug di un'applicazione multithreading](../debugger/get-started-debugging-multithreaded-apps.md). In entrambi gli argomenti viene illustrato come utilizzare gli indicatori dei thread.
  
- Per il codice che utilizza il [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) o [Runtime di concorrenza](/cpp/parallel/concrt/concurrency-runtime/), sono i principali strumenti per il debug di **stack in parallelo** finestra, il **Espressioni di controllo parallelo** finestra e **attività** finestra (la **attività** finestra supporta anche JavaScript). Per iniziare, vedere [procedura dettagliata: debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md) e [procedura dettagliata: debug di un'applicazione C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application). 

- Per il debug di thread nella GPU, lo strumento principale è il **thread GPU** finestra. Vedere [procedura: utilizzare la finestra thread GPU](../debugger/how-to-use-the-gpu-threads-window.md).  

- Per i processi, i principali strumenti sono il **Connetti a processo** nella finestra di dialogo di **processi** finestra e **posizione di Debug** barra degli strumenti.  
  
Visual Studio offre anche potenti punti di interruzione e punti di analisi che possono rivelarsi molto utili per il debug di applicazioni multithreading. È possibile utilizzare condizioni punto di interruzione e i filtri per posizionare i punti di interruzione su singoli thread. Vedere [utilizzando i punti di interruzione](../debugger/using-breakpoints.md). 
  
Il debug di un'applicazione multithreading dotata di un'interfaccia utente può essere particolarmente complesso. In tal caso, potrebbe essere necessario eseguire l'applicazione in un secondo computer e utilizzare il debug remoto. Per informazioni, vedere [il debug remoto](../debugger/remote-debugging.md).  
  
## <a name="in-this-section"></a>In questa sezione
 [Introduzione al debug di un'applicazione multithreading](../debugger/get-started-debugging-multithreaded-apps.md).  
 Presentazione guidata delle funzionalità, con particolare attenzione alle funzionalità di debug dei thread di **stack in parallelo** finestra e **espressioni di controllo parallelo** finestra.

 [Strumenti per il debug di thread e processi](../debugger/debug-threads-and-processes.md)  
 Elenca le funzionalità degli strumenti per il debug di thread e processi.  
  
 [Eseguire il debug di più processi](../debugger/debug-multiple-processes.md)  
 Spiega la procedura per eseguire il debug di più processi

 [Procedura dettagliata: Debug tramite la finestra thread](../debugger/how-to-use-the-threads-window.md).  
 Procedura dettagliata in cui viene illustrato come utilizzare il **thread** finestra e **posizione di Debug** barra degli strumenti. 

 [Procedura dettagliata: Debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Procedura dettagliata in cui viene illustrato come utilizzare il **stack in parallelo** e **attività** windows.  
  
 [Procedura: Passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Tre modi per passare il contesto di debug a un altro thread.  
  
 [Procedura: Impostare e rimuovere i flag dei thread](../debugger/how-to-flag-and-unflag-threads.md)  
 Aggiunta di contrassegni o flag ai thread a cui è opportuno prestare particolare attenzione durante il debug.    
  
 [Procedura: Eseguire il debug su un cluster ad alte prestazioni](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Tecniche per il debug di applicazioni in esecuzione su un cluster ad alte prestazioni.  

 [Suggerimenti per il debug dei thread in codice nativo](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Semplici tecniche utili per il debug di thread nativi. 

 [Procedura: Impostare il nome di un thread in codice nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Attribuzione di un nome da visualizzare nella **thread** finestra.  
  
 [Procedura: Impostare il nome di un thread in codice gestito](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Attribuzione di un nome da visualizzare nella **thread** finestra. 
  
## <a name="related-sections"></a>Sezioni correlate  
 [Uso di punti di interruzione](../debugger/using-breakpoints.md)

 - Utilizzare le condizioni di punto di interruzione o filtri quando si desidera eseguire il debug di un singolo thread.  
  
 - I punti di traccia consentono di tracciare l'esecuzione dei programmi senza interruzioni. Ciò può risultare utile nello studio di problemi quali i deadlock.  
  
 [Threading](/dotnet/standard/threading/index)  
 Informazioni sul threading ed esempio di codice nella programmazione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 [Multithreading nei componenti](http://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
 Utilizzo del multithreading nei componenti di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 [Supporto del multithreading per il codice precedente (Visual C++)](/cpp/parallel/multithreading/multithreading-support-for-older-code-visual-cpp)  
 Informazioni sul threading ed esempio di codice per programmatori C++ che utilizzano MFC.  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il debug di thread e processi](../debugger/debug-threads-and-processes.md)   
 [Debug remoto](../debugger/remote-debugging.md)