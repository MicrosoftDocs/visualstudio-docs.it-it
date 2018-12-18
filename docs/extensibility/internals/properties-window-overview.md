---
title: Panoramica della finestra proprietà | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e255795a52064723477eda4e1aca532adedb6be1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="properties-window-overview"></a>Panoramica della finestra Proprietà
Il **proprietà** finestra consente di visualizzare le proprietà di oggetti selezionati nei due tipi principali di windows disponibile nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE). Questi due tipi di windows sono:  
  
-   Finestre degli strumenti, ad esempio Esplora soluzioni, Visualizzazione classi e oggetti browser  
  
-   Finestre di documento che contiene tali editor e finestre di progettazione come finestra di progettazione di form, editor XML, editor HTML  
  
## <a name="using-the-properties-window"></a>Utilizzando la finestra proprietà  
 Il **proprietà** finestra vengono visualizzate le proprietà di uno o più elementi selezionati. Se sono selezionati più elementi, viene visualizzato l'intersezione di tutte le proprietà per tutti gli oggetti selezionati.  
  
 Eventi correlati a un oggetto selezionato in una finestra di progettazione di form o un editor HTML utilizzando metadati COM+ vengono visualizzati nel **proprietà** finestra. Ad esempio, è possibile selezionare un pulsante e visualizzare gli eventi associati, ad esempio un `OnClick` evento, che può essere collegato a tale pulsante.  
  
 Gli eventi visualizzati nel **proprietà** finestra vengono utilizzati principalmente con gli oggetti associati al codice. Se si sta modificando un formato di file che non vengono eseguite operazioni con il codice, non si desidera disporre di tutti gli eventi. Gli eventi vengono visualizzati solo nel **proprietà** finestra quando è presente un'associazione tra l'esecuzione di codice e alcuni eventi associati a oggetti specifici. Un esempio sarebbe code-behind di un oggetto selezionato viene eseguito quando viene attivato l'oggetto.  
  
 La tabella seguente elenca le interfacce principali utilizzate dal **proprietà** finestra.  
  
|Nome dell'interfaccia|Descrizione|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Fornisce un elenco di categorie per il **proprietà** finestra ed esegue il mapping a una categoria di ogni proprietà.|  
|[Interfaccia IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)|Espone metodi e proprietà per la programmazione di strumenti e altre applicazioni che supportano l'automazione di un oggetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Sono disponibili i pulsanti con puntini di sospensione (…) denominati *generatori* che aprire finestre di dialogo modali implementate dall'oggetto stesso. Utilizzato quando un valore non è tipizzato con facilità dall'utente in un campo di testo. Ad esempio, potrebbe essere consente di aprire un selettore di colore che determina il valore RGB per l'utente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Fornisce l'accesso agli oggetti utilizzati per aggiornare le informazioni visualizzate nel **proprietà** finestra. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> è implementato dal VSPackage per ogni finestra che contiene oggetti selezionabili con le proprietà correlate da visualizzare.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Fornisce informazioni sul tipo di oggetto, ad esempio i metodi di un'interfaccia e i campi di una struttura.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Consente i pacchetti VSPackage per ricevere la notifica degli eventi di selezione e recuperare le informazioni sulla gerarchia del progetto corrente, elemento, valore dell'elemento e contesto del comando dell'interfaccia utente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Fornisce l'ambiente con accesso a più selezioni.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Utilizzato per fornire nomi localizzati in alcune proprietà visualizzate nel **proprietà** finestra.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifica a VSPackage registrati di modifiche alla selezione corrente, un valore dell'elemento o un contesto di comando dell'interfaccia utente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Notifica all'ambiente di una modifica nella selezione corrente e fornisce l'accesso alle informazioni di gerarchia e l'elemento riguardanti la nuova selezione.|  
  
 Per ulteriori informazioni su `IDispatch`, vedere MSDN library.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)   
 [Campi e interfacce della finestra Proprietà](../../extensibility/internals/properties-window-fields-and-interfaces.md)