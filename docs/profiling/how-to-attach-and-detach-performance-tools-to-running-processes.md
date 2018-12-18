---
title: 'Procedura: Connettere e disconnettere gli strumenti per le prestazioni ai processi in esecuzione | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c53dcbec5d41b6aa93eef115bba966076fcfda2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Procedura: Connettere e disconnettere gli strumenti per le prestazioni ai processi in esecuzione
Il profiler può essere usato per la connessione o la disconnessione da un processo in esecuzione per facilitare la raccolta e il campionamento dei dati relativi alle prestazioni. È possibile usare questo metodo per la profilatura di un processo quando si vuole evitare di raccogliere dati sul tempo di caricamento dell'applicazione o per monitorare le prestazioni di un processo dopo il raggiungimento di uno stato specifico.  
  
> [!NOTE]
>  La procedura riportata di seguito si applica alle operazioni di connessione e disconnessione dei processi nell'ambiente di sviluppo integrato (IDE) di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Per informazioni su come usare gli strumenti della riga di comando, vedere [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md). Per informazioni su come profilare i servizi, vedere [Profilatura di servizi](../profiling/command-line-profiling-of-services.md).  
  
 I processi disponibili per la profilatura dipendono dalle autorizzazioni di accesso a livello utente impostate dall'amministratore del computer. Un account utente può, ad esempio, disporre dell'autorizzazione per uno dei seguenti elementi:  
  
-   Funzionalità di profilatura avanzate, quando l'amministratore ha impostato l'avvio del driver e del servizio.  
  
-   Solo profilatura dei campioni (utenti di dominio).  
  
-   Accesso negato alla profilatura per tutti gli utenti.  
  
 Per altre informazioni, vedere [Profilatura e sicurezza in Windows Vista](../profiling/profiling-and-windows-vista-security.md) e le opzioni ADMIN in [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-attach-to-a-running-process"></a>Per connettersi a un processo in esecuzione  
  
1.  Nel menu **Debug** scegliere **Profiler**, **Esplora prestazioni** e quindi fare clic su **Connetti**.    
  
     Verrà visualizzata la finestra di dialogo **Connettere profiler a processo**.  
  
2.  Fare clic sul nome del processo a cui si vuole effettuare la connessione.  
  
3.  Scegliere **Connetti**.  
  
### <a name="to-detach-from-a-running-process"></a>Per disconnettersi da un processo in esecuzione  
  
1.  Nel menu **Debug** scegliere **Profiler**, **Esplora prestazioni** e quindi fare clic su **Disconnetti**. 
  
     Verrà visualizzata la finestra di dialogo **Connettere profiler a processo**.  
  
2.  Fare clic sul nome dell'immagine da cui eseguire la disconnessione.  
  
3.  Scegliere **Disconnetti**.  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo della raccolta di dati](../profiling/controlling-data-collection.md)   
 [Panoramica delle sessioni di prestazioni](../profiling/performance-session-overview.md)   
 [Procedura: Iniziare e terminare la raccolta dei dati sulle prestazioni](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Profilatura e sicurezza in Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)