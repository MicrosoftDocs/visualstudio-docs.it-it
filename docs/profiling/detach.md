---
title: Detach | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 02ff1bd3e3db51a444d371e2e803f77ef1429676
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2018
---
# <a name="detach"></a>Detach
L'opzione **Detach** di VSPerfCmd.exe disconnette il profiler dai processi specificati o da tutti i processi se non ne vengono specificati. La profilatura deve essere inizializzata usando il metodo di campionamento.  
  
 La profilatura avviata con l'opzione **Launch** o **Attach** può essere disconnessa con **Detach**. Il profiler può essere connesso nuovamente usando comandi **Attach** successivi.  
  
 **Detach** non consente di chiudere il file di dati di profilatura. Usare l'opzione **Shutdown** per terminare la profilatura e chiudere il file di dati.  
  
> [!NOTE]
>  Se l'opzione **Start** è stata specificata con l'opzione **Crosssession**, eventuali chiamate a **VSPerfCmd /Attach** o a **VSPerfCmd /Detach** devono specificare anche **Crosssession**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### <a name="parameters"></a>Parametri  
 `PIDs|ProcessNames`  
 `PID` - Identificatore numerico del sistema di uno o più processi.  
  
 `ProcessNames` - Nome del processo. Se si eseguono più istanze del processo denominato, i risultati sono imprevedibili.  
  
 Se si specificano più processi, separarli con virgole.  
  
 Se non viene specificato alcun processo, il profiler viene disconnesso da tutti i processi profilati.  
  
## <a name="valid-options"></a>Opzioni valide  
 Le seguenti opzioni di **VSPerfCmd** possono essere combinate con l'opzione **Attach** in una singola riga di comando.  
  
 **Crosssession**  
 Consente la profilatura delle applicazioni in sessioni diverse da quella di accesso. Obbligatoria se l'opzione **Start** è stata specificata con l'opzione **Crosssession**.  
  
## <a name="example"></a>Esempio  
 In questo esempio il comando **Detach** sospende la profilatura e il comando **Shutdown** chiude il file di dati del profiler.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)