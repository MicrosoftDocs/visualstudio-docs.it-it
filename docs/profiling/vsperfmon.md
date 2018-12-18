---
title: VSPerfMon | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPerfMon tool
- command line, tools
- command-line tools, VSPerfMon tool
- data [Visual Studio ALM], VSPerfMon tool
- performance data, VSPerfMon tool
- performance tools, VSPerfMon tool
- profilng tools,VSPerfCmd
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8700cf317e60f8f842186e04cc36f4037172aa2d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="vsperfmon"></a>VSPerfMon
È possibile usare lo strumento VSPerfMon per raccogliere dati sulle prestazioni per un'applicazione. In genere, questo strumento viene avviato da VSPerfCmd.exe. VSPerfMon visualizza informazioni aggiuntive sul collegamento o lo scollegamento di processi che non sono disponibili tramite lo strumento VSPerfCmd. Per visualizzare queste informazioni, avviare VSPerfMon in una finestra separata. Per richiamare VSPerfMon, usare la sintassi seguente:  
  
```  
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]  
```  
  
 Nella tabella seguente vengono descritte le opzioni dello strumento VSPerfMon:  
  
|Opzioni|Descrizione|  
|-------------|-----------------|  
|**U**|L'output di console reindirizzato viene scritto come Unicode.  Deve essere la prima opzione specificata.|  
|**OUTPUT:** `<` *nome file* `>`|Reindirizza l'output nel nome file specificato.|  
|**TRACE**|Avvia il monitoraggio delle prestazioni per la profilatura instrumentata.|  
|**SAMPLE**|Avvia il monitoraggio delle prestazioni per la profilatura tramite campionamento.|  
|**COVERAGE**|Avvia il monitoraggio delle prestazioni per la raccolta dei dati di code coverage.|  
|**CONCURRENCY**|Avvia il monitoraggio delle prestazioni per la profilatura dei conflitti di risorse.|  
|**USER:** `[` *dominio* `\]` *nomeutente*|Consente l'accesso client al monitoraggio delle prestazioni dall'account specificato.|  
|**CROSSSESSION**|Abilita la profilatura tra sessioni.|  
|**COUNTER** `:cfg`|Quando viene usato il metodo di profilatura tramite strumentazione (TRACE), specifica un contatore CPU da raccogliere a ogni punto di strumentazione. È possibile raccogliere i dati di più contatori specificando più opzioni Counter.<br /><br /> Usare la seguente sintassi per specificare i dati del contatore (*cfg*):<br /><br /> **CounterName** [**,Reload**[,**FriendlyName**]]<br /><br /> -   **CounterName** è il nome di un contatore restituito dal comando VSPerfCmd /QueryCounters.<br />-   **Reload** è l'intervallo di campionamento degli eventi del contatore. Non usare *Reload* con il metodo di strumentazione.<br />Quando specificato, **FriendlyName** sostituisce **CounterName** nei nomi di colonna dei report degli strumenti di profilatura.|  
|**WINCOUNTER** `:path`|Specifica un contatore delle prestazioni di Windows da includere con i dati contrassegnati. `path` è una stringa del contatore delle prestazioni di Windows nel formato del percorso del contatore PDH. Ad esempio:<br /><br /> \Processor(0)\\% Processor Time<br /><br /> \System\Context Switches/sec|  
|**AUTOMARK** `:n`|Specifica l'intervallo di tempo (in millisecondi) tra i contrassegni automatici quando si usa /WINCOUNTER. Arrotondato per eccesso al più vicino multiplo di 500 ms.<br /><br /> Usare 0 per disabilitare i contrassegni automatici. Se non si specifica alcun valore, l'impostazione predefinita è 500 ms.|  
  
## <a name="see-also"></a>Vedere anche  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Performance Report Views](../profiling/performance-report-views.md)(Visualizzazioni dei rapporti di prestazioni)