---
title: 'Procedura: implementare progetti annidati | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 757668070daacb449a6bc7cbd88ae629fe6487a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-nested-projects"></a>Procedura: implementare progetti annidati
Quando si crea un tipo di progetto annidato sono sono un alcuni passaggi aggiuntivi che devono essere implementati. Un progetto padre assume alcune delle responsabilità stessa con la soluzione per i progetti nidificati (figlio). Il progetto principale è un contenitore di progetti è simili a una soluzione. In particolare, sono disponibili diversi eventi che devono essere generati per la soluzione e per i progetti padre per compilare la gerarchia di progetti annidati. Questi eventi sono descritte nel processo seguente per la creazione di progetti annidati.  
  
### <a name="to-create-nested-projects"></a>Per creare progetti annidati  
  
1.  Ambiente di sviluppo integrato (IDE) carica le informazioni di avvio e i file di progetto del progetto padre chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfaccia. Il progetto principale viene creato e aggiunto alla soluzione.  
  
    > [!NOTE]
    >  A questo punto, è abbastanza recente del processo per il progetto principale creare il progetto annidato perché è necessario creare il progetto principale prima di possono creare i progetti figlio. Questa sequenza, il progetto principale è possibile applicare le impostazioni per i progetti figlio e i progetti figlio possono acquisire informazioni dai progetti padre, se necessario. Questa sequenza è se è necessario in dai client, ad esempio Esplora soluzioni e di controllo del codice sorgente (SCC).  
  
     Il progetto principale deve attendere il <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> metodo chiamato dall'IDE prima dei relativi nidificati (figlio) può creare i progetti.  
  
2.  Le chiamate IDE `QueryInterface` per il progetto padre per <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>. Se la chiamata ha esito positivo, le chiamate a IDE il <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> metodo dell'oggetto padre per aprire tutti i progetti nidificati per il progetto principale.  
  
3.  Le chiamate di progetto padre il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> metodo per notificare ai listener che annidati progetti devono essere creati. Controllo del codice sorgente, ad esempio, è in ascolto per tali eventi a sapere se si verificano nell'ordine i passaggi nel processo di creazione di soluzioni e progetti. Se si verificano i passaggi nell'ordine errato, la soluzione potrebbe non essere registrata con controllo del codice sorgente in modo corretto.  
  
4.  Le chiamate di progetto padre <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> metodo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> metodo su ciascuno dei relativi progetti figlio.  
  
     Si passa <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> per il `AddVirtualProject` metodo per indicare che il progetto (nidificato) virtuale deve essere aggiunti alla finestra di progetto, escluso dalla compilazione, aggiunto al controllo del codice sorgente e così via. `VSADDVPFLAGS`Consente di controllare la visibilità del progetto annidato e indicare quali funzionalità sono associata.  
  
     Se si Ricarica progetto figlio già esistente che include un progetto GUID archiviato nel file di progetto del progetto padre, le chiamate di progetto padre `AddVirtualProjectEx`. L'unica differenza tra `AddVirtualProject` e `AddVirtualProjectEX` che `AddVirtualProjectEX` dispone di un parametro per abilitare il progetto principale specificare una per ogni istanza `guidProjectID` per il progetto figlio abilitare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> alla funzione in modo corretto.  
  
     Se non è presente alcun GUID disponibili, ad esempio quando si aggiunge un nuovo progetto nidificato, la soluzione viene creata una per il progetto al momento viene aggiunto all'elemento padre. È responsabilità del progetto per mantenere tale progetto GUID nel file di progetto principale. Se si elimina un progetto nidificato, il GUID per il progetto può anche essere eliminato.  
  
5.  Le chiamate a IDE il `M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren` metodo su ogni progetto figlio del progetto principale.  
  
     Il progetto padre deve implementare `IVsParentProject` se si desidera nidificare i progetti. Ma l'elemento padre progetto mai chiamate `QueryInterface` per `IVsParentProject` anche se presenta progetti principali disponibili al suo interno. La soluzione gestisce la chiamata a `IVsParentProject` e, se viene implementato, chiama `OpenChildren` per creare i progetti annidati. `AddVirtualProjectEX`viene sempre chiamato da `OpenChildren`. Non dovrebbe mai essere chiamato dal progetto padre per mantenere la gerarchia, gli eventi di creazione in ordine.  
  
