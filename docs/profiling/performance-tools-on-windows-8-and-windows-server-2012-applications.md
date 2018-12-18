---
title: Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012 | Microsoft Docs
ms.custom: 
ms.date: 06/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a704215d-d252-4087-921b-ac81ebe2a9c9
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b82860f4bdbf206441591703137f15decb294269
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012
Le funzionalità di protezione avanzata introdotte a partire da Windows 8 e Windows Server 2012 hanno richiesto modifiche significative delle modalità di raccolta dei dati in queste piattaforme con gli strumenti per le prestazioni di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Questo argomento descrive le modifiche agli strumenti per le prestazioni introdotte a partire dalle piattaforme Windows 8 e Windows Server 2012.
  
> [!NOTE]
>  Gli strumenti per le prestazioni per le altre versioni di Windows supportate (Windows 7, Windows Server 2008 R2) sono rimasti invariati.
  
##  <a name="BKMK_In_this_topic"></a> In questo argomento  
 [Raccolta di dati nelle app UWP dall'IDE di Visual Studio](#BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE)  
  
 [Raccolta di dati nelle app in esecuzione sul desktop di Windows 8 o in Windows Server 2012 dall'IDE di Visual Studio](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE)  
  
-   [Raccolta di dati nelle app in esecuzione sul desktop di Windows 8 o in Windows Server 2012 mediante campionamento dall'IDE di Visual Studio](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE)  
  
 [Profilatura dalla riga di comando](#BKMK_Profiling_from_the_command_line)  
  
 [Raccolta di dati di interazione tra livelli (TIP)](#BKMK_Collecting_tier_interaction__TIP__data)  
  
##  <a name="BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE"></a> Raccolta di dati nelle app UWP dall'IDE di Visual Studio  
 Quando si profila un'app UWP scritta in JavaScript e HTML 5, si raccolgono dati di strumentazione per il codice JavaScript. Quando si profila un'app UWP o un componente scritto in Visual C++, Visual C# o Visual Basic, si raccolgono dati di campionamento per il codice nativo e il codice gestito. È possibile profilare l'applicazione localmente o in un computer remoto.  
  
 Le funzionalità e opzioni di profilatura seguenti non sono supportate per la profilatura di app UWP:  
  
-   Profilatura di applicazioni JavaScript usando il metodo del campionamento.  
  
-   Profilatura di codice gestito e codice nativo usando il metodo di strumentazione.  
  
-   Profilatura della concorrenza  
  
-   Profilatura della memoria .NET  
  
-   Profilatura di interazione tra livelli (TIP)  
  
-   Opzioni di campionamento, come l'impostazione dell'evento e dell'intervallo di campionamento o la raccolta di dati aggiuntivi del contatore delle prestazioni.  
  
-   Opzioni di strumentazione, ad esempio la raccolta dei dati dei contatori Windows e delle prestazioni o la specifica di opzioni della riga di comando aggiuntive.  
  
 Per altre informazioni sulla profilatura delle app UWP, vedere gli argomenti seguenti:  
  
 [Eseguire app UWP nel computer locale](../debugger/run-windows-store-apps-on-the-local-machine.md)  
  
 [Eseguire app UWP in un computer remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md)  
  
 [Profiling Tools](profiling-tools.md) (Strumenti di profilatura)  
  
-   [Memoria JavaScript](../profiling/javascript-memory.md)
  
-   [Profilare codice Visual C++, Visual C# e Visual Basic nelle app UWP in un computer locale](http://msdn.microsoft.com/en-us/2d0c939e-0bac-48c5-b727-46f6c6113060)  
  
-   [Profilare codice Visual C++, Visual C# e Visual Basic nelle app UWP in un dispositivo remoto](http://msdn.microsoft.com/en-us/b932a2be-11b0-40fd-b996-75c6b6a79d22)  
  
-   [Analizzare i dati relativi alle prestazioni per il codice Visual C++, Visual C# e Visual Basic nelle app UWP](http://msdn.microsoft.com/en-us/5de4a413-d924-425f-afc4-e1ecfb0fca18)  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE"></a> Raccolta di dati nelle app in esecuzione sul desktop di Windows 8 o in Windows Server 2012 dall'IDE di Visual Studio  
 La profilatura mediante il metodo di strumentazione è rimasta invariata per Windows 8.  
  
 La profilatura di interazione tra livelli (TIP) non è supportata usando il metodo di campionamento.  
  
###  <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE"></a> Raccolta di dati nelle app in esecuzione sul desktop di Windows 8 o in Windows Server 2012 mediante campionamento dall'IDE di Visual Studio  
 Queste funzionalità e opzioni di profilatura non sono supportate quando si profilano applicazioni di Windows 8 Desktop o di Windows Server 2012 usando il metodo di campionamento:
  
-   Profilatura di interazione tra livelli (TIP). La raccolta di dati TIP è supportata mediante la strumentazione.
  
-   Opzioni di campionamento, come l'impostazione dell'evento e dell'intervallo di campionamento o la raccolta di dati aggiuntivi del contatore delle prestazioni.  
  
##  <a name="BKMK_Profiling_from_the_command_line"></a> Profilatura dalla riga di comando  
 Per raccogliere dati di profilatura nei dispositivi Windows 8 e Windows Server 2012, inclusi i dispositivi privi di installazione di Visual Studio, si usano due strumenti da riga di comando:  
  
|Nome dello strumento|Descrizione|  
|---------------|-----------------|  
|[VSPerf](../profiling/vsperf.md)|Raccoglie i dati di profilatura dalle app UWP e raccoglie campioni di dati di profilatura dalle applicazioni Windows 8 Desktop e Windows Server 2012.|  
|[VSPerfCmd](../profiling/vsperfcmd.md)|Raccoglie i dati di profilatura della strumentazione, della concorrenza e dell'interazione tra livelli dalle applicazioni in esecuzione su Windows 8 Desktop o Windows Server 2012. Raccoglie tutti i tipi di dati di profilatura dalle versioni precedenti di Windows.|  
  
 Entrambi gli strumenti vengono installati con Visual Studio per l'uso nel computer locale.  
  
 Per profilare le applicazioni sui dispositivi in cui non è installato Visual Studio, eseguire una delle operazioni seguenti:  
  
-   Scaricare gli strumenti come parte di Remote Tools per Visual Studio dal [sito Web MSDN](http://go.microsoft.com/fwlink/?LinkID=219549).  
  
-   Copiare ed eseguire il programma di installazione dei profiler autonomi dal computer con Visual Studio. I programmi di installazione si trovano nella cartella *%VSInstallDir%* **\Team Tools\Performance Tools\Setups** . Scegliere il programma di installazione per il sistema operativo (x86/x64) del computer remoto.  
  
> [!NOTE]
>  Per raccogliere i dati di profilatura TIP, è necessario installare il profiler autonomo dal computer con Visual Studio nel computer remoto.  
  
 Queste funzionalità e opzioni di profilatura non sono supportate quando si profilano applicazioni Windows 8 o applicazioni Windows Server 2012 dalla riga di comando:  
  
-   Raccolta di dati da app Web di Windows 8 e Windows Server 2012 usando la modalità di campionamento con [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md).  
  
-   Raccolta di dati di campionamento tramite VsPerfCmd.exe.  
  
-   Opzioni di campionamento, come l'impostazione dell'evento e dell'intervallo di campionamento o la raccolta di dati aggiuntivi del contatore delle prestazioni.  
  
##  <a name="BKMK_Collecting_tier_interaction__TIP__data"></a> Raccolta di dati di interazione tra livelli (TIP)  
 La profilatura delle interazioni tra livelli offre informazioni aggiuntive sui tempi di esecuzione delle funzioni di applicazioni multilivello che comunicano con i database tramite i servizi ADO.NET. I dati vengono raccolti solo per le chiamate di funzione sincrone.  
  
 **Versioni di Visual Studio**  
  
 I dati di profilatura dell'interazione tra livelli possono essere raccolti usando [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]o [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)], ma possono essere visualizzati solo in [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] e [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
 **Windows 8 e Windows Server 2012**  
  
1.  Per raccogliere dati di interazione tra livelli dalle app in esecuzione su Windows 8 Desktop o Windows Server 2012, è necessario usare il metodo di strumentazione.  
  
2.  Non è possibile raccogliere dati di interazione tra livelli per le app UWP.  
  
3.  È possibile includere i dati di interazione tra livelli in tutti i metodi di profilatura su un'altra versione di Windows supportata.  
  
 **Creazione guidata sessione di prestazioni e Esplora prestazioni**  
  
 È necessario aggiungere l'opzione di raccolta dati di interazione tra livelli a una profilatura eseguita da Esplora prestazioni. È inoltre necessario aggiungere il progetto, il file eseguibile o il sito Web al nodo di destinazione di Esplora prestazioni. Vedere [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md).  
  
 **Raccolta di dati TIP in un computer remoto**  
  
 Per raccogliere dati di interazione tra livelli in un computer remoto, è necessario copiare il file **vs_profiler_***\<Piattaforma>***_***\<Linguaggio>***.exe** dalla cartella *%VSInstallDir%***\Team Tools\Performance Tools\Setups** di un computer Visual Studio nel computer remoto e installarlo. Non è possibile usare gli strumenti di profilatura nel pacchetto di download di [debug remoto](../debugger/remote-debugging.md).  
  
 È possibile usare [VSPerfCmd](../profiling/vsperfcmd.md) o [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) per raccogliere i dati di profilatura.  
  
 **Report TIP**  
  
 I dati di interazione tra livelli possono essere visualizzati solo nell'IDE di [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] o [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] . I report sull'interazione tra livelli basati su file tramite [VSPerfReport](../profiling/vsperfreport.md) non sono disponibili.  
  
## <a name="see-also"></a>Vedere anche  
 [Esplora prestazioni](../profiling/performance-explorer.md)   
 [Configuring Performance Sessions](../profiling/configuring-performance-sessions.md)  (Configurazione di sessioni di prestazioni)  
 [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)