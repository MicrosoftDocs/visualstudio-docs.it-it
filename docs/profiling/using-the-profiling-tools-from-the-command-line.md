---
title: Uso degli strumenti per la profilatura dalla riga di comando | Microsoft Docs
description: Usare gli strumenti da riga di comando di Visual Studio Strumenti di profilatura per profilare le applicazioni e automatizzare la profilatura usando file batch e scripting.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6cfb8f26486c731d3900522d72ac62ff6997005e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885950"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Usare gli strumenti per la profilatura dalla riga di comando
È possibile usare gli strumenti da riga di comando degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per eseguire la profilatura di applicazioni dal prompt dei comandi e automatizzare la profilatura tramite file batch e script. È anche possibile generare file di report dal prompt dei comandi. È possibile usare il profiler autonomo leggero per raccogliere dati nei computer in cui non è installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Attività comuni

| Attività | Contenuto correlato |
| - | - |
| **Impostare il percorso dei simboli:** Per visualizzare i nomi di funzioni e parametri, il profiler deve avere accesso al simbolo (.*PDB*) file dei file binari profilati. Questi file devono includere i file di simboli per il sistema operativo Microsoft e le applicazioni da visualizzare nell'analisi. È possibile usare il server di simboli Microsoft pubblico per assicurarsi di avere la correttezza. file *PDB* per i file binari Microsoft. | -   [Procedura: specificare i percorsi dei file di simboli dalla riga di comando](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Eseguire la profilatura dell'applicazione:** gli strumenti e le opzioni della riga di comando usati per la profilatura di un'applicazione di destinazione dipendono dal tipo di applicazione, dal metodo di profilatura e dal fatto che la destinazione sia un'applicazione gestita o nativa. | -   [Usare i metodi di profilatura dalla riga di comando](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profilare applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Servizi profili](../profiling/command-line-profiling-of-services.md) |
| **Creare report XML e CSV:** la profilatura dal prompt dei comandi crea file di dati che possono essere visualizzati nell'interfaccia di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È anche possibile generare. valore *XML* o delimitato da virgole (.*CSV*) file dei dati tramite lo strumento da riga di comando VSPerfReport. | -   [Creare report del profiler dalla riga di comando](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md) |
| **Eseguire la profilatura del codice nei computer senza Visual Studio:** è possibile usare il profiler autonomo degli strumenti di profilatura per raccogliere dati per le applicazioni nei computer in cui non è installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. | -   [Procedura: installare il profiler autonomo](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>Riferimento
- [Riferimento Strumenti di profilatura della riga di comando](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>Vedi anche
- [Esplora prestazioni](../profiling/performance-explorer.md)
