---
title: Il caricamento di progetto in una soluzione di gestione | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a2be2c75704646bab50f89377d960d44f6fa14f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="managing-project-loading-in-a-solution"></a>Gestire il caricamento di progetto in una soluzione
Soluzioni di Visual Studio possono contenere un numero elevato di progetti. Il comportamento di Visual Studio predefinito consiste nel caricare tutti i progetti in una soluzione al momento che dell'apertura della soluzione e non consentire all'utente di accedere a tutti i progetti finché non termina il caricamento di tutti gli elementi. Quando il processo di caricamento progetto durata più di due minuti, viene visualizzato un indicatore di stato che mostra il numero di progetti caricati e il numero totale di progetti. L'utente può scaricare i progetti mentre si lavora in una soluzione con più progetti, ma questa procedura presenta alcuni svantaggi: non compilati progetti scaricati come parte di un comando Ricompila soluzione e le descrizioni di IntelliSense dei tipi e membri di chiuso i progetti non vengono visualizzati.  
  
 Gli sviluppatori possono ridurre i tempi di caricamento di soluzione e gestire il comportamento di caricamento tramite la creazione di un caricamento della soluzione responsabile di progetto. Gestione del carico di soluzione possibile impostare il caricamento di priorità per progetti specifici o tipi di progetto del progetto diverso, assicurarsi che i progetti siano caricati prima di avviare una compilazione in background, ritardare il caricamento in background fino al completamento di altre attività in background ed eseguire altre attività di gestione del carico di progetto.  
  
## <a name="project-loading-priorities"></a>Il caricamento di priorità del progetto  
 Visual Studio definisce i quattro livelli di priorità di progetto diverso durante il caricamento:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>(predefinito): quando viene aperta una soluzione, i progetti vengono caricati in modo asincrono. Se la priorità è impostata su un progetto scaricato dopo la soluzione è già aperta, il progetto verrà caricato al successivo punto di inattività.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: quando viene aperta una soluzione, i progetti vengono caricati in background, consentendo all'utente di accedere ai progetti come vengono caricati senza dover attendere finché non vengono caricati tutti i progetti.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: i progetti vengono caricati quando vi si accede. Quando si espande il nodo del progetto in Esplora soluzioni, quando un file che appartiene al progetto viene aperto quando la soluzione viene aperta perché è nell'elenco di documenti aperti (persistente nel file della soluzione user options) o quando si accede a un progetto di un altro progetto vale a dire il progetto in fase di caricamento presenta una dipendenza. Questo tipo di progetto non viene caricato automaticamente prima di avviare un processo di compilazione. Gestione del carico di soluzione è responsabile di garantire che tutti i progetti necessari siano caricati. Questi progetti devono inoltre essere caricati prima di avviare una ricerca/sostituzione nei file attraverso l'intera soluzione.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: i progetti non devono essere caricati a meno che l'utente richiede in modo esplicito. Ciò avviene quando i progetti vengono scaricati in modo esplicito.  
  
## <a name="creating-a-solution-load-manager"></a>Creazione di un caricamento della soluzione gestione  
 Gli sviluppatori possono creare un caricamento della soluzione gestione implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> e Visual Studio che informa che è attiva la gestione del carico di soluzione.  
  
#### <a name="activating-a-solution-load-manager"></a>L'attivazione di gestione di un carico di soluzione  
 Visual Studio consente un solo gestore di caricamento di soluzioni in un determinato momento, pertanto è necessario informare Visual Studio quando si desidera attivare il caricamento della soluzione gestione. Se un manager di carico secondo soluzione viene attivato in un secondo momento, la gestione del carico di soluzione verrà disconnesso.  
  
 È necessario ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> del servizio e impostare il <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> proprietà:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implementazione IVsSolutionLoadManager  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> metodo viene chiamato durante il processo di apertura della soluzione. Per implementare questo metodo, utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> servizio per impostare la priorità di carico per il tipo di progetto che si desidera gestire. Ad esempio, il codice seguente imposta i tipi di progetto c# per il caricamento in background:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> metodo viene chiamato quando Visual Studio viene arrestato o quando un pacchetto diverso ha assunto come gestione del carico di soluzione attiva chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> con il <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> proprietà.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie per diversi tipi di gestore di caricamento di soluzioni  
 È possibile implementare gestori carico soluzione in modi diversi, a seconda dei tipi di soluzioni che sono disponibili solo per la gestione.  
  
 Se la gestione del carico di soluzioni deve gestire soluzioni durante il caricamento in generale, può essere implementata come parte di un VSPackage. Il pacchetto deve essere impostato su autoload aggiungendo il <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> nel pacchetto VSPackage con un valore di <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Gestione del carico di soluzione quindi può essere attivata la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo.  
  
