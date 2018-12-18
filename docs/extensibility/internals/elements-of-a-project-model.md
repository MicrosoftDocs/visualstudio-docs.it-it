---
title: Gli elementi di un modello di progetto | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c5f230da41efa8dd2fa522a5f86ae1402991b2cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="elements-of-a-project-model"></a>Elementi di un modello di progetto
Le interfacce e implementazioni di tutti i progetti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] condividono una struttura di base: il modello di progetto per il tipo di progetto. Nel modello di progetto che è il pacchetto VSPackage si sta sviluppando, creare oggetti conformi con le decisioni di progettazione e interagiscono con la funzionalità globale fornita dall'IDE. Anche se il controllo il mantenimento di un elemento di progetto, ad esempio, non si controlla la notifica che un file deve essere resa persistente. Quando un utente inserisce lo stato attivo su un elemento di progetto aperto e sceglie **salvare** sul **File** menu il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menu barra, codice del tipo di progetto devono intercettare il comando dall'IDE, mantenere il file, e Invia notifica all'IDE che non viene modificato il file.  
  
 Il pacchetto VSPackage interagisce con l'IDE tramite i servizi che forniscono l'accesso alle interfacce IDE. Ad esempio, tramite il servizio specifico, monitoraggio e route comandi e si forniscono informazioni di contesto per le selezioni effettuate nel progetto. Tutte le funzionalità IDE globali necessarie per il pacchetto VSPackage sono fornita dai servizi. Per ulteriori informazioni sui servizi, vedere [procedura: ottenere un servizio](../../extensibility/how-to-get-a-service.md).  
  
 Altre considerazioni sull'implementazione:  
  
-   Un modello di progetto singolo può contenere più di un tipo di progetto.  
  
-   Tipi di progetto e la factory dei progetti Supervisore sono registrate in modo indipendente con GUID.  
  
-   Ogni progetto deve avere un file di modello o una procedura guidata per inizializzare il nuovo file di progetto quando un utente crea un nuovo progetto tramite la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente. Ad esempio, il [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] modelli inizializzare cosa diventare vcproj (file).  
  
 Nella figura seguente mostra le interfacce primarie, servizi e gli oggetti che compongono l'implementazione di un progetto tipico. È possibile utilizzare l'helper di applicazione, HierUtil7, per creare gli oggetti sottostanti e altri standard di programmazione. Per ulteriori informazioni sull'helper di applicazione HierUtil7, vedere [non incluso nella Build: utilizzo di classi di progetto HierUtil7 per implementare un tipo di progetto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
 ![Rappresentazione grafica di Visual Studio progetto modello](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
modello di progetto  
  
 Per ulteriori informazioni sulle interfacce e i servizi elencati nel diagramma precedente e altre interfacce facoltative non inclusi nel diagramma, vedere [componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md).  
  
 Progetti può supportare i comandi e pertanto deve implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia deve far parte di comandi (routing) tramite il contesto del GUID.  
  
## <a name="see-also"></a>Vedere anche  
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Non incluso nella Build: utilizzo di classi di progetto HierUtil7 per implementare un tipo di progetto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)   
 [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Procedura: ottenere un servizio](../../extensibility/how-to-get-a-service.md)   
 [Creazione di tipi di progetto](../../extensibility/internals/creating-project-types.md)