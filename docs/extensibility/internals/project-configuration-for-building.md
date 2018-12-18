---
title: Configurazione per la compilazione del progetto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d78ac1cabc356db162639d3eb19d0bff71e295e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="project-configuration-for-building"></a>Configurazione di progetto per la compilazione
L'elenco di configurazioni di soluzione per una determinata soluzione è gestito dalla finestra di dialogo configurazioni di soluzione.  
  
 Un utente può creare configurazioni di soluzione aggiuntive, ognuna con un nome univoco. Quando l'utente crea una nuova configurazione di soluzione, l'IDE per impostazione predefinita al nome della configurazione in progetti o di Debug se non esiste alcun nome corrispondente. L'utente può modificare la selezione per soddisfare esigenze specifiche, se necessario. L'unica eccezione a questo comportamento è quando il progetto supporta una configurazione che corrisponde al nome della nuova configurazione di soluzione. Si supponga, ad esempio, che una soluzione contiene Progetto1 e Progetto2. Project1 dispone di configurazioni di progetto MyConfig1, finale e Debug. Project2 dispone di configurazioni di progetto MyConfig2, finale e Debug.  
  
 Se l'utente crea una nuova configurazione di soluzione denominata MyConfig2, Project1 associa la configurazione di Debug per la configurazione della soluzione per impostazione predefinita. Project2 associa anche la relativa configurazione MyConfig2 per la configurazione della soluzione per impostazione predefinita.  
  
> [!NOTE]
>  L'associazione è tra maiuscole e minuscole.  
  
 Quando l'utente seleziona il **selezione multipla** elemento nell'elenco a discesa configurazione, l'ambiente consente di visualizzare una finestra di dialogo che fornisce l'elenco delle configurazioni disponibili.  
  
 ![Configurazioni multiple](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
Configurazioni multiple  
  
 In questa finestra di dialogo, l'utente può selezionare una o più configurazioni. Una volta selezionato, i valori delle proprietà visualizzati nella finestra di dialogo Pagine delle proprietà rifletteranno l'intersezione dei valori per le configurazioni selezionate.  
  
 Vedere [configurazione soluzione](../../extensibility/internals/solution-configuration.md) per le informazioni relative all'aggiunta e ridenominazione di configurazioni per i progetti e soluzioni.  
  
 Dipendenze del progetto e ordine di compilazione sono indipendenti dalla configurazione della soluzione:, è possibile impostare solo albero una dipendenza per tutti i progetti nella soluzione. Facendo clic la soluzione o il progetto e quindi scegliere il **dipendenze progetto** o **ordine compilazione progetto** opzione viene visualizzata la **dipendenze progetto** la finestra di dialogo. Può anche essere aperta dal **progetto** menu.  
  
 ![Dipendenze progetto](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
Dipendenze progetto  
  
 Dipendenze del progetto determinano l'ordine in cui compilare i progetti. Utilizzare la scheda di ordine di compilazione nella finestra di dialogo per visualizzare l'ordine esatto in cui i progetti all'interno di una soluzione di compilare e utilizzare la scheda dipendenze per modificare l'ordine di compilazione.  
  
> [!NOTE]
>  I progetti nell'elenco le caselle di controllo selezionate ma vengono visualizzate in grigio sono stati aggiunti dall'ambiente a causa di dipendenze esplicite specificato dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfacce e non può essere modificato. Ad esempio, aggiungendo un riferimento al progetto da un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] progetto a un altro progetto aggiunge automaticamente una dipendenza di compilazione che può essere rimossa solo eliminando il riferimento. Impossibile selezionare progetti cui caselle di controllo sono chiare e vengono visualizzate in grigio perché questa operazione creerebbe un ciclo di dipendenze (ad esempio Project1 sarebbe dipende Project2 e Project2 sarebbe dipende Project1), che verrebbe interruzione della compilazione.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i processi di compilazione includono la compilazione tipiche e le operazioni di collegamento che vengano richiamate con un singolo comando di compilazione. Due altri processi di compilazione possono anche essere supportati: un'operazione di pulizia per eliminare tutti gli elementi di output da una compilazione precedente e un controllo aggiornato per determinare se un elemento di output in una configurazione è stato modificato.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> gli oggetti restituiscono un oggetto corrispondente <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (restituito da <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) per gestire i processi di compilazione. Per segnalare lo stato di un'operazione di compilazione in corso, configurazioni di effettuano chiamate a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, un'interfaccia implementata dall'ambiente e qualsiasi altro oggetto interessati a eventi dello stato di compilazione.  
  
 Una volta creato, è possono utilizzare le impostazioni di configurazione per determinare se può essere eseguiti sotto il controllo del debugger. Implementano le configurazioni <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> per supportare il debug.  
  
 Dopo aver implementato le dipendenze di progetto, è possibile modificare a livello di codice le dipendenze tramite il modello di automazione. Chiamare <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> nel modello di automazione. Non sono presenti interfacce disponibili di VSIP a livello di API che consentono la manipolazione diretta di configurazioni di compilazione di soluzioni manager e le relative proprietà.  
  
 Inoltre, è possibile fornire una griglia nella finestra di dipendenze del progetto. Per ulteriori informazioni, vedere [griglia di visualizzazione delle proprietà](../../extensibility/internals/properties-display-grid.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)   
 [Configurazione di progetto per la distribuzione di gestione](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)