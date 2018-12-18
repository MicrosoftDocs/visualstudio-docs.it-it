---
title: 'DA0504: Working set massimo in byte del processo sottoposto a profilatura | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.DA0504
- vs.performance.504
- vs.performance.rules.DA0504
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 74912daf23e4b62778a81cd94938836ec122fba0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504: Working set massimo in byte del processo sottoposto a profilatura
|||  
|-|-|  
|ID regola|DA0504|  
|Category|Gestione delle risorse|  
|Metodo di profilatura|Tutti|  
|Messaggio|Dati raccolti a solo scopo informativo. Il contatore working set di processo misura l'utilizzo della memoria fisica da parte del processo sottoposto a profilatura. Il valore restituito corrisponde al valore massimo osservato per tutti gli intervalli di misurazione.|  
|Tipo regola|Informazioni|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questo messaggio indica la quantità massima di memoria fisica, in byte, usata attualmente dal processo. Il working set del processo rappresenta pagine dallo spazio degli indirizzi del processo che attualmente risiedono nella memoria fisica. Questa regola indica il valore massimo per il working set del processo mentre la profilatura era attiva.  
  
 Il valore indicato include pagine residenti da segmenti di memoria condivisa a cui ha fatto riferimento il processo. Le DLL condivise a cui fa riferimento il processo sono incluse nei segmenti di memoria condivisa contati. Il valore del working set del processo può essere maggiore della quantità di memoria virtuale allocata dal processo a causa dei segmenti di memoria condivisa.  
  
 La dimensione del working set del processo riflette la quantità di memoria virtuale attivamente usata dal processo stesso. Dipende anche dalla quantità di memoria fisica (o RAM) disponibile per eseguire l'applicazione e dai conflitti tra altri processi in esecuzione per tale memoria fisica. Per altre informazioni sui working set di processo, vedere [Working Set](http://go.microsoft.com/fwlink/?LinkId=177830) nella documentazione relativa alla gestione della memoria di Windows in MSDN.  
  
## <a name="how-to-use-rule-data"></a>Come usare i dati della regola  
 La regola raccoglie questi dati di misurazione dalla funzionalità di monitoraggio delle prestazioni di Windows e li riporta a scopo informativo. Usarli della regola per confrontare le prestazioni di versioni o build diverse del programma o per ottenere informazioni sulle prestazioni dell'applicazione in scenari di test diversi.  
  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla [visualizzazione Contrassegni](../profiling/marks-view.md) dei dati di profilatura. Individuare le colonne del contatore **Processo\Working set** e **Memoria\Pagine/sec**. Individuare quindi il valore massimo di **Processo\Working Set** e confrontarlo con il valore di **Memoria\Pagine/sec**. Il valore massimo del working set è spesso associato a un intervallo in cui l'attività I/O di paging è ridotta, specialmente se la memoria del computer è limitata.