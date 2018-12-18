---
title: Pagine delle proprietà | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b08e210a57388d77859600c02c0e6a30a404884
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="property-pages"></a>Pagine delle proprietà
Gli utenti possono visualizzare e modificare proprietà dipendenti dalla configurazione e - indipendente tramite pagine delle proprietà del progetto. Oggetto **pagine delle proprietà** pulsante è abilitato nel **proprietà** finestra o sulla barra degli strumenti Esplora soluzioni per gli oggetti che forniscono una visualizzazione della pagina di proprietà dell'oggetto selezionato. Pagine delle proprietà vengono creati dall'ambiente e sono disponibili per i progetti e soluzioni. Possono, tuttavia, essere resa disponibile per gli elementi di progetto che costituiscono l'utilizzo di proprietà dipendenti dalla configurazione. Questa funzionalità può essere usata quando i file all'interno di un progetto richiedono le impostazioni dell'opzione del compilatore diverse compilare in modo corretto.  
  
## <a name="using-property-pages"></a>Utilizzo delle pagine delle proprietà  
 Se è già visualizzata una pagina delle proprietà e la selezione viene modificata (ad esempio, da una soluzione a un progetto), le informazioni visualizzate nelle pagine delle modifiche per visualizzare le proprietà per la nuova selezione. Se non esistono proprietà che supportano le pagine delle proprietà per l'oggetto, la pagina delle proprietà è vuota.  
  
 Se sono selezionati più oggetti, la pagina delle proprietà consente di visualizzare l'intersezione di proprietà per tutti gli elementi selezionati. Se l'elemento selezionato non contiene le proprietà dipendenti dalla configurazione e **pagine delle proprietà** si fa clic sul pulsante sulla barra degli strumenti Esplora soluzioni, lo stato attivo passa alla finestra Proprietà. Per ulteriori informazioni relative alla selezione e alla finestra Proprietà, vedere [estensione di proprietà](../../extensibility/internals/extending-properties.md).  
  
 Se si modifica un valore in una pagina delle proprietà vengono visualizzate le proprietà per più oggetti, tutti i valori per gli oggetti vengono impostati per il nuovo valore anche se fossero inizialmente diversi e la pagina non è stata specificata quando sono visualizzate le proprietà di un singolo oggetto.  
  
 Esistono due tipi generali di **ProjectProperty pagine** alle finestre di dialogo disponibili in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Nel primo, per i progetti di Visual Basic, ad esempio, le pagine delle proprietà vengono visualizzati utilizzando un formato del campo, come illustrato nella schermata seguente. Nel secondo caso riportato più avanti in questa sezione, la proprietà host pagina una griglia di proprietà simile a quella disponibile nella finestra Proprietà.  
  
 ![Pagine delle proprietà di Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
La finestra di dialogo Pagine delle proprietà di progetto con la struttura di campo di formato e struttura ad albero  
  
 La struttura ad albero nella finestra di dialogo Pagine delle proprietà non viene compilata utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. L'ambiente, in base al nome di livello passato dal <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> le interfacce, lo compila.  
  
 Sono disponibili solo due categorie principali in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pagine delle proprietà:  
  
-   Proprietà comuni, che mostra informazioni indipendenti dalla configurazione per gli oggetti selezionati. Di conseguenza, quando è selezionata una le sottocategorie di proprietà comuni, le opzioni di configurazione, piattaforma e Configuration Manager nella parte superiore della finestra di dialogo non sono disponibili.  
  
-   Proprietà di configurazione, che contiene informazioni dipendenti dalla configurazione relative ai parametri di compilazione, debug e ottimizzazione per la soluzione o progetto.  
  
 Non è possibile creare le eventuali altre categorie di livello superiore, ma è possibile scegliere di non visualizzare uno o l'altro per l'implementazione di `IVsPropertyPage`. Se, ad esempio, non si dispone qualsiasi indipendenti dalla configurazione di proprietà da visualizzare per un oggetto, è possibile scegliere di non visualizzare la categoria di proprietà comuni. Per visualizzare le proprietà di comune se `ISpecifyPropertyPages` viene implementata dalla proprietà di configurazione e dell'oggetto dell'elemento quando si implementa `ISpecifyPropertyPages` nell'oggetto di configurazione (l'oggetto che implementa `IVsCfg`, `IVsProjectCfg`ed elementi correlati interfacce).  
  
 Ogni categoria visualizzato in una categoria principale rappresenta una pagina delle proprietà separate. Voci di categoria e sottocategoria disponibili nella finestra di dialogo sono determinate dall'implementazione di `ISpecifyPropertyPages` e `IVsPropertyPage`.  
  
 `IDispatch` gli oggetti per gli elementi nel contenitore di selezione che dispongono di proprietà da visualizzare nella proprietà pagine implementare `ISpecifyPropertyPages` per enumerare un elenco di ID di classe. Gli ID di classe vengono passati come variabili `ISpecifyPropertyPages` e vengono utilizzati per creare un'istanza delle pagine delle proprietà. L'elenco di ID di classe viene inoltre passato a `IVsPropertyPage` per creare la struttura ad albero a sinistra della finestra di dialogo. Le pagine delle proprietà, quindi passare informazioni eseguire il backup per il `IDispatch` oggetto che implementa `ISpecifyPropertyPages` e inserisce le informazioni per ogni pagina.  
  
 Le proprietà dell'oggetto Sfoglia vengono recuperate tramite `IDispatch` per ogni oggetto nel contenitore di selezione.  
  
 Implementazione di `Help::DisplayTopicFromF1Keyword` in VSPackage fornisce la funzionalità per il pulsante?.  
  
 Per ulteriori informazioni, vedere `IDispatch` e `ISpecifyPropertyPages`in MSDN library.  
  
 Il secondo tipo di pagine delle proprietà visualizzati negli host di esempi una forma di griglia delle proprietà, come illustrato nella schermata seguente.  
  
 ![Pagine delle proprietà di VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
Finestra di dialogo Pagine delle proprietà con la griglia delle proprietà  
  
 Le interfacce `IVSMDPropertyBrowser` e `IVSMDPropertyGrid` (dichiarato in vsmanaged.h) vengono utilizzati per creare e popolare la griglia delle proprietà all'interno di una finestra di dialogo o una finestra.  
  
 L'architettura di progetti è stato notevolmente modificato dalle versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. In particolare, la nozione di selezionare il progetto è attiva è stata modificata. In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], non vi è alcun concetto di un progetto attivo. Negli ambienti di sviluppo precedenti, il progetto attivo è stato il progetto che compilare e distribuire comandi sarebbe predefinito per indipendentemente dal contesto. A questo punto, la soluzione controlla e regola cui compilare e distribuire i comandi si applicano a progetti.  
  
 Che in precedenza era un progetto attivo viene acquisito in uno dei tre modi diversi:  
  
-   Il progetto di avvio  
  
     È possibile specificare uno o più progetti dalla pagina delle proprietà della soluzione che verrà avviata quando l'utente preme F5 o si sceglie di eseguire dal menu Compila. Questo procedimento funziona in modo analogo al vecchio progetto attivo nel senso che il relativo nome viene visualizzato in Esplora soluzioni con tipo di carattere grassetto.  
  
     È possibile recuperare il progetto di avvio come proprietà nel modello di automazione chiamando `DTE.Solution.SolutionBuild.StartupProjects`. In un pacchetto VSPackage, si chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> metodi. `IVsSolutionBuildManager` è disponibile come un servizio da `QueryService` su SID_SVsSolutionBuildManager. Per ulteriori informazioni, vedere [oggetto di configurazione di progetto](../../extensibility/internals/project-configuration-object.md) e [configurazione soluzione](../../extensibility/internals/solution-configuration.md).  
  
-   Configurazione di compilazione della soluzione attiva  
  
     [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con una configurazione soluzione attiva, disponibile nel modello di automazione mediante l'implementazione `DTE.Solution.SolutionBuild.ActiveConfiguration`. Una configurazione di soluzione è una raccolta che contiene una configurazione di progetto per ogni progetto nella soluzione (ogni progetto può disporre di più configurazioni, su più piattaforme, con nomi diversi). Per ulteriori informazioni relative alle pagine delle proprietà della soluzione, vedere [configurazione soluzione](../../extensibility/internals/solution-configuration.md).  
  
-   Progetto attualmente selezionato  
  
     Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> metodo per recuperare la gerarchia del progetto e l'elemento di progetto o gli elementi selezionati. Da DTE, si utilizzerebbe il `SelectedItems.SelectedItem.Project` e `SelectedItems.SelectedItem.ProjectItem` metodi. Esempio di codice sotto le intestazioni nel nucleo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] documenti.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)   
 [Oggetto di configurazione di progetto](../../extensibility/internals/project-configuration-object.md)   
 [Configurazione di soluzioni](../../extensibility/internals/solution-configuration.md)