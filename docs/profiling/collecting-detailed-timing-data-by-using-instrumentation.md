---
title: Raccolta di dati di intervallo dettagliati tramite la strumentazione | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7bc5b81349c64c3b3422fb16b9cf578d0b8496ea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="collecting-detailed-timing-data-by-using-instrumentation"></a>Raccolta di dati di intervallo dettagliati tramite la strumentazione
Il metodo di strumentazione degli strumenti per la profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inserisce il codice di profilatura in una copia di un modulo. Il codice registra ogni voce, uscita e chiamata di funzione delle funzioni nel modulo durante un'esecuzione di profilatura. Il metodo di strumentazione è utile per raccogliere informazioni dettagliate sugli intervalli relative a una sezione del codice e per comprendere l'impatto delle operazioni di input e output sulle prestazioni dell'applicazione.  
  
 È possibile specificare il metodo di strumentazione tramite una delle procedure seguenti:  
  
-   Nella prima pagina della procedura guidata di profilatura selezionare **Strumentazione**.  
  
-   Nell'elenco **Metodo** della barra degli strumenti di **Esplora prestazioni** fare clic su **Strumentazione**.  
  
-   Nella pagina **Generale** della finestra di dialogo delle proprietà per la sessione di prestazioni selezionare **Strumentazione**.  
  
## <a name="common-tasks"></a>Attività comuni  
 È possibile specificare altre opzioni nella finestra di dialogo *Pagine delle proprietà***Sessioni prestazioni** della sessione di prestazioni. Per aprire questa finestra di dialogo:  
  
-   In **Esplora prestazioni**fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni e quindi scegliere **Proprietà**.  
  
 Le attività nella tabella seguente descrivono le opzioni che è possibile specificare nella finestra di dialogo *Pagine delle proprietà***Sessioni prestazioni** quando si esegue la profilatura con il metodo di strumentazione.  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|Nella pagina **Generale** aggiungere dati di durata e allocazione di memoria .NET e specificare i dettagli di denominazione per il file di dati di profilatura (con estensione vsp) generato.|-   [Raccolta di dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [How to: Set Performance Data File Name Options](../profiling/how-to-set-performance-data-file-name-options.md) (Procedura: Impostare le opzioni relative ai nomi file dei dati di profilatura)|  
|Nella pagina **Avvio** specificare l'applicazione da avviare e l'ordine di avvio se si hanno più progetti EXE nella soluzione.|-   [How to: Specify the Binary to Start](../profiling/how-to-specify-the-binary-to-start.md) (Procedura: Specificare il file binario da avviare)|  
|Nella pagina **Binari** specificare un percorso per le copie instrumentate dei moduli. Per impostazione predefinita, i file binari originali vengono spostati in una cartella di backup.|-   [How to: Relocate Instrumented Binaries](../profiling/how-to-relocate-instrumented-binaries.md) (Procedura: Rilocare file binari sottoposti a strumentazione)|  
|Nella pagina **Interazione tra livelli** aggiungere i dati delle chiamate ADO.NET per l'esecuzione della profilatura.|-   [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|  
|Nella pagina **Strumentazione** escludere le funzioni piccole dalla profilatura per ridurre il sovraccarico di profilatura, eseguire la profilatura del codice JavaScript nelle pagine Web ASP.NET e specificare i comandi da eseguire a un prompt dei comandi prima e dopo il processo di strumentazione.|-   [How to: Exclude or Include Short Functions from Instrumentation](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md) (Procedura: Escludere o includere funzioni brevi nella strumentazione)<br />-   [How to: Profile JavaScript Code in Web Pages](../profiling/how-to-profile-javascript-code-in-web-pages.md) (Procedura: Sottoporre a profilatura codice JavaScript nelle pagine Web)<br />-   [How to: Specify Pre- and Post-Instrument Commands](../profiling/how-to-specify-pre-and-post-instrument-commands.md) (Procedura: Specificare comandi pre- e post-strumentazione)|  
|Nella pagina **Contatori CPU** specificare uno o più contatori di prestazioni del processore da aggiungere ai dati di profilatura.|-   [How to: Collect CPU Counter Data](../profiling/how-to-collect-cpu-counter-data.md) (Procedura: Raccogliere i dati dei contatori CPU)|  
|Nella pagina **Eventi di Windows** selezionare uno o più eventi Event Tracing for Windows (ETW) da raccogliere con i dati di campionamento.|-   [How to: Collect Event Tracing for Windows (ETW) Data](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md) (Procedura: Raccogliere dati ETW (Event Tracing for Windows))|  
|Nella pagina **Contatori Windows** specificare uno o più contatori di prestazioni del sistema operativo da aggiungere ai dati di profilatura come contrassegni.|-   [How to: Collect Windows Counter Data](../profiling/how-to-collect-windows-counter-data.md) (Procedura: Raccogliere i dati dei contatori Windows)|  
|Nella pagina **Avanzate** specificare le opzioni aggiuntive da passare al programma di strumentazione VSInstr, ad esempio le opzioni per includere o escludere funzioni specifiche.|-   [How to: Specify Additional Instrumentation Options](../profiling/how-to-specify-additional-instrumentation-options.md) (Procedura: Specificare opzioni di strumentazione aggiuntive)<br />-   [How to: Limit Instrumentation to Specific Functions](../profiling/how-to-limit-instrumentation-to-specific-functions.md) (Procedura: Limitare la strumentazione a specifiche funzioni)<br />-   [VSInstr](../profiling/vsinstr.md)|