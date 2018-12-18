---
title: User (VSPerfCmd) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b774367120c9c33be57018fd8ea94674febfbf5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="user-vsperfcmd"></a>User (VSPerfCmd)
L'opzione **User** specifica il dominio e il nome utente dell'account proprietario del processo profilato. Questa opzione è obbligatoria solo se il processo è in esecuzione come utente diverso dall'utente connesso. Il proprietario del processo è elencato nella colonna Nome utente nella scheda Processi di Gestione attività di Windows.  
  
 L'opzione **User** può essere specificata solo in una riga di comando che contiene anche l'opzione **Start**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### <a name="parameters"></a>Parametri  
 `Domain`  
 Nome del dominio dell'utente.  
  
 `UserName`  
 Nome dell'utente.  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 L'opzione **User** può essere usata solo con l'opzione **Start**.  
  
 **Start:** `Method`  
 Inizializza il profiler sul metodo di profilatura specificato.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra l'uso dell'opzione **User**.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)