> [!NOTE]
>  Per ulteriori informazioni sui pacchetti di caricamento automatico, vedere [VSPackage durante il caricamento](../extensibility/loading-vspackages.md).  
  
 Poiché Visual Studio riconosce solo la gestione di carico soluzione ultimo da attivare, gestioni di carico soluzione generale devono sempre rilevare se è un gestore di carico esistente prima di attivare autonomamente. Se la chiamata di GetProperty() sul servizio soluzione per <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> restituisce `null`, non è disponibile alcun gestore di carico di soluzione attiva. Se non viene restituito null, controllare se l'oggetto è lo stesso come la gestione del carico di soluzione.  
  
 Se la gestione del carico di soluzioni deve gestire solo pochi tipi di soluzione, il pacchetto VSPackage può sottoscrivere gli eventi di caricamento della soluzione (chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) e utilizzare il gestore eventi per <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> per attivare la gestione del carico di soluzione.  
  
 Se la gestione del carico di soluzioni deve gestire solo soluzioni specifiche, è possono rendere persistenti le informazioni di attivazione come parte del file della soluzione. A tale scopo, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> per la sezione di pre-soluzione.  
  
 Gestori di soluzioni specifiche carico verrà disattivato nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> gestore dell'evento, in modo da non in conflitto con altri gestori di caricamento della soluzione.  
  
 Se è necessario un manager di carico soluzione solo per rendere persistenti le priorità di caricamento di progetti globale (ad esempio, proprietà impostate in una pagina di opzioni), è possibile attivare la gestione del carico di soluzione nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> gestore dell'evento, mantenere l'impostazione della proprietà della soluzione, quindi disattivare la gestione del carico di soluzione.  
  
## <a name="handling-solution-load-events"></a>Gestione degli eventi di caricamento di soluzioni  
 Per sottoscrivere gli eventi di caricamento della soluzione, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> quando si attiva la gestione del carico di soluzione. Se si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, è possibile rispondere agli eventi che riguardano il caricamento di priorità del progetto diverso.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Viene generato prima dell'apertura di una soluzione. È possibile utilizzare, per modificare il progetto durante il caricamento di priorità per i progetti nella soluzione.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Viene generato dopo la soluzione è completamente caricata, ma prima di background avvia nuovamente il caricamento del progetto. Ad esempio, un utente abbia avuto accesso un progetto la cui priorità di carico è LoadIfNeeded o gestione del carico di soluzione sono state modificate una priorità di caricamento progetto per BackgroundLoad, che avvia un caricamento in background del progetto.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Viene generato dopo una soluzione è inizialmente completamente caricata, se non è presente un gestore di caricamento di soluzioni. Inoltre viene generato dopo il caricamento o richiesta caricato ogni volta che la soluzione diventa completamente caricata. Allo stesso tempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> viene riattivato.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Viene generato prima del caricamento di un progetto (o progetti). Per garantire che altri processi in background vengono completati prima che i progetti vengono caricati, impostare `pfShouldDelayLoadToNextIdle` a **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Viene generato quando sta per essere caricato un batch di progetti. Se `fIsBackgroundIdleBatch` è true, i progetti devono essere caricati in background; se `fIsBackgroundIdleBatch` è false, i progetti devono essere caricati in modo sincrono in seguito a una richiesta dell'utente, ad esempio se l'utente lo espande un progetto in Esplora soluzioni in sospeso. È possibile implementare questa per eseguire operazioni costose che in caso contrario sarebbero necessario eseguire <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Viene generato dopo il caricamento di un batch di progetti.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Rilevamento e la gestione di soluzioni e il caricamento di progetto  
 Per rilevare lo stato di caricamento dei progetti e soluzioni, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> con i valori seguenti:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` restituisce `true` se la soluzione e tutti i relativi progetti vengono caricati, in caso contrario `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` restituisce `true` se un batch di progetti vengono attualmente caricate in background, in caso contrario `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` restituisce `true` se un batch di progetti vengono attualmente caricati in modo sincrono a causa di un comando dell'utente o altri carico esplicita, in caso contrario `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` restituisce `true` se la soluzione attualmente viene chiuso, in caso contrario `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` restituisce `true` se una soluzione attualmente viene aperto, in caso contrario `false`.  
  
 È inoltre possibile garantire che i progetti e soluzioni vengono caricate (indipendentemente da quali sono le priorità di caricamento del progetto), chiamando uno dei metodi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: questo metodo forza i progetti in una soluzione per caricare prima il metodo restituisce.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: questo metodo forza i progetti in `guidProject` caricare prima il metodo restituisce.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: questo metodo forza il progetto in `guidProjectID` caricare prima il metodo restituisce.  
  
> [!NOTE]
>  . Per impostazione predefinita solo i progetti con la richiesta di caricamento e vengono caricate le priorità di caricamento in background, ma se il <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> flag viene passato al metodo, verranno caricati tutti i progetti tranne quelli che sono contrassegnati per caricare in modo esplicito.