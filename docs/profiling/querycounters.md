---
title: QueryCounters | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9a05fbb94d818868dbd13ae1c7f1b0c64d68b749
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="querycounters"></a>QueryCounters
L'opzione **QueryCounters** elenca i contatori delle prestazioni della CPU (hardware) disponibili nel computer.  
  
 **QueryCounters** deve essere l'unica opzione nella riga di comando.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Parametri  
 nessuno  
  
## <a name="remarks"></a>Note  
 Quando si usa il metodo di strumentazione, il profiler può raccogliere i valori di uno o più contatori delle prestazioni della CPU per ogni evento di raccolta dati. Quando si usa il metodo di campionamento per la profilatura, è possibile specificare un solo evento di contatore e il numero di occorrenze dell'evento da usare come intervallo di campionamento.  
  
 Processori diversi espongono contatori delle prestazioni della CPU differenti. Il profiler definisce un set di contatori generici utilizzabili per quasi tutti i processori. L'opzione **QueryCounters** elenca sia i nomi dei contatori generici sia i nomi dei contatori specifici del processore.  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)