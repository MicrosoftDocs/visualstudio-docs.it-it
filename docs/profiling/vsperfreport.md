---
title: VSPerfReport | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command-line tools, VSPerfReporttool
- performance tools, VSPerfReport tool
- profiling tools,VSPerfReport
- VSPerfReport tool
- command line, tools
- instrumentation, VSPerfReporttool
ms.assetid: dbfd8d91-4430-4b82-81b9-97ac61412a6c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c7460b287b22ead961a5701fe4f8fa8bb22fc2d2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="vsperfreport"></a>VSPerfReport
Lo strumento da riga di comando VSPerfReport viene usato per creare report usando i file di dati di profilatura degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Il formato predefinito per i report è un file CSV.  
  
 VSPerfReport usa la sintassi seguente:  
  
```  
VSPerfReport [/U] vspfilename [/options]  
```  
  
 Si noti che `filename` deve essere un file con estensione vsp o vsps valido.  
  
 Lo strumento da riga di comando VSPerfReport viene inoltre usato per confrontare i file con estensione vsp o vsps. Per generare un report delle differenze ("diff"), usare la sintassi seguente:  
  
```  
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]  
```  
  
 `vspfilename1 and vspfilename2` devono essere file con estensione vsp o vsps validi.  
  
## <a name="symbol-files"></a>File di simboli  
 Per visualizzare informazioni sui simboli quali i nomi delle funzioni e i numeri di riga, VSPerfReport richiede l'accesso ai file di simboli (con estensione PDB) dei componenti profilati e ai file dei simboli di Windows. Per altre informazioni, vedere [Procedura: Specificare percorsi dei file di simboli tramite la riga di comando](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
  
## <a name="general-report-options"></a>Opzioni generali per i report  
 La tabella seguente descritte le opzioni di formattazione dei report generali e le opzioni per selezionare i dati da includere nel report.  
  
|Opzioni|Descrizione|  
|-------------|-----------------|  
|**U**|L'output del report e l'output di console reindirizzato vengono scritti in formato Unicode. Deve essere la prima opzione specificata.|  
|**Summary:**[*tipi*]|Crea uno o più tipi di report.<br /><br /> -   `All` - Vengono generati tutti i tipi di report.<br />-   `CallerCallee` - Relazioni padre-figlio tra le funzioni.<br />-   `Function` - Funzioni chiamate.<br />-   `CallTree` - Gerarchia delle funzioni chiamate.<br />-   `Counter` - Tutti i contrassegni insieme ai valori dei contatori delle prestazioni di Windows.<br />-   `Ip` - Istruzioni profilate.<br />-   `Life` - Durata degli oggetti allocati (disponibile quando sono stati raccolti dati sulle allocazioni).<br />-   `Line` - Dati di profilatura delle righe di codice sorgente.<br />-   `Header` - Il report contiene informazioni sull'intestazione di file.<br />-   `Mark` - Tutti i contrassegni.<br />-   `Module` - Moduli profilati.<br />-   `Process` - Processi profilati.<br />-   `Thread` - Thread profilati.<br />-   `Type` -Tipo allocati.<br />-   `Contention` - Conflitti di risorse.<br />-   `RuleWarnings` - Problemi relativi alle regole di prestazioni.<br />-   `ETW` - Tutti gli eventi ETW (Event Tracing for Windows) raccolti durante l'esecuzione della profilatura. Il file di dati con estensione etl deve essere nella posizione originale o nella directory contenente il file con estensione vsp o vsps.|  
|**Xml**|Il report viene generato in formato XML.|  
|**CallTrace**|Crea un elenco di ingressi e uscite da funzioni, eventi ETW e contrassegni.|  
|**ClearPackedSymbols**|Rimuove i simboli precedentemente incorporati da un file di dati del profiler. Eseguire questo comando prima di eseguire PackSymbols una seconda volta.|  
|**SymbolPath:** `path`|Specifica uno o più percorsi di ricerca o server di simboli che contengono i simboli per il file di dati del profiler.|  
|**DebugSymPath**|Elenca i percorsi in cui vengono cercati i simboli e se vengono trovati. Questa opzione è utile per risolvere i problemi di risoluzione dei simboli.|  
|**PackSymbols**|Salva i simboli nel file di dati di profilatura (con estensione vsp) in modo che i file di simboli (con estensione pdb) non siano necessari per l'analisi.|  
|**Output:** *percorso*&#124;*nomefile*|Specifica un percorso alternativo per i file dei report generati. Per impostazione predefinita, i report vengono creati nella directory corrente.|  
|**SummaryFile**|Analizza e salva le informazioni analizzate in un file di riepilogo vsps.|  
|**PrintMarks**|Mostra il nome e il timestamp di tutti i contrassegni nel file di report specificato.|  
|**?**|Visualizza informazioni sull'utilizzo.|  
|**NoLogo**|Nasconde le informazioni sulla versione quando il report è in esecuzione.|  
|**UserRulesDirectory**|Specifica la directory che contiene le regole per le prestazioni definite dall'utente [non ancora implementate].|  
  
