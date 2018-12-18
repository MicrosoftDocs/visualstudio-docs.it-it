---
title: VSPerfCmd | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance tools, VSPerfCmd tool
- command-line tools, VSPerfCmd tool
- command line, tools
- profiling tools,VSPerfCmd
- VSPerfCmd tool
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
caps.latest.revision: "49"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: af5636866e2d91cc5aac5c8054a92961aeb3d042
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="vsperfcmd"></a>VSPerfCmd
Lo strumento **VSPerfCmd.exe** viene usato per avviare e arrestare la raccolta di dati sulle prestazioni. Viene usata la sintassi seguente:  
  
```  
VSPerfCmd [/U] [/options]  
```  
  
 Le tabelle seguenti descrivono le opzioni dello strumento **VSPerfCmd.exe**.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|**U**|L'output di console reindirizzato viene scritto come Unicode. Deve essere la prima opzione specificata.|  
|[Start](../profiling/start.md) **:** `mode`|Avvia il servizio di profilatura nella modalità specificata.|  
|[Output](../profiling/output.md) **:** `filename`|Specifica il nome del file di output. Usare solo con **Start**.|  
|[CrossSession&#124;CS](../profiling/crosssession.md)|Abilita la profilatura tra sessioni di Windows. Usare solo con **Start**, **Attach** o **Launch**.|  
|[User](../profiling/user-vsperfcmd.md) **:**[`domain\`]`username`|Consente l'accesso al servizio profiler all'account specificato. Usare solo con **Start**.|  
|[WaitStart](../profiling/waitstart.md)[**:**`n`]|Attende l'inizializzazione del logger di raccolta dei dati. Se si specifica `n`, **VSPerfCmd** attende al massimo `n` secondi. Se non si specifica `n`, **VSPerfCmd** attenderà un tempo illimitato. Ciò semplifica l'uso di **VSPerfCmd** come parte di un processo batch.|  
|[Counter](../profiling/counter.md) **:** `cfg`|Quando viene usato il metodi di campionamento per la profilatura, specifica un contatore di CPU e il numero di eventi da usare come intervallo di campionamento. È possibile campionare solo un valore di contatore.<br /><br /> Quando viene usato il metodo di profilatura tramite strumentazione, specifica un contatore di CPU da raccogliere a ogni punto di strumentazione. Usare solo con **Start:**`Trace`, **Attach**o **Launch**.|  
|[QueryCounters](../profiling/querycounters.md)|Visualizza un elenco di contatori CPU validi per il computer corrente.|  
|[WinCounter](../profiling/wincounter.md) **:** *percorso*|Specifica un evento contatore delle prestazioni di Windows da includere con i dati contrassegnati di profilatura. Usare solo con **Start**.|  
|[AutoMark](../profiling/automark.md) **:** *n*|Specifica l'intervallo di tempo (in millisecondi) tra gli eventi di raccolta di dati dei contatori delle prestazioni di Windows. Usare con **WinCounter**.|  
|[Events](../profiling/events-vsperfcmd.md) **:** `option`|Controlla la raccolta degli eventi ETW (Event Tracing for Windows) specificati. I dati ETW vengono raccolti in un file con estensione itl diverso dal file di dati di profilatura (con estensione vsp).|  
|[Status](../profiling/status.md)|Visualizza lo stato del profiler, informazioni sui processi attualmente in corso di profilatura e gli account che dispongono dell'autorità per controllare il profiler.|  
|[Shutdown](../profiling/shutdown.md)[**:**`n`]|Chiude il file di dati di profilatura e disattiva il profiler.|  
|[GlobalOn](../profiling/globalon-and-globaloff.md)|Riprende la raccolta di dati dopo una chiamata a **VSPerfCmdGlobalOff**.|  
|[GlobalOff](../profiling/globalon-and-globaloff.md)|Arresta la raccolta di tutti i dati, ma non termina la sessione di profilatura.|  
|[ProcessOn](../profiling/processon-and-processoff.md) **:** `pid`|Riprende la raccolta di dati per il processo specificato dopo la sospensione della profilatura tramite una chiamata a **VSPerfCmdProcessOff**.|  
|[ProcessOff](../profiling/processon-and-processoff.md) **:** `pid`|Arresta la raccolta di dati per il processo specificato.|  
|[ThreadOn e ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Riprende la profilatura per il processo specificato dopo la sospensione della profilatura tramite una chiamata a **VSPerfCmdThreadOff**. Usare **ThreadOn** solo durante la profilatura con il metodo di strumentazione.|  
|[ThreadOn e ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Sospende la profilatura per il thread specificato. Usare **ThreadOff** solo durante la profilatura con il metodo di strumentazione.|  
|[Mark](../profiling/mark.md) **:** *NumContrassegno*[**,***TestoContrassegno***]**|Inserisce un contrassegno nel file dati di profilatura, con testo facoltativo.|  
  
## <a name="sampling-method-options"></a>Opzioni del metodo di campionamento  
 Le opzioni seguenti sono disponibili solo quando si usa il metodo di campionamento per la profilatura.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|[Launch](../profiling/launch.md) **:** *Eseguibile*|Avvia l'applicazione specificata e inizia la profilatura.|  
|[Args](../profiling/args.md) **:** *Argomenti*|Specifica gli argomenti della riga di comando da passare all'applicazione avviata.|  
|[Console](../profiling/console.md)|Avvia il comando specificato in una nuova finestra del prompt dei comandi.|  
|[Attach](../profiling/attach.md) **:** *PID*[**,***PID*]|Avvia la profilatura dei processi specificati. I processi possono essere identificati in base all'ID o al nome del processo.|  
|[Detach](../profiling/detach.md)[**:***PID*[,*PID*]]|Arresta la profilatura dei processi specificati. I processi possono essere identificati in base all'ID o al nome del processo. Se non viene specificato alcun processo, la profilatura viene interrotta per tutti i processi.|  
|[GC](../profiling/gc-vsperfcmd.md)[**:**{**Allocation**`&#124;`**Lifetime**}]|Raccoglie dati sull'allocazione di memoria .NET e sulla durata degli oggetti. Usare solo con l'opzione **VSPerfCmdLaunch**.|  
  
### <a name="sampling-interval-options"></a>Opzioni per l'intervallo di campionamento  
 Le opzioni seguenti specificano il tipo e la durata degli intervalli di campionamento. L'opzione predefinita è **Timer**. È possibile specificare anche un contatore CPU come intervallo tramite l'opzione **Counter**. Queste opzioni possono essere specificate solo con **Launch** o con la prima operazione **Attach** di una sessione di profilatura.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|[PF](../profiling/pf.md)[**:***n*]|Esegue il campionamento ogni n errori di pagina (valore predefinito=10).|  
|[Sys](../profiling/sys-vsperfcmd.md)[**:***n*]|Esegue il campionamento ogni n chiamate di sistema (valore predefinito=10).|  
|[Timer](../profiling/timer.md)[**:***n*]|Esegue il campionamento ogni n cicli (valore predefinito=10000000).|  
  
## <a name="service-component-and-kernel-mode-device-options"></a>Opzioni per il componente del servizio e il dispositivo in modalità kernel  
 Le opzioni di amministrazione seguenti supportano la profilatura di componenti del servizio o dei driver di dispositivo in modalità kernel. Le opzioni di amministrazione impostano le autorizzazioni di profilatura e controllano il servizio o il driver di dispositivo profilato.  
  
 Le opzioni di amministrazione devono essere eseguite in un prompt dei comandi in esecuzione con credenziali amministrative.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|**Admin:Security** \<**ALLOW&#124;DENY**> *Diritto*[ *Diritto*] \<*Utente*&#124;*Gruppo*>|Consente o nega l'accesso ai servizi di profilatura all'utente o al gruppo specificato.<br /><br /> `Right` può essere:<br /><br /> CrossSession: consente all'utente l'accesso al servizio per la profilatura tra sessioni.<br /><br /> SampleProfiling: consente all'utente di accedere al driver per abilitare la profilatura di campionamento. Usato anche per accedere alle informazioni di transizione del kernel durante la profilatura di traccia.<br /><br /> FullAccess: consente all'utente sia l'accesso CrossSession che l'accesso SampleProfiling.|  
|**Admin:Security, List**|Elenca lo stato corrente dei servizi di profilatura e le autorizzazioni utente.|  
|**Admin:** \<*Servizio*&#124;*Driver*>\<**START**&#124;**STOP**&#124;**INSTALL**&#124;**UNINSTALL**>|Avvia, arresta, installa o disinstalla il componente del servizio di profilatura (Servizio) o il driver del dispositivo in modalità kernel (Driver).|  
|**Admin:** \<*Servizio*&#124;*Driver*>**AutoStart**\<**ON**&#124;**OFF**>|Abilita o disabilita l'avvio automatico del servizio di profilatura (Servizio) o del driver del dispositivo in modalità kernel (Driver) dopo un riavvio.|  
  
## <a name="vsperfcmd-driver"></a>VSPerfCmd /Driver  
 L'opzione **VSPerfCmd /Driver** è obsoleta. Usare le opzioni **VsPerfCmdAdmin** per questa funzionalità.  
  
## <a name="see-also"></a>Vedere anche  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfReport](../profiling/vsperfreport.md)