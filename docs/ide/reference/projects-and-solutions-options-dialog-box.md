---
title: Finestra di dialogo Progetti e soluzioni, Opzioni | Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd72380cbc17d0ff161a296e1ef08e238159da43
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="projects-and-solutions-options-dialog-box"></a>Progetti e soluzioni, Opzioni (finestra di dialogo)
Consente di impostare il comportamento di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in relazione a progetti e soluzioni. Per accedere a queste opzioni selezionare **Strumenti > Opzioni**, espandere **Progetti e soluzioni** e fare clic su **Generale**.

I percorsi predefiniti per le cartelle di progetti e modelli vengono impostati nella scheda **Percorsi** della stessa finestra di dialogo.
  
> [!NOTE]
>  Le opzioni disponibili nelle finestre di dialogo e i nomi e i percorsi dei comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida a seconda dell'edizione o delle impostazioni attive. Questo argomento della Guida è stato creato tenendo presente le **Impostazioni generali per lo sviluppo**. Per visualizzare o modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti**. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="general-tab-options"></a>Opzioni della scheda Generale

**Mostra sempre Elenco errori se la compilazione finisce con errori**  
Apre la finestra **Elenco errori** al completamento della compilazione, ma solo se la compilazione di un progetto non è riuscita. Vengono visualizzati gli errori che si sono verificati durante il processo di compilazione. Quando questa opzione è deselezionata, gli errori si verificano ugualmente, ma la finestra non verrà aperta una volta completata la compilazione. Questa opzione è attivata per impostazione predefinita.  

**Tieni traccia degli elementi attivi in Esplora soluzioni**  
Se selezionata, **Esplora soluzioni** viene aperto automaticamente e l'elemento attivo viene selezionato. L'elemento selezionato cambia quando si lavora con diversi file in un progetto o soluzione oppure componenti diversi in una finestra di progettazione. Quando questa opzione è deselezionata, la selezione in **Esplora soluzioni** non viene modificata automaticamente. Questa opzione è attivata per impostazione predefinita.  

**Mostra configurazioni della build avanzate**  
Se selezionata, le opzioni di configurazione di compilazione vengono visualizzate nella finestra di dialogo **Pagine delle proprietà** del progetto e nella finestra di dialogo **Pagine delle proprietà** della soluzione. Se deselezionata, le opzioni di configurazione di compilazione non vengono visualizzate nella finestra di dialogo **Pagine delle proprietà** del progetto e nella finestra di dialogo **Pagine delle proprietà** della soluzione per i progetti [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] che contengono una sola configurazione oppure le due configurazioni debug e rilascio. Se un progetto ha una configurazione definita dall'utente, verranno visualizzate le opzioni di configurazione di compilazione.  

Se è deselezionata, i comandi del menu **Compila**, ad esempio **Compila soluzione**, **Ricompila soluzione** e **Pulisci soluzione**, vengono eseguiti nella configurazione Rilascio e i comandi dal menu **Debug**, ad esempio **Avvia il debug** e **Avvia senza eseguire debug**, vengono eseguiti nella configurazione Debug.  

**Mostra sempre soluzione**  
Se selezionata, la soluzione e tutti i comandi che agiscono sulle soluzioni vengono sempre visualizzati nell'IDE. Se deselezionata, tutti i progetti vengono creati come progetti autonomi e la soluzione non viene visualizzata in Esplora soluzioni o i comandi che agiscono sulle soluzioni non vengono visualizzati nell'IDE se la soluzione contiene un solo progetto.  

**Salva nuovi progetti alla creazione**  
Se selezionata, è possibile specificare un percorso per il progetto nella finestra di dialogo **Nuovo progetto**. Se deselezionata, tutti i nuovi progetti vengono creati come progetti temporanei. Quando si lavora con i progetti temporanei, è possibile creare ed effettuare prove con un progetto senza dover specificare un percorso sul disco.  

**Avvisa utente quando il percorso del progetto non è attendibile**  
Se si prova a creare un nuovo progetto o ad aprire un progetto esistente in una posizione non completamente attendibile (ad esempio, in un percorso UNC o un percorso HTTP), verrà visualizzato un messaggio. Usare questa opzione per specificare se il messaggio viene visualizzato ogni volta che si prova a creare o ad aprire un progetto in una posizione non completamente attendibile.  

**Mostra finestra di output a inizio compilazione**  
Consente di visualizzare automaticamente la finestra di Output nell'IDE all'inizio delle compilazioni della soluzione. Per altre informazioni, vedere [Procedura: Controllare la finestra di output](http://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858).

**Richiedi ridenominazione simbolica quando vengono rinominati i file**  
Se selezionata, viene visualizzata una finestra di messaggio che richiede se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve rinominare anche tutti i riferimenti nel progetto all'elemento di codice.  

**Chiedi conferma prima di spostare i file in un'altra posizione**  
Se selezionata, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] visualizza una finestra di messaggio di conferma prima che i percorsi dei file vengano modificati dalle azioni di Esplora soluzioni. 

## <a name="locations-tab-options"></a>Opzioni della scheda Percorsi

**Percorso progetti**  
Specifica il percorso predefinito in cui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] crea nuove cartelle di progetti e soluzioni. Anche diverse finestre di dialogo usano il percorso impostato in questa opzione come punto di partenza della cartella. Ad esempio, la finestra di dialogo Apri progetto usa questo percorso per il collegamento Progetti.  

**Percorso dei modelli di progetto utente**  
Specifica il percorso predefinito usato dalla finestra di dialogo **Nuovo progetto** per creare l'elenco **Modelli personali**. Per altre informazioni, vedere [Procedura: Individuare e organizzare modelli](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  

**Percorso dei modelli di elemento utente**  
Specifica il percorso predefinito usato dalla finestra di dialogo **Aggiungi nuovo elemento** per creare l'elenco **Modelli personali**. Per altre informazioni, vedere [Procedura: Individuare e organizzare modelli](../../ide/how-to-locate-and-organize-project-and-item-templates.md). 

## <a name="see-also"></a>Vedere anche  
- [Finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)  
- [Finestra di dialogo Opzioni, Progetti e soluzioni, Progetti Web](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)