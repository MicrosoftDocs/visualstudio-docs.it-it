---
title: Attach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98e18456ad4665359e33d7a9b5f064585f8195be
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="attach"></a>Attach
L'opzione **Attach** di VSPerfCmd.exe avvia una profilatura campione del processo in esecuzione specificato dall'ID processo (PID).  
  
 Per usare l'opzione **Attach**, è necessario specificare il metodo **Sample** nell'opzione Start.  
  
> [!NOTE]
>  Se l'opzione **Start** è stata specificata con l'opzione **Crosssession**, eventuali chiamate a **VSPerfCmd /Attach** o a **VSPerfCmd /Detach** devono specificare anche **Crosssession**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Attach:ProcessID [Options]  
```  
  
#### <a name="parameters"></a>Parametri  
 `ProcessID`  
 ID di processo (PID) del processo in esecuzione. Il PID di un processo in esecuzione è indicato nella scheda Processi di Gestione attività di Windows.  
  
## <a name="valid-options"></a>Opzioni valide  
 Le seguenti opzioni di **VSPerfCmd** possono essere combinate con l'opzione **Attach** in una singola riga di comando.  
  
 **Crosssession**  
 Consente la profilatura delle applicazioni in sessioni diverse da quella di accesso. Obbligatoria se l'opzione **Start** è stata specificata con l'opzione **Crosssession**.  
  
 **Start:** `Method`  
 Inizializza la sessione del profiler da riga di comando e imposta il metodo di profilatura specificato.  
  
 **TargetCLR**  
 Specifica la versione di Common Language Runtime (CLR) .NET Framework da sottoporre a profilatura quando in una sessione di profilatura è caricata più di una versione. Per impostazione predefinita, viene sottoposta a profilatura la prima versione caricata.  
  
 **GlobalOn GlobalOff**  
 Riprende (**GlobalOn**) o sospende (**GlobalOff**) la profilatura, ma non termina la sessione di profilatura.  
  
 **ProcessOn:** `PID` **ProcessOff:** `PID`  
 Riprende (**ProcessOn**) o sospende (**ProcessOff**) la profilatura per il processo specificato.  
  
## <a name="interval-options"></a>Opzioni di intervallo  
 È possibile specificare una delle opzioni seguenti per l'intervallo di campionamento nella riga di comando di Attach. L'intervallo di campionamento predefinito è 10.000.000 di cicli di clock del processore.  
  
 **Timer**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[**:** Events]**Counter**[**:**`Name`,`Reload`,`FriendlyName`]  
 Specifica il numero e il tipo di intervallo di campionamento.  
  
-   **Timer**: esegue il campionamento ogni `Cycles` cicli di clock del processore. Se non si specifica `Cycles`, vengono usati 10.000.000 di cicli.  
  
-   **PF**: esegue il campionamento ogni `Events` errori di pagina. Se non si specifica `Events`, vengono usati 10 errori di pagina.  
  
-   **Sys**: esegue il campionamento ogni `Events` chiamate al sistema operativo. Se non si specifica `Events`, vengono usate 10 chiamate del sistema.  
  
-   **Counter**: esegue il campionamento ogni `Reload` dei contatori delle prestazioni della CPU specificato da `Name`. Facoltativamente, `FriendlyName` può specificare una stringa da usare come intestazione di colonna nei report del profiler.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come connettersi a un'istanza di un'applicazione in esecuzione con ID processo 12345.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)