---
title: 'Elenco di controllo: Creazione di nuovi tipi di progetto | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 11707e62e99dd6a7920ad627d02e6e418c002e80
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="checklist-creating-new-project-types"></a>Elenco di controllo: Creazione di nuovi tipi di progetto
È necessario completare diverse attività per creare un nuovo tipo di progetto. L'elenco di controllo seguente viene fornita una Guida alle attività.  
  
1.  Progettare la funzionalità per il nuovo tipo di progetto. Per ulteriori informazioni, vedere [decisioni di progettazione di tipo di progetto](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Determinare quale editor vengono utilizzati per codice e altri elementi del progetto. È possibile utilizzare i componenti di base o l'editor standard oppure è possibile creare e utilizzare gli editor specifici del progetto. Per ulteriori informazioni, vedere [creare editor personalizzati e finestre di progettazione](../../extensibility/creating-custom-editors-and-designers.md) e [procedura: aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Determinare il livello di partecipazione avranno gli elementi del progetto come il **Visualizzazione classi** e **Visualizzatore oggetti**. Per ulteriori informazioni, vedere [strumenti di esplorazione simbolo supporto](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Derivare nuove classi di base sulle decisioni di progettazione effettuate in precedenza per il progetto e gli elementi di progetto.  
  
5.  Scrivere il codice per i componenti di tipo di progetto seguenti:  
  
    -   Factory del progetto, per gestire la creazione di nuovi progetti e aprire progetti esistenti. Per ulteriori informazioni, vedere [la creazione di istanze da utilizzando progetto factory dei progetti](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Gerarchia del progetto e la gestione dei comandi. Per ulteriori informazioni, vedere [non incluso nella Build: utilizzo di classi di progetto HierUtil7 per implementare un tipo di progetto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346), [gli elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md), [componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)e [tra oggetti MenuCommand e. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
    -   Gestione elementi di progetto, inclusa l'aggiunta del progetto per il **nuovo progetto** la finestra di dialogo. Per ulteriori informazioni, vedere [aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md) e [registrazione Project and Item Templates](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Persistenza dello stato di progetto e i singoli elementi. Per ulteriori informazioni, vedere [di apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md). Per la persistenza di informazioni sulla soluzione, vedere [soluzioni](../../extensibility/internals/solutions.md).  
  
    -   Proprietà indipendente di configurazione da visualizzare nella finestra Proprietà. Per ulteriori informazioni, vedere [estensione di proprietà](../../extensibility/internals/extending-properties.md).  
  
    -   Proprietà di configurazione del progetto come implementato nelle pagine delle proprietà per visualizzare le proprietà dipendenti dalla configurazione. Per ulteriori informazioni, vedere [la gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).  
  
    -   L'enumerazione di output per la distribuzione. Per ulteriori informazioni, vedere [configurazione per l'Output del progetto](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Servizi di avvio del progetto. Per ulteriori informazioni, vedere [gli elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md) e [componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md).  
  
    -   Gli oggetti o le classi derivate da `IDispatch`, disponibile per l'automazione.  
  
    -   File di tabella comandi XML (con estensione vsct). Per ulteriori informazioni, vedere [Visual Studio Command Table (. File Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Test, eseguire il debug e il tipo di progetto di avvio.  
  
7.  Visualizzare il progetto nel **progetto** scheda della finestra di **Aggiungi riferimento** la finestra di dialogo impostando `VARIANT_TRUE` come valore per `VSHPROPID_ShowProjInSolutionPage`. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Creare il file di Microsoft Installer (MSI) per l'installazione di VSPackage. Per ulteriori informazioni, vedere [l'installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [registrazione di un tipo di progetto](../../extensibility/internals/registering-a-project-type.md), e [VSPackage](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Quando creare tipi di progetto](../../extensibility/internals/when-to-create-project-types.md)   
 [Creazione di tipi di progetto](../../extensibility/internals/creating-project-types.md)