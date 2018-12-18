---
title: Output | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b7452ad6aa8d7f190eebbc35d4be087c14dcd51a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="output"></a>Output
L'opzione **Output** specifica il nome del file di dati di profilatura per la sessione di prestazioni. L'opzione **Output** deve essere usata con l'opzione **Start**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parametri  
 `FileName`  
 Nome del file di dati. Sono accettati percorsi completi e parziali. Se non viene specificato un percorso, il file viene creato nella directory corrente.  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 L'opzione **Output** deve essere usata con l'opzione **Start**.  
  
 **Start:** `Method`  
 Specifica il nome del file di output.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente il file di dati di profilatura viene creato nella directory corrente.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)