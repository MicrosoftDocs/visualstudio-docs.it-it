---
title: Sys (VSPerfCmd) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0e054cc07748e7503cb7410206c5ebff1408725b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
L'opzione **Sys** di VSPerfCmd.exe imposta l'evento di profilatura campionato per gli eventi di chiamata del sistema (chiamate di funzione dall'applicazione profilata al sistema operativo) e, facoltativamente, modifica il numero di chiamate del sistema in un intervallo di campionamento rispetto al valore predefinito 10.  
  
 L'opzione **Sys** può essere usata solo in una riga di comando che contiene anche l'opzione **Launch** o l'opzione **Attach**.  
  
 Per impostazione predefinita, l'evento di campionamento del profiler è impostato sui cicli del clock del processore e l'intervallo di campionamento è impostato su 10.000.000. Le opzioni **Timer**, **PF**, **Sys** e **Counter** consentono di impostare l'evento di campionamento e l'intervallo di campionamento. L'opzione **GC** raccoglie dati di memoria .NET in corrispondenza di ogni evento di allocazione e di Garbage Collection. È possibile specificare solo una di queste opzioni in una riga di comando.  
  
 L'evento di campionamento e l'intervallo di campionamento possono essere impostati solo nella prima riga di comando che include un'opzione **Launch** o **Attach**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]  
```  
  
#### <a name="parameters"></a>Parametri  
 `Events`  
 Valore intero che specifica il numero di eventi di chiamata del sistema in un intervallo di campionamento. Se non si specifica `Events`, l'intervallo viene impostato su 10.  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 **Sys** richiede una delle opzioni seguenti.  
  
 **Launch:** `AppName`  
 Avvia il profiler e l'applicazione specificata da `AppName`.  
  
 **Attach:** `PID`  
 Collega il profiler al processo specificato da `PID`.  
  
## <a name="invalid-options"></a>Opzioni non valide  
 Le opzioni seguenti non possono essere specificate nella stessa riga di comando che include **Sys**.  
  
 **PF**[**:**`Events`]  
 Imposta l'evento di campionamento sugli errori di pagina e, facoltativamente, imposta l'intervallo di campionamento su `Events`. L'intervallo PF predefinito è 10.  
  
 **Timer**[**:**`Cycles`]  
 Imposta l'evento di campionamento sui cicli di clock del processore e, facoltativamente, imposta l'intervallo di campionamento su `Cycles`. L'intervallo Timer predefinito è 10.000.000.  
  
 **Counter:** `Name`[`,Reload`[`,FriendlyName`]]  
 Imposta l'evento di campionamento sul contatore delle prestazioni della CPU specificato da `Name` e imposta l'intervallo di campionamento su `Reload`.  
  
 **GC**[**:**{**Allocation**&#124;**Lifetime**}]  
 Raccoglie dati di memoria .NET. Per impostazione predefinita, (**Allocation**), i dati vengono raccolti in corrispondenza di ogni evento di allocazione di memoria. Quando si specifica il parametro **Lifetime**, i dati vengono raccolti anche in corrispondenza di ogni evento di Garbage Collection.  
  
## <a name="example"></a>Esempio  
 Questo esempio illustra come impostare l'evento di campionamento del profiler sulle chiamate del sistema e come impostare l'intervallo di campionamento su 20 chiamate per campione.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)