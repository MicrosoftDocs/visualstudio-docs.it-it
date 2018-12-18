---
title: 'Procedura: Visualizzare, salvare e configurare file di log di compilazione | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1a57911b8736af27caf0bd9ba30e9e03bdebed2d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Procedura: visualizzare, salvare e configurare file di log di compilazione
Dopo aver compilato un progetto nell'IDE di Visual Studio, è possibile visualizzare informazioni sulla compilazione nella finestra **Output**. Usando queste informazioni è possibile ad esempio risolvere un errore di compilazione. Per i progetti C++ è possibile visualizzare le stesse informazioni anche in un file con estensione txt creato e salvato automaticamente. Per i progetti di codice gestito è possibile copiare e incollare le informazioni dalla finestra **Output** in un file con estensione txt e salvarlo manualmente. È anche possibile usare l'IDE per specificare i tipi di informazioni da visualizzare per ogni compilazione.  
  
 Se si compila qualsiasi tipo di progetto usando MSBuild, è possibile creare un file con estensione txt per salvare le informazioni sulla compilazione. Per altre informazioni, vedere [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
### <a name="to-view-the-build-log-file-for-a-c-project"></a>Per visualizzare il file di log di compilazione per un progetto C++  
  
1.  In **Esplora risorse** o **Esplora file** aprire il file seguente: \\...\Visual Studio *Version*\Projects\\*ProjectName*\\*ProjectName*\Debug\\*ProjectName*.txt  
  
### <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Per creare un file di log di compilazione per un progetto di codice gestito  
  
1.  Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
2.  Nella finestra **Output** evidenziare le informazioni di compilazione e quindi copiarle negli Appunti.  
  
3.  Aprire un editor di testo, ad esempio Blocco note, incollare le informazioni nel file e quindi salvarlo.  
  
### <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Per modificare la quantità di informazioni inclusa nel log di compilazione  
  
1.  Nella barra dei menu scegliere **Strumenti**, **Opzioni**.  
  
2.  Nella pagina **Progetti e soluzioni** scegliere la pagina **Compila ed esegui**.  
  
3.  Nell'elenco **Livello di dettaglio output in compilazione progetto MSBuild** scegliere uno dei valori seguenti e quindi scegliere il pulsante **OK**.  
  
    |Livello di dettaglio|Descrizione|  
    |---------------------|-----------------|  
    |Quiet|Visualizza solo un riepilogo della compilazione.|  
    |Minimal|Visualizza un riepilogo della compilazione e gli errori, gli avvisi e i messaggi classificati con priorità elevata.|  
    |Normale|Visualizza un riepilogo della compilazione, gli errori, gli avvisi e i messaggi classificati con priorità elevata e le fasi principali della compilazione. Si tratta del livello di dettaglio usato più di frequente.|  
    |Dettagliato|Visualizza un riepilogo della compilazione, gli errori, gli avvisi e i messaggi classificati con priorità elevata, tutte le fasi della compilazione e i messaggi classificati con priorità normale.|  
    |Diagnostico|Visualizza tutti i dati disponibili per la compilazione. È possibile usare questo livello di dettaglio per facilitare il debug di problemi con gli script di compilazione personalizzati e altri problemi di compilazione.|  
  
     Per altre informazioni, vedere [Finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) e <xref:Microsoft.Build.Framework.LoggerVerbosity>.  
  
    > [!IMPORTANT]
    >  È necessario ricompilare il progetto per rendere effettive le modifiche nella finestra **Output** (tutti i progetti) e nel file *ProjectName*.txt (solo progetti C++).  
  
## <a name="see-also"></a>Vedere anche  
 [Obtaining Build Logs](../msbuild/obtaining-build-logs-with-msbuild.md)  (Recupero di log di compilazione)  
 [Compilazione e pulizia di progetti e soluzioni in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Compilazione e creazione](../ide/compiling-and-building-in-visual-studio.md)