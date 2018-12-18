---
title: 'DA0503: Working set medio in byte del processo sottoposto a profilatura | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.503
- vs.performance.DA0503
- vs.performance.rules.DA0503
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3c5333a6ce2ddfa5e3d627030e71466a8c9ae0c1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="da0503-average-working-set-in-bytes-for-the-process-being-profiled"></a>DA0503: Working set medio in byte del processo sottoposto a profilatura
|||  
|-|-|  
|ID regola|DA0503|  
|Category|Monitoraggio risorse|  
|Metodo di profilatura|Tutti|  
|Messaggio|Dati raccolti a solo scopo informativo. Il contatore working set di processo misura l'utilizzo della memoria fisica da parte del processo sottoposto a profilatura. Il valore restituito corrisponde al valore medio rilevato per tutti gli intervalli di misurazione.|  
|Tipo regola|Informazioni|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questo messaggio indica la quantità media di memoria fisica, in byte, usata attualmente dal processo espressa in byte (il working set). Il working set del processo rappresenta pagine dallo spazio degli indirizzi del processo che attualmente risiedono nella memoria fisica.  
  
 Il valore indicato include pagine residenti da segmenti di memoria condivisa a cui ha fatto riferimento il processo. Le DLL condivise a cui fa riferimento il processo sono incluse nei segmenti di memoria condivisa contati. Il valore del working set del processo può essere maggiore della quantità di memoria virtuale allocata dal processo a causa dei segmenti di memoria condivisa.  
  
 Il valore indicato è il valore medio fra tutti gli intervalli di misurazione nei quali il processo sottoposto a profilatura era attivo.  
  
 La dimensione del working set del processo riflette la quantità di memoria virtuale attivamente usata dal processo stesso. Dipende anche dalla quantità di memoria fisica (o RAM) disponibile per eseguire l'applicazione e dai conflitti tra altri processi in esecuzione per tale memoria fisica. Se la memoria fisica è vincolata, il valore del working set del processo è soggetto a variazioni significative in quanto il sistema operativo tenta di bilanciare l'utilizzo della memoria tra i processi attivi rimuovendo periodicamente le pagine quasi inattive dai working set del processo.  
  
 Per altre informazioni sui working set di processo, vedere [Working Set](http://go.microsoft.com/fwlink/?LinkId=177830) nella documentazione relativa alla gestione della memoria di Windows in MSDN.  
  
## <a name="how-to-use-rule-data"></a>Come usare i dati della regola  
 Usare il valore della regola per confrontare le prestazioni di versioni o build diverse del programma o per ottenere informazioni sulle prestazioni dell'applicazione in scenari di profilatura diversi.  
  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla [visualizzazione Contrassegni](../profiling/marks-view.md) dei dati di profilatura. Individuare le colonne **Processo\Working Set** e **Memoria\Pagine/sec**. Confrontare le due colonne e determinare se sono presenti fasi specifiche di esecuzione del programma che sembrano associate ad attività I/O di paging aumentate.