6.  Le chiamate a IDE il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> metodo sul progetto figlio.  
  
7.  Le chiamate di progetto padre il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> metodo per notificare ai listener che siano stati creati i progetti figlio per l'elemento padre.  
  
8.  Le chiamate a IDE il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> metodo sul progetto padre dopo l'apertura di tutti i progetti figlio.  
  
     Se non esiste già, il progetto principale crea un GUID per ogni progetto annidato chiamando `CoCreateGuid`.  
  
    > [!NOTE]
    >  `CoCreateGuid`è un'API COM chiamata quando un GUID da creare. Per ulteriori informazioni, vedere `CoCreateGuid` e i GUID in MSDN Library.  
  
     Il progetto principale archivia questo GUID nel relativo file di progetto per recuperare la prossima volta che viene aperto nell'IDE. Vedere il passaggio 4 per ulteriori informazioni relative al chiamante di `AddVirtualProjectEX` per recuperare il `guidProjectID` per il progetto figlio.  
  
9. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> viene quindi chiamato il metodo per l'elemento padre ItemID per convenzione delegare per il progetto annidato. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> recupera le proprietà del nodo che consente di annidare un progetto che si desidera delegare quando viene chiamato sull'oggetto padre.  
  
     Poiché i progetti padre e figlio vengono creata un'istanza a livello di codice, è possibile impostare le proprietà dei progetti annidati a questo punto.  
  
    > [!NOTE]
    >  Non solo ricevono le informazioni sul contesto dal progetto nidificato, ma è inoltre possibile richiedere se il progetto principale dispone di alcun contesto per l'elemento controllando <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>. In tal modo, è possibile aggiungere attributi aggiuntivi Guida dinamica e le opzioni di menu specifiche per singoli progetti annidati.  
  
10. La gerarchia viene compilata per la visualizzazione in Esplora soluzioni con una chiamata al <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> metodo.  
  
     Passare la gerarchia dell'ambiente mediante `GetNestedHierarchy` per compilare la gerarchia per la visualizzazione in Esplora soluzioni. In questo modo, la soluzione sa che il progetto esista e può essere gestito per la compilazione dal gestore di compilazione oppure consentire i file del progetto da inserire nel controllo del codice sorgente.  
  
11. Quando sono stati creati tutti i progetti annidati per Project1, il controllo viene passato nuovamente alla soluzione e il processo viene ripetuto per Project2.  
  
     Lo stesso processo per la creazione di progetti annidati si verifica per un progetto figlio che include un elemento figlio. In questo caso, se BuildProject1, vale a dire un elemento figlio di Project1, conteneva progetti figlio, si creerebbe BuildProject1 e precede Project2. Il processo è ricorsiva e la gerarchia viene compilata dall'alto verso il basso.  
  
     Quando un progetto annidato viene chiuso perché l'utente ha chiuso la soluzione o di specifiche di progetto, l'altro metodo `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, viene chiamato. Il progetto principale esegue il wrapping di chiamate per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> metodo con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> per notificare a listener di eventi di soluzione che i progetti annidati vengono chiusi.  
  
 Gestiscono diversi altri concetti da considerare quando si implementano progetti annidati gli argomenti seguenti:  
  
 [Considerazioni per lo scaricamento e il ricaricamento di progetti annidati](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
 [Supporto di procedure guidate per i progetti annidati](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
 [Implementazione della gestione dei comandi per i progetti annidati](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
 [Applicazione di un filtro nella finestra di dialogo AddItem per i progetti annidati](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta di elementi di Aggiungi nuovo elemento di finestre di dialogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parametri di contesto](../../extensibility/internals/context-parameters.md)   
 [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)