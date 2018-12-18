---
title: Shutdown | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f2e5411a4d5b88340105f71248ca2e5c2410ff12
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="shutdown"></a>Arresta
L'opzione **Shutdown** attende il termine o la disconnessione di qualsiasi processo in corso di profilatura, quindi disattiva il profiler e chiude il file di dati di profilatura. L'opzione **Shutdown** deve essere l'ultimo comando di un'esecuzione di profilatura.  
  
 Se non si specifica un parametro di timeout, l'opzione **Shutdown** attenderà per un tempo illimitato. Se si specifica un parametro di timeout, l'opzione restituisce il controllo dopo il numero di secondi specificato senza disattivare il profiler o chiudere il file di dati.  
  
 L'opzione **Shutdown** deve essere l'unica opzione specificata nella riga di comando.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>Parametri  
 `Timeout`  
 -   (Facoltativo) Se specificata, l'opzione restituisce il controllo dopo il numero di secondi specificato senza disattivare il profiler o chiudere il file di dati di profilatura.  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)