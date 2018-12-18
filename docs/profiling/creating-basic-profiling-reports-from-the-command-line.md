---
title: Creazione di report di profilatura di base tramite la riga di comando | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 502fe56f04fe933e51e9afa5376a35a53445c099
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="creating-basic-profiling-reports-from-the-command-line"></a>Creazione di rapporti di profilatura di base tramite la riga di comando
Questo argomento descrive i comandi VSPerfReport di base che generano report con estensione csv da file di dati di profilatura con estensione vsp o vsps. Per la descrizione di tutte le opzioni del report, vedere [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="report-commands"></a>Comandi del report  
 Usare uno dei comandi seguenti per creare un report per il file di dati di profilatura specificato.  
  
 **VSPerfReport** `VSPFile` **/Summary:All**  
 Genera tutti i report disponibili per il file con estensione vsp o vsps.  
  
 **VSPerfReport** `VSPFile` **/Summary:**`ReportType`[,`ReportType`...]  
 Genera i tipi di report specificati.  
  
 **VSPerfReport** `VSPFile` **/CallTrace**  
 Genera un report che elenca ogni evento di raccolta dati. Solo strumentazione.  
  
## <a name="summary-report-type-parameters"></a>Parametri di riepilogo per tipo di report  
 La tabella seguente descrive i report generati a seconda dell'opzione di tipo di report specificata Le colonne di un report variano a seconda del metodo di profilatura usato per raccogliere i dati.  
  
|Parametro di riepilogo|Descrizione report|Riferimenti per il report|  
|-----------------------|------------------------|----------------------|  
|**CallerCallee**|Rappresenta le relazioni padre-figlio tra le funzioni.|-   [Dati di campionamento](../profiling/caller-callee-view-sampling-data.md)<br />-   [Dati di strumentazione](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Dati di strumentazione di memoria .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Dati su conflitti](../profiling/caller-callee-view-contention-data.md)|  
|**Function**|Elenca i dati di profilatura per funzione.|-   [Dati di campionamento](../profiling/functions-view-sampling-data.md)<br />-   [Dati di strumentazione](../profiling/functions-view-instrumentation-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Dati di strumentazione di memoria .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Dati su conflitti](../profiling/functions-view-contention-data.md)|  
|**CallTree**|Rappresenta i percorsi di esecuzione e i dati di profilatura delle funzioni nell'esecuzione della profilatura.|-   [Dati di strumentazione](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Dati di campionamento](../profiling/call-tree-view-sampling-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Dati di strumentazione di memoria .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Dati su conflitti](../profiling/call-tree-view-contention-data.md)|  
|**Contatore**|Elenca i contrassegni di profilo e valori del contatore delle prestazioni di Windows raccolti durante l'esecuzione della profilatura.|-   [Visualizzazione Contrassegni](../profiling/marks-view.md)|  
|**Ip**|Elenca i dati di profilatura per istruzione.|-   [Dati di campionamento](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Dati su conflitti](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**Life**|Visualizza la durata degli oggetti allocati.|-   [Visualizzazione Durata oggetti](../profiling/object-lifetime-view.md)|  
|**Line**|Elenca i dati di profilatura per riga di codice sorgente.|-   [Dati di campionamento](../profiling/lines-view-sampling-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Dati su conflitti](../profiling/lines-view-contention-data.md)|  
|**Header**|Informazioni di intestazione per il file di dati di profilatura.|Specifico per il file.|  
|**Contrassegno**|Contrassegni di profilatura raccolti nell'esecuzione della profilatura.|-   [Visualizzazione Contrassegni](../profiling/marks-view.md)|  
|**Modulo**|Elenca i dati di profilatura per i moduli.|-   [Dati di campionamento](../profiling/modules-view-sampling-data.md)<br />-   [Dati di strumentazione](../profiling/modules-view-instrumentation-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Dati di strumentazione di memoria .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Dati su conflitti](../profiling/modules-view-contention-data.md)|  
|**Processo**|Elenca i dati di profilatura per i processi.|-   [Visualizzazione Processo](../profiling/process-view.md)<br />-   [Dati su conflitti](../profiling/process-view-contention-data.md)|  
|**Thread**|Elenca i dati di profilatura per i thread.|-   [Visualizzazione Processo](../profiling/process-view.md)|  
|**Type**|Elenca i dati di profilatura dell'allocazione in base al tipo.|-   [Visualizzazione Allocazioni](../profiling/dotnet-memory-allocations-view.md)|  
|**Contention**|Conflitti tra risorse.|-   [Conflitti tra risorse](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|Elenca i problemi relativi alle regole di prestazioni.|Elenca il valore CheckId, la descrizione e il percorso del codice sorgente del problema relativo alla regola.|  
|**ETW**|Elenca gli eventi ETW (Event Tracing for Windows) raccolti durante l'esecuzione della profilatura.|-   [Rapporto ETW](../profiling/event-tracing-for-windows-etw-report.md)|