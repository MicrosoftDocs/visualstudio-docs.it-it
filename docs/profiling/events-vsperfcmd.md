---
title: Events (VSPerfCmd) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3cfbeaa9c11bdb24b561e0dfdc10e8ab2a10053a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="events-vsperfcmd"></a>Events (VSPerfCmd)
L'opzione **Events** di VSPerfCmd.exe controlla la registrazione di Event Tracing for Windows (ETW). I dati ETW vengono salvati in un file ETL separato dal file di dati del profiler. I dati possono essere visualizzati in un report usando il comando di [VSPerfReport](../profiling/vsperfreport.md) /summary: ETW.  
  
 L'opzione **Events** può essere chiamata in qualsiasi momento prima di chiamare il comando **Shutdown** di VSPerfCmd per arrestare la profilatura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### <a name="parameters"></a>Parametri  
 **On**&#124;**Off**  
 Avvia o arresta la raccolta dei dati dell'evento.  
  
 `Guid`  
 GUID del controllo provider.  
  
 `ProviderName`  
 Nome del provider registrato con Strumentazione gestione Windows (WMI).  
  
 `Flags`  
 Valore di flag esadecimale con prefisso "0x" definito dal provider di eventi.  
  
 `Level`  
 Specifica la quantità di dati raccolti. `Level` è definito dal provider di eventi.  
  
 L'opzione **Events** riconosce le seguenti parole chiave del kernel come nomi di provider:  
  
 **Processo**  
 Eventi del processo  
  
 **Thread**  
 Eventi del thread  
  
 **Immagine**  
 Eventi di caricamento e scaricamento di immagini  
  
 **Disk**  
 Eventi di I/O dei dischi  
  
 **File**  
 Eventi di I/O dei file  
  
 **Hardfault**  
 Errori di pagina hardware  
  
 **PageFault**  
 Errori di pagina software  
  
 **Network**  
 Eventi di rete  
  
 **Registry**  
 Eventi di accesso al Registro di sistema  
  
 Si noti che il provider del Kernel può solo essere abilitato. Non può essere disattivato, né i relativi flag possono essere modificati, finché il monitor non viene chiuso.  
  
## <a name="remarks"></a>Note  
  
> [!NOTE]
>  Quando sono abilitati gli eventi ETW di CLR i dati di avvio aggiuntivi vengono raccolti anche nel report della visualizzazione tracce. Per evitare che gli eventi di avvio vengano visualizzati nel report, usare il comando seguente:  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  Se non si escludono gli eventi di avvio, poiché non sono elencati nel file MOF (Managed Object Format), tali eventi vengono visualizzati come GUID nel report. Per altre informazioni, vedere la pagina [File di esempio Managed Object Format (MOF)](http://go.microsoft.com/fwlink/?linkid=37118) nel sito Web Microsoft.  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)