## <a name="filter-options"></a>Opzioni di filtro  
 La tabella seguente descrive le opzioni disponibili per filtrare i dati disponibili.  
  
|Opzioni|Descrizione|  
|-------------|-----------------|  
|**JustMyCode**[**:**[`caller`][,`callee`]]|Mostra solo le chiamate di funzioni dell'applicazione dell'utente. Le chiamate di sistema vengono nascoste.<br /><br /> - Nessun parametro: nasconde tutte le funzioni di sistema.<br />-   `caller` - Mostra un livello di funzioni di sistema che chiamano funzioni dell'applicazione.<br />-   `callee` - Mostra un livello di funzioni di sistema che vengono chiamate da funzioni dell'applicazione dell'utente.|  
|**StartTime:**[*valore*]|Mostra solo i dati raccolti dopo il valore (in millisecondi).|  
|**EndTime:**[*valore*]|Mostra solo i dati raccolti prima del valore (in millisecondi).|  
|**FilterFile:** `VSPFFile`|Specifica il percorso di un file di filtro generato dalla finestra Visual Studio Performance Report.|  
|**MsFilter:**[*orainizio,durata*]|Mostra solo i dati da `starttime` fino alla durata `duration` (in millisecondi).|  
|**Process:**[*pid*]|Mostra solo i dati del processo specificato.|  
|**Thread:**[*idthread*]|Mostra solo i dati del thread specificato.|  
|**Thread:**[*idthread,idprocesso*]|Mostra solo i dati del thread specificato associato al processo specificato.|  
  
## <a name="difference-report-options"></a>Opzioni per i report sulle differenze  
 La tabella seguente descrive le opzioni per confrontare i file di report.  
  
|Opzioni|Descrizione|  
|-------------|-----------------|  
|**Diff**  `vspfile1 vspfile2`|Confrontare due file di report (con estensione vsp o vsps). Le opzioni Summary verranno ignorate quando si usa l'opzione Diff.|  
|**Diff:**[*valore*]|Sotto questo valore di soglia la differenza tra due valori verrà ignorata. Inoltre, i nuovi dati con valori al di sotto della soglia non verranno visualizzati.|  
|**DiffTable:**[*nometabella*]|Usare questa tabella specifica per confrontare i file. Per impostazione predefinita, viene usata la tabella delle funzioni.|  
|**DiffColumn:**[*nomecolonna*]|Usare questa colonna specifica per confrontare i file. Per impostazione predefinita, viene usata la colonna percentuale campioni esclusivi.|  
|**QueryDiffTables**|Elenco delle tabelle e delle colonne valide per i due file di report specificati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Performance Report Views](../profiling/performance-report-views.md)(Visualizzazioni dei rapporti di prestazioni)