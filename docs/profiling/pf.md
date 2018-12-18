---
title: PF | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 548a4cedf715faf998912500bf3e2390ac07070b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="pf"></a>PF
L'opzione **PF** di VSPerfCmd.exe imposta l'evento di profilatura campionato per gli errori di pagina e modifica facoltativamente il numero di cicli in un intervallo di campionamento dal valore predefinito di 10.  
  
> [!NOTE]
>  L'opzione PF non può esser usata in sistemi a 64 bit.  
  
 Si noti che l'opzione **PF** non è supportata nei computer a 64 bit. L'opzione **PF** può essere usata solo in una riga di comando che contiene anche l'opzione **Launch** o l'opzione **Attach**.  
  
 Per impostazione predefinita, l'evento di campionamento è impostato sui cicli del clock del processore non interrotti e l'intervallo di campionamento è impostato su 10.000.000. Le opzioni **Timer**, **PF**, **Sys** e **Counter** consentono di impostare l'evento di campionamento e l'intervallo di campionamento. L'opzione **GC** raccoglie dati di memoria .NET in corrispondenza di ogni evento di allocazione e di Garbage Collection. È possibile specificare solo una di queste opzioni in una riga di comando.  
  
 L'evento di campionamento e l'intervallo di campionamento possono essere impostati solo nella prima riga di comando che include un'opzione **Launch** o **Attach**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### <a name="parameters"></a>Parametri  
 `Events`  
 Valore intero che specifica il numero di eventi di errore di pagina in un intervallo di campionamento. Se non si specifica `Events`, l'intervallo viene impostato su 10.  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 L'opzione **PF** può essere specificata solo in una riga di comando che include una delle opzioni seguenti.  
  
 **Launch:** `AppName`  
 Avvia il profiler e l'applicazione specificata da AppName.  
  
 **Attach:** `PID`  
 Collega il profiler al processo specificato da AppName.  
  
## <a name="invalid-options"></a>Opzioni non valide  
 Le opzioni seguenti non possono essere specificate nella stessa riga di comando che include **PF**.  
  
 **Timer**[**:**`Cycles`]  
 Imposta l'evento di campionamento sui cicli di clock del processore e, facoltativamente, imposta l'intervallo di campionamento su `Cycles`. L'intervallo Timer predefinito è 10.000.000.  
  
 **Sys**[**:**`Events`]  
 Imposta l'evento di campionamento per le chiamate dall'applicazione profilata al kernel del sistema operativo (syscall) e imposta facoltativamente l'intervallo di campionamento su `Events`. L'intervallo Sys predefinito è 10.  
  
 **Counter:** `Name`[`,Reload`[`,FriendlyName`]]  
 Imposta l'evento di campionamento sul contatore delle prestazioni della CPU specificato da `Name` e imposta l'intervallo di campionamento su `Reload`.  
  
 **GC**[**:**{**Allocation**&#124;**Lifetime**}]  
 Raccoglie dati di memoria .NET. Per impostazione predefinita, (**Allocation**), i dati vengono raccolti in corrispondenza di ogni evento di allocazione di memoria. Quando si specifica il parametro **Lifetime**, i dati vengono raccolti anche in corrispondenza di ogni evento di Garbage Collection.  
  
## <a name="example"></a>Esempio  
 Questo esempio illustra come impostare l'evento di campionamento di profilatura per gli errori di pagina e imposta l'intervallo di campionamento su 20 errori di pagina.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)