---
title: 'Procedura: Eseguire il Debug di un motore di Debug personalizzato | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0b814b441846479163aad4e003480cc9cfadde44
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Procedura: Eseguire il Debug di un motore di Debug personalizzati
Un tipo di progetto consente di avviare il motore di debug (DE) dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metodo. Ciò significa che la Germania venga avviato con il controllo dell'istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il controllo del tipo di progetto. Tuttavia, tale istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non è possibile eseguire il debug la Germania. Di seguito è riportati i passaggi per consentire il debug la Germania personalizzato.  
  
> [!NOTE]
>  : Nella procedura "Debug di un motore di Debug di Custom", è necessario attendere DE avviare prima di poterla associare a esso. Se si inserisce una finestra di messaggio nella parte iniziale della Germania che viene visualizzato all'avvio la Germania, è possibile collegare a questo punto e quindi deselezionare la casella di messaggio per continuare. In questo modo, è possibile intercettare tutti gli eventi DE.  
  
> [!WARNING]
>  È necessario che il debug remoto installato prima di tentare le procedure seguenti. Vedere [il debug remoto](../../debugger/remote-debugging.md) per informazioni dettagliate.  
  
### <a name="debugging-a-custom-debug-engine"></a>Debug di un motore di Debug personalizzati  
  
1.  Avviare msvsmon.exe, Remote Debugging Monitor.  
  
2.  Dal **strumenti** menu msvsmon.exe, selezionare **opzioni** per aprire la **opzioni** la finestra di dialogo.  
  
3.  Selezionare l'opzione "Nessuna autenticazione" e fare clic su **OK**.  
  
4.  Avvia un'istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e aprire il progetto DE personalizzato.  
  
5.  Avviare una seconda istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e aprire un progetto personalizzato che consente di avviare la Germania (per lo sviluppo, si tratta in genere nell'hive del Registro di sistema sperimentale impostato quando viene installato VSIP).  
  
6.  In questa seconda istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], caricare un file di origine da un progetto personalizzato e avviare il programma da sottoporre a debug. Attendere qualche minuto per consentire la Germania caricare o attendere fino a quando non viene raggiunto un punto di interruzione.  
  
7.  Nella prima istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (con il progetto DE), selezionare **Connetti a processo** dal **Debug** menu.  
  
8.  Nel **Connetti a processo** nella finestra di dialogo Modifica il **trasporto** a **remoto (solo nativo senza autenticazione)**.  
  
9. Modifica il **qualificatore** sul nome del computer (Nota: è presente una cronologia delle voci, pertanto è necessario digitare il nome una sola volta).  
  
10. Nel **processi disponibili** elenco, selezionare l'istanza della Germania che sia in esecuzione e fare clic su di **collegamento** pulsante.  
  
11. Dopo i simboli sono caricati nella Germania, inserire punti di interruzione nel codice DE.  
  
12. Ogni volta che si arresta e riavvia il processo di debug, ripetere i passaggi da 6 a 10.  
  
### <a name="debugging-a-custom-project-type"></a>Debug di un tipo di progetto personalizzati  
  
1.  Avviare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nell'hive del Registro di sistema normale di caricamento progetto digitare progetto (si tratta, l'origine per il tipo di progetto, non un'istanza del tipo di progetto).  
  
2.  Aprire le proprietà del progetto e passare al **Debug** pagina. Per il **comando**, digitare il percorso di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (per impostazione predefinita, si tratta di *[unità]*\Programmi\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).  
  
3.  Per il **gli argomenti del comando**, tipo `/rootsuffix exp` per l'hive del Registro di sistema sperimentale (creato durante l'installazione di VSIP).  
  
4.  Fai clic su **OK** per accettare le modifiche.  
  
5.  Avviare il tipo di progetto premendo F5. Verrà avviata una seconda istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
6.  A questo punto, è possibile inserire punti di interruzione nel codice di origine del tipo di progetto.  
  
7.  Nella seconda istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], caricare o creare una nuova istanza del tipo di progetto. Durante la creazione o di carico, i punti di interruzione può essere raggiunto.  
  
8.  Eseguire il debug del tipo di progetto.  
  
9. Se si sceglie di debug del processo di avvio un Germania, è possibile eseguire i passaggi nella procedura "Debug di un motore di Debug di Custom" a cui connettersi la Germania dopo che viene avviata. Questa query fornirà tre istanze di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in esecuzione: una per l'origine del tipo di progetto e un altro per il tipo di progetto creata un'istanza e un terzo associata per la Germania.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)