---
title: Il caricamento di progetto in una soluzione di gestione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d0e479a96252710d1f7e6285ffaaa2baf383c061
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="managing-project-loading-in-a-solution"></a>Gestire il caricamento di progetto in una soluzione
Soluzioni di Visual Studio possono contenere un numero elevato di progetti. Il comportamento di Visual Studio predefinito consiste nel caricare tutti i progetti in una soluzione al momento che dell'apertura della soluzione e non consentire all'utente di accedere a tutti i progetti finché non termina il caricamento di tutti gli elementi. Quando il processo di caricamento progetto durata più di due minuti, viene visualizzato un indicatore di stato che mostra il numero di progetti caricati e il numero totale di progetti. L'utente può scaricare i progetti mentre si lavora in una soluzione con più progetti, ma questa procedura presenta alcuni svantaggi: non compilati progetti scaricati come parte di un comando Ricompila soluzione e le descrizioni di IntelliSense dei tipi e membri di chiuso i progetti non vengono visualizzati.  
  
 Gli sviluppatori possono ridurre i tempi di caricamento di soluzione e gestire il comportamento di caricamento tramite la creazione di un caricamento della soluzione responsabile di progetto. La gestione di caricamento di soluzioni può assicurarsi che i progetti siano caricati prima di avviare una compilazione in background, ritardare il caricamento in background fino al completamento di altre attività in background ed eseguire altre attività di gestione di carico.  
  
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
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> metodo viene chiamato quando Visual Studio viene arrestato o quando un pacchetto diverso ha assunto come gestione del carico di soluzione attiva chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> con il <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> proprietà.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie per diversi tipi di gestore di caricamento di soluzioni  
 È possibile implementare gestori carico soluzione in modi diversi, a seconda dei tipi di soluzioni che sono disponibili solo per la gestione.  
  
 Se la gestione del carico di soluzioni deve gestire soluzioni durante il caricamento in generale, può essere implementata come parte di un VSPackage. Il pacchetto deve essere impostato su autoload aggiungendo il <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> nel pacchetto VSPackage con un valore di <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Gestione del carico di soluzione quindi può essere attivata la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo.  
  
> [!NOTE]
>  Per ulteriori informazioni sui pacchetti di caricamento automatico, vedere [VSPackage durante il caricamento](../extensibility/loading-vspackages.md).  
  
 Poiché Visual Studio riconosce solo la gestione di carico soluzione ultimo da attivare, gestioni di carico soluzione generale devono sempre rilevare se è un gestore di carico esistente prima di attivare autonomamente. Se la chiamata di GetProperty() sul servizio soluzione per <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> restituisce `null`, non è disponibile alcun gestore di carico di soluzione attiva. Se non viene restituito null, controllare se l'oggetto è lo stesso come la gestione del carico di soluzione.  
  
 Se la gestione del carico di soluzioni deve gestire solo pochi tipi di soluzione, il pacchetto VSPackage può sottoscrivere gli eventi di caricamento della soluzione (chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) e utilizzare il gestore eventi per <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> per attivare la gestione del carico di soluzione.  
  
 Se la gestione di caricamento di soluzioni deve gestire solo soluzioni specifiche, le informazioni di attivazione possono essere reso persistente come parte del file di soluzione chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> per la sezione di pre-soluzione.  
  
 Gestori di soluzioni specifiche carico verrà disattivato nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> gestore dell'evento, in modo da non in conflitto con altri gestori di caricamento della soluzione.  
  
 Se è necessario un manager di carico soluzione solo per rendere persistenti le proprietà di carico di progetti globale (ad esempio, proprietà impostate in una pagina di opzioni), è possibile attivare la gestione del carico di soluzione nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> gestore dell'evento, mantenere l'impostazione nella proprietà della soluzione, quindi disattivare la gestione del carico di soluzione.  
  
## <a name="handling-solution-load-events"></a>Gestione degli eventi di caricamento di soluzioni  
 Per sottoscrivere gli eventi di caricamento della soluzione, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> quando si attiva la gestione del carico di soluzione. Se si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, è possibile rispondere agli eventi correlati al progetto diverso, il caricamento delle proprietà.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Questo evento viene generato prima dell'apertura di una soluzione.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Questo evento viene generato dopo la soluzione viene completamente caricata, ma in background prima di inizia nuovamente il caricamento del progetto.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Questo evento viene generato dopo che una soluzione viene inizialmente completamente caricata, se non è presente un gestore di caricamento di soluzioni. Inoltre viene generato dopo il caricamento o richiesta caricato ogni volta che la soluzione diventa completamente caricata. Allo stesso tempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> viene riattivato.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Questo evento viene generato prima del caricamento di un progetto (o progetti). Per garantire che altri processi in background vengono completati prima che i progetti vengono caricati, impostare `pfShouldDelayLoadToNextIdle` a **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Questo evento viene generato quando sta per essere caricato un batch di progetti. Se `fIsBackgroundIdleBatch` è true, i progetti devono essere caricati in background; se `fIsBackgroundIdleBatch` è false, i progetti devono essere caricati in modo sincrono in seguito a una richiesta dell'utente, ad esempio se l'utente lo espande un progetto in Esplora soluzioni in sospeso. È possibile gestire questo evento per eseguire operazioni costose che in caso contrario, dovrà essere eseguita in <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Questo evento viene generato dopo il caricamento di un batch di progetti.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Rilevamento e la gestione di soluzioni e il caricamento di progetto  
 Per rilevare lo stato di caricamento dei progetti e soluzioni, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> con i valori seguenti:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` restituisce `true` se la soluzione e tutti i relativi progetti vengono caricati, in caso contrario `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` restituisce `true` se un batch di progetti attualmente caricato in background, in caso contrario `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` restituisce `true` se un batch di progetti attualmente caricato in modo sincrono in seguito a un comando dell'utente o altre condizioni di carico esplicita, in caso contrario `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` restituisce `true` se chiudere la soluzione è attualmente in corso, in caso contrario `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` restituisce `true` se viene aperta una soluzione attualmente in corso, in caso contrario `false`.  
  
 È inoltre possibile garantire che i progetti e soluzioni vengono caricate chiamando uno dei metodi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: questo metodo forza i progetti in una soluzione per caricare prima il metodo restituisce.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: questo metodo forza i progetti presenti nella `guidProject` caricare prima il metodo restituisce.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: questo metodo forza il progetto in `guidProjectID` caricare prima il metodo restituisce.  
