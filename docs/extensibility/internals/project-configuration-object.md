---
title: Oggetto di configurazione progetto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7385a5f7768a57fd1a3d9688df152fd60a1ea130
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="project-configuration-object"></a>Oggetto di configurazione di progetto
L'oggetto di configurazione di progetto gestisce la visualizzazione delle informazioni di configurazione per l'interfaccia utente.  
  
 ![Configurazione del progetto di Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
Pagine delle proprietà di configurazione di progetto  
  
 Il Provider di configurazione di progetto gestisce le configurazioni di progetto. L'ambiente e altri pacchetti, per ottenere l'accesso e recuperare informazioni sulle configurazioni del progetto, chiamare le interfacce associate all'oggetto Provider di configurazione di progetto.  
  
> [!NOTE]
>  È possibile creare o modificare i file di configurazione di soluzione a livello di codice. È necessario utilizzare `DTE.SolutionBuilder`. Vedere [configurazione soluzione](../../extensibility/internals/solution-configuration.md) per ulteriori informazioni.  
  
 Per pubblicare un nome visualizzato da utilizzare nella configurazione dell'interfaccia utente, il progetto deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. L'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, che restituisce un elenco di `IVsCfg` puntatori che è possibile utilizzare per ottenere i nomi visualizzati per le informazioni di configurazione e piattaforma da elencare nell'interfaccia utente dell'ambiente. La piattaforma e la configurazione attiva dipendono dalla configurazione del progetto nella configurazione soluzione attiva. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> metodo può essere utilizzato per recuperare la configurazione del progetto attivo.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> oggetto facoltativamente può essere implementato nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> dell'oggetto con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> oggetto consente di recuperare un `IVsProjectCfg2` oggetto in base al nome di configurazione di progetto canonico.  
  
 Un altro modo per fornire l'ambiente e altri progetti con l'accesso alle configurazioni di progetto è per i progetti fornire un'implementazione del `IVsCfgProvider2::GetCfgs` per restituire uno o più oggetti di configurazione. I progetti possono inoltre implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, che eredita da `IVsProjectCfg` e quindi da `IVsCfg`, per fornire informazioni specifiche della configurazione. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> supporta piattaforme e le funzionalità per l'aggiunta, eliminazione e ridenominazione di configurazioni di progetto.  
  
> [!NOTE]
>  Poiché Visual Studio non è più limitato a due tipi di configurazione, il codice che elabora le configurazioni non deve essere scritte con presupposti relativi al numero di configurazioni, né deve essere scritto partendo dal presupposto che un progetto che presenta solo uno configurazione è necessariamente Debug o finale. In questo modo l'utilizzo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> obsoleta.  
  
 La chiamata `QueryInterface` sull'oggetto restituito da`IVsGetCfgProvider::GetCfgProvider` recupera `IVsCfgProvider2`. Se `IVsGetCfgProvider` non viene trovato chiamando `QueryInterface` sul `IVsProject3` oggetto di progetto, è possibile accedere all'oggetto di provider di configurazione chiamando `QueryInterface` sull'oggetto gerarchia principale del browser per l'oggetto restituito per `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, o tramite un puntatore a restituito per il provider di configurazione `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.  
  
 `IVsProjectCfg2` principalmente fornisce l'accesso a compilare, eseguire il debug e distribuzione management objects e consente la libertà di output gruppo di progetti. I metodi di `IVsProjectCfg` e `IVsProjectCfg2` può essere utilizzato per implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> per gestire il processo di compilazione e <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> puntatori per i gruppi di output di una configurazione.  
  
 Il progetto deve restituire lo stesso numero di gruppi per ogni configurazione che supporta anche se il numero di output contenuti all'interno di un gruppo può variare da una configurazione alla configurazione. I gruppi devono anche presentare le stesse informazioni di identificatore (nome canonico, nome visualizzato e informazioni di gruppo) configurazione alla configurazione all'interno di un progetto. Per ulteriori informazioni, vedere [configurazione per l'Output del progetto](../../extensibility/internals/project-configuration-for-output.md).  
  
 Per abilitare il debug, è necessario implementare delle configurazioni di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` interfaccia facoltativa implementata dai progetti per consentire il debugger da avviare una configurazione ed è implementata per l'oggetto di configurazione con `IVsCfg` e `IVsProjectCfg`. L'ambiente viene chiamato quando l'utente sceglie di avviare il debugger premendo F5.  
  
 `ISpecifyPropertyPages` e `IDispatch` vengono utilizzati in combinazione con le pagine delle proprietà per recuperare e visualizzare all'utente informazioni dipendenti dalla configurazione. Per ulteriori informazioni, vedere [pagine delle proprietà](../../extensibility/internals/property-pages.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)   
 [Configurazione di progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)   
 [Configurazione per l'Output del progetto](../../extensibility/internals/project-configuration-for-output.md)   
 [Pagine delle proprietà](../../extensibility/internals/property-pages.md)   
 [Configurazione di soluzioni](../../extensibility/internals/solution-configuration.md)