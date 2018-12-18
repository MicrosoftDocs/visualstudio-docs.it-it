---
title: Status | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d1168fb27330f49a714e64478fc7ab167569dadb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="status"></a>Status
L'opzione **Status** di VSPerfCmd.exe visualizza informazioni sullo stato del profiler e di eventuali processi in corso di profilatura.  
  
 L'opzione **Status** deve essere l'unica opzione specificata nella riga di comando. Il profiler deve essere inizializzato con l'opzione **Start** di VSPerfCmd.exe prima di poter visualizzare qualsiasi stato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### <a name="parameters"></a>Parametri  
 nessuno  
  
## <a name="remarks"></a>Note  
 L'opzione **Status** consente di visualizzare le informazioni sullo stato seguenti per il profiler.  
  
 **Nome file di output**  
 Percorso e nome del file di dati del profiler corrente.  
  
 **Modalità di raccolta**  
 SAMPLE o TRACE  
  
 **Numero massimo di processi**  
 Numero massimo di processi di cui è possibile eseguire la profilatura contemporaneamente e il numero di processi attivi.  
  
 **Numero massimo di thread**  
 Numero massimo di thead di cui è possibile eseguire la profilatura contemporaneamente.  
  
 **Numero di buffer**  
 Numero di buffer di memoria dedicati alla scrittura dei dati di profilatura.  
  
 **Dimensione dei buffer**  
 Dimensione di un buffer di memoria in byte.  
  
 L'opzione **Status** visualizza le informazioni sullo stato seguenti per ogni processo in corso di profilatura.  
  
 **Processo**  
 Nome del processo profilato.  
  
 **ID processo**  
 Identificatore di sistema del processo.  
  
 **Num. thread**  
 Numero di thread in esecuzione.  
  
 **Conteggio Start/Stop**  
 Conteggio del profiler interno principale per controllare la raccolta dei dati per questo processo. Il conteggio deve essere uguale a uno per raccogliere i dati. Il conteggio Start/Stop può essere modificato dalle API del profiler e dalle opzioni di VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn** e **ThreadOff**.  
  
 **Conteggio Suspend/Resume**  
 Conteggio del profiler interno secondario per controllare la raccolta dei dati per questo processo. Il conteggio deve essere minore o uguale a zero per raccogliere i dati. Il conteggio **Suspend/Resume** può essere modificato solo dalle API del profiler.  
  
 **Utenti con diritti di accesso al monitor**  
 Elenca i nomi degli utenti che hanno accesso al profiler. È possibile concedere l'accesso ad altri utenti tramite l'opzione **Admin** di VSPerfCmd.exe.  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)