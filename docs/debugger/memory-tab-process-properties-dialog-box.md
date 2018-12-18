---
title: "Scheda di memoria, finestra di dialogo Proprietà processo | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f846b66378f73239adf025d017e3553aaf6046a8
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2018
---
# <a name="memory-tab-process-properties-dialog-box"></a>Scheda Memoria, finestra di dialogo Proprietà processo
Utilizzare il **memoria** scheda per visualizzare l'utilizzo della memoria da parte di un processo. Per visualizzare il [finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo per un [visualizzazione processi](../debugger/processes-view.md) finestra. Selezionare qualsiasi nodo del processo nell'albero, quindi scegliere **proprietà** dal **vista** menu.  
  
 Le impostazioni seguenti sono disponibili sul **memoria** scheda:  
  
|Voce|Descrizione|  
|-----------|-----------------|  
|**Byte virtuali**|Le dimensioni correnti (in byte) di spazio degli indirizzi virtuali usata dal processo. L'utilizzo dello spazio degli indirizzi virtuali non implica necessariamente un uso corrispondente di pagine su disco o memoria principale. Tuttavia, lo spazio virtuale è finito e utilizzare troppo elevato può limitare la capacità del processo di caricare librerie.|  
|**Numero massimo byte virtuali**|Il numero massimo di byte di spazio degli indirizzi virtuali di processo è stato utilizzato in qualsiasi momento.|  
|**Working Set**|Il set di pagine di memoria utilizzate di recente dai thread nel processo. Se la memoria disponibile nel computer supera una soglia, le pagine vengono lasciate nel Working Set di un processo, anche se non sono in uso. Quando la memoria disponibile scende sotto una soglia, le pagine vengono rimosse dal Working Set. Se sono necessarie, saranno richiamate nuovamente nel Working Set prima di lasciare la memoria principale.|  
|**Working Set massimo**|Il numero massimo di pagine del working set del processo in qualsiasi punto nel tempo.|  
|**Byte del Pool di paging**|La quantità corrente di pool di paging allocata dal processo. Pool di paging è un'area di memoria di sistema in cui i componenti del sistema operativo acquisiscono spazio, come il completamento delle attività assegnate. Le pagine del pool di paging possono essere inviate al file di paging quando non vi si accede dal sistema per lunghi periodi di tempo.|  
|**Byte del Pool non di paging**|Numero corrente di byte nel pool non di paging allocata dal processo. Il pool non di paging è un'area della memoria di sistema in cui lo spazio viene acquisito da componenti del sistema operativo come il completamento delle attività assegnate. Pagine del pool non di paging non possono essere inviate al file di paging. rimangono nella memoria principale come vengono allocati.|  
|**Byte privati**|Il numero corrente di byte allocati da questo processo non può essere condivisa con altri processi.|  
|**Byte liberi**|Lo spazio di indirizzi virtuale totale inutilizzato del processo.|  
|**Byte riservati**|La quantità totale di memoria virtuale riservata per utilizzi futuri da questo processo.|  
|**Byte immagine liberi**|La quantità di spazio degli indirizzi virtuali non è in uso o riservato dalle immagini all'interno di questo processo.|  
|**Byte riservati immagine**|La somma della memoria virtuale riservata dalle immagini eseguite all'interno di questo processo.|