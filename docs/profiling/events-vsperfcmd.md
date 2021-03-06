---
title: Events (VSPerfCmd) | Microsoft Docs
description: Controllare Event Tracing for Windows registrazione (ETW) utilizzando l'opzione eventi nello strumento da riga di comando VSPerfCmd.exe. Esaminare i parametri della sintassi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1ec92cae275d9f73f24f983905bc0013950e9d37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899561"
---
# <a name="events-vsperfcmd"></a>Events (VSPerfCmd)
L'opzione **eventi** *VSPerfCmd.exe* controlla la registrazione di Event Tracing for Windows (ETW). I dati ETW vengono salvati in un file ETL separato dal file di dati del profiler. I dati possono essere visualizzati in un report usando il comando di [VSPerfReport](../profiling/vsperfreport.md) /summary: ETW.

 L'opzione **Events** può essere chiamata in qualsiasi momento prima di chiamare il comando **Shutdown** di VSPerfCmd per arrestare la profilatura.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]
```

#### <a name="parameters"></a>Parametri
 **On**&#124;**Off** Avvia o arresta la raccolta dei dati dell'evento.

 `Guid` GUID del controllo provider.

 `ProviderName` Nome del provider registrato con Strumentazione gestione Windows (WMI).

 `Flags` Valore di flag esadecimale con prefisso "0x" definito dal provider di eventi.

 `Level` Specifica la quantità di dati raccolti. `Level` è definito dal provider di eventi.

 L'opzione **Events** riconosce le seguenti parole chiave del kernel come nomi di provider:

 **Process** Eventi dei processi

 **Thread** Eventi dei thread

 **Image** Eventi di caricamento e scaricamento di immagini

 **Disk** Eventi di I/O dei dischi

 **File** Eventi di I/O dei file

 **Hardfault** Errori di pagina hardware

 **Pagefault** Errori di pagina software

 **Network** Eventi di rete

 **Registry** Eventi di accesso al Registro di sistema

 Si noti che il provider del Kernel può solo essere abilitato. Non può essere disattivato, né i relativi flag possono essere modificati, finché il monitor non viene chiuso.

## <a name="remarks"></a>Commenti

> [!NOTE]
> Quando sono abilitati gli eventi ETW di CLR i dati di avvio aggiuntivi vengono raccolti anche nel report della visualizzazione tracce. Per evitare che gli eventi di avvio vengano visualizzati nel report, usare il comando seguente:

```cmd
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5
```

> [!IMPORTANT]
> Se non si escludono gli eventi di avvio, poiché non sono elencati nel file MOF (Managed Object Format), tali eventi vengono visualizzati come GUID nel report. Per altre informazioni, vedere la pagina [File di esempio Managed Object Format (MOF)](https://msdn.microsoft.com/library/default.aspx) nel sito Web Microsoft.

## <a name="see-also"></a>Vedi anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
