---
title: Counter | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eaebb7afc76066e9c1c53b0649c70dd346ddb72f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="counter"></a>Counter
L'opzione **Counter** raccoglie i dati dai contatori delle prestazioni del processore (hardware).  
  
-   Quando si usa il metodo di profilatura basato sul campionamento, l'opzione **Counter** consente di specificare il contatore delle prestazioni del chip e il numero di eventi del contatore da usare come intervallo di campionamento. Quando si usa il campionamento, è possibile specificare un solo contatore.  
  
-   Quando si usa il metodo di profilatura basato sulla strumentazione, il numero di eventi del contatore che si verificano nell'intervallo tra l'evento di raccolta corrente e quello precedente vengono elencati come campi separati nei report del profiler. Quando si usa la strumentazione, è possibile specificare più opzioni **Counter**.  
  
 Ogni tipo di processore dispone del proprio set di contatori delle prestazioni dell'hardware. Il profiler definisce un set di contatori delle prestazioni generici comuni a quasi tutti i processori. Per elencare nel computer i contatori generici e quelli specifici del processore, usare il comando **QueryCounters** di VSPerfCmd.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]  
```  
  
```  
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]  
```  
  
#### <a name="parameters"></a>Parametri  
 `Name`  
 Nome del contatore. Usare l'opzione **/QueryCounters** di VSPerfCmd.exe per elencare i nomi dei contatori disponibili nel computer.  
  
 `Reload`  
 Numero di eventi dei contatori nell'intervallo di campionamento. Non usare con il metodo basato sulla strumentazione.  
  
 `FriendlyName`  
 (Facoltativo) Stringa da usare al posto di `Name` nelle intestazioni di colonna dei report e delle visualizzazioni del profiler.  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 L'opzione Counter può essere usata solo con una delle opzioni seguenti:  
  
 **Start:** `Trace`  
 Inizializza il profiler per l'uso del metodo basato sulla strumentazione.  
  
 **Launch:** `AppName`  
 Avvia l'applicazione specificata e il profiler. Il profiler deve essere inizializzato per l'uso del metodo basato sul campionamento.  
  
 **Attach:** `PID`  
 Avvia il profiler e lo connette al processo specificato dall'ID processo. Il profiler deve essere inizializzato per l'uso del metodo basato sul campionamento.  
  
## <a name="example"></a>Esempio  
 Nell'esempio del metodo basato sul campionamento viene illustrato come campionare un'applicazione ogni 1000 occorrenze del contatore del profiler generico NonHaltedCycles.  
  
 Nell'esempio del metodo basato sulla strumentazione viene illustrato come inizializzare il profiler per la raccolta di eventi del contatore L2InstructionFetches. Il nome del contatore L2InstructionFetches è specifico del processore.  
  
```  
; Sample Method Example  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"  
  
;INSTRUMENTATION METHOD EXAMPLE  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)