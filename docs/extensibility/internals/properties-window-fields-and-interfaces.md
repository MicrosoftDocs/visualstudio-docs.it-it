---
title: Campi di finestra delle proprietà e le interfacce | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a286d8cc782305b746789f56af431d7a62f8e2fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="properties-window-fields-and-interfaces"></a>Le interfacce e i campi di proprietà finestra
Il modello per la selezione determinare quali informazioni vengono visualizzate nel **proprietà** finestra è basata sulla finestra che ha lo stato attivo nell'IDE. Ogni finestra e un oggetto all'interno della finestra selezionata, può includere il relativo oggetto di contesto di selezione inserito nel contesto di selezione globale. L'ambiente aggiorna il contesto di selezione globale con i valori di una cornice di finestra quando tale finestra ha lo stato attivo. Quando viene modificato lo stato attivo, pertanto, non il contesto della selezione.  
  
## <a name="tracking-selection-in-the-ide"></a>Traccia della selezione nell'IDE  
 La cornice della finestra o un sito, dall'IDE, di proprietà è un servizio denominato <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. I passaggi seguenti mostrano come una modifica in una selezione, causata dall'utente modificando lo stato attivo a un'altra finestra aperta o selezionando un elemento di progetto diverso in **Esplora**, viene implementato per modificare il contenuto visualizzato nella finestra di  **Proprietà** finestra.  
  
1.  L'oggetto creato dal pacchetto VSPackage che viene inserito nelle chiamate finestra selezionata <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> avere <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> richiamare <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2.  Il contenitore di selezione, fornito dalla finestra selezionata, consente di creare il proprio <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> oggetto. Quando viene modificata la selezione, il pacchetto VSPackage chiama <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> per notificare tutti i listener nell'ambiente, inclusi il **proprietà** finestra, della modifica. Fornisce inoltre l'accesso alle informazioni di gerarchia ed elementi correlate per la nuova selezione.  
  
3.  La chiamata <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> e passando gli elementi della gerarchia selezionata nel `VSHPROPID_BrowseObject` parametro consente di popolare il <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> oggetto.  
  
4.  Oggetto derivato dalla classe di [interfaccia IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) viene restituito per <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> per l'elemento richiesto e l'ambiente esegue il wrapping in un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (vedere il passaggio seguente). Se la chiamata non riesce, l'ambiente rende una seconda chiamata a `IVsHierarchy::GetProperty`, passandogli il contenitore di selezione <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> che forniscono la gerarchia o più elementi.  
  
     Il progetto non è possibile creare VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> perché la finestra di ambiente fornito dal pacchetto VSPackage che implementa (ad esempio, **Esplora**) costruisce <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> per suo conto.  
  
5.  L'ambiente chiama i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> per ottenere gli oggetti in base il `IDispatch` interfaccia per riempire il **proprietà** finestra.  
  
 Quando un valore di **proprietà** finestra viene modificata, i pacchetti VSPackage implementare `IVsTrackSelectionEx::OnElementValueChangeEx` e `IVsTrackSelectionEx::OnSelectionChangeEx` per segnalare la modifica il valore dell'elemento. L'ambiente chiama quindi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> per mantenere le informazioni visualizzate nel **proprietà** finestra sincronizzati con i valori delle proprietà. Per ulteriori informazioni, vedere [aggiornare i valori delle proprietà nella finestra proprietà](#updating-property-values-in-the-properties-window).  
  
 Oltre a selezionare un altro elemento di progetto **Esplora** per visualizzare le proprietà correlate a tale elemento, è anche possibile scegliere un oggetto diverso da all'interno di una finestra del documento utilizzando l'elenco a discesa disponibile nel **Proprietà** finestra. Per ulteriori informazioni, vedere [elenco di oggetti finestra delle proprietà](../../extensibility/internals/properties-window-object-list.md).  
  
 È possibile modificare il modo in cui vengono visualizzate informazioni di **proprietà** griglia della finestra da in ordine alfabetico in categorico, e, se disponibile, è anche possibile aprire una pagina delle proprietà per un oggetto selezionato facendo clic sui pulsanti appropriati nel  **Proprietà** finestra. Per ulteriori informazioni, vedere [pulsanti della finestra proprietà](../../extensibility/internals/properties-window-buttons.md) e [pagine delle proprietà](../../extensibility/internals/property-pages.md).  
  
 Infine, la parte inferiore del **proprietà** finestra contiene inoltre una descrizione del campo selezionato nel **proprietà** della griglia della finestra. Per ulteriori informazioni, vedere [il recupero delle descrizioni dei campi dalla finestra delle proprietà](#getting-field-descriptions-from-the-properties-window).  
  
## <a name="updating-property-values-in-the-properties-window"></a> L'aggiornamento dei valori di proprietà nella finestra proprietà
Esistono due modi per mantenere sincronizzata la finestra **Proprietà** con le modifiche dei valori della proprietà. Il primo consiste nel chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia, che fornisce l'accesso alle funzionalità di windowing di base, inclusi l'accesso e creazione di finestre di documenti e degli strumenti disponibili nell'ambiente. I passaggi seguenti descrivono il processo di sincronizzazione.  
  
### <a name="updating-property-values-using-ivsuishell"></a>Aggiornamento dei valori di proprietà tramite IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Per aggiornare i valori di proprietà tramite l'interfaccia IVsUIShell  
  
1.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (tramite <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> servizio) ogni volta che VSPackage, progetti o editor devono creare o enumerare finestre di documento o degli strumenti.  
  
2.  Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> per mantenere il **proprietà** finestra sincronizzato con le modifiche alle proprietà per un progetto (o qualsiasi altro oggetto selezionato visualizzato tramite il **proprietà** finestra) senza implementare <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> e la generazione di <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> eventi.  
  
3.  Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> per stabilire e disabilitare, rispettivamente, la notifica client degli eventi di gerarchia senza richiedere la gerarchia per implementare <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
### <a name="updating-property-values-using-iconnection"></a>Aggiornamento dei valori di proprietà tramite IConnection  
 Il secondo modo per mantenere sincronizzata la finestra **Proprietà** con le modifiche dei valori della proprietà consiste nell'implementare `IConnection` sull'oggetto collegabile per indicare l'esistenza delle interfacce in uscita. Se si desidera localizzare il nome della proprietà, derivare l'oggetto da <xref:System.ComponentModel.ICustomTypeDescriptor>. Il <xref:System.ComponentModel.ICustomTypeDescriptor> implementazione può modificare i descrittori di proprietà restituisce e cambiare il nome di una proprietà. Per localizzare la descrizione, creare un attributo che deriva da <xref:System.ComponentModel.DescriptionAttribute> ed eseguire l'override della proprietà Description.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Considerazioni relative all'implementazione dell'interfaccia IConnection  
  
1.  `IConnection` fornisce l'accesso a un oggetto secondario enumeratore con il <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfaccia. Fornisce inoltre l'accesso a tutti oggetti punto di connessione secondaria, ciascuno dei quali implementa il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaccia.  
  
2.  Qualsiasi oggetto è responsabile dell'implementazione un' <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> evento. Nella finestra **Proprietà** verrà indicato l'evento impostato tramite `IConnection`.  
  
3.  Un punto di connessione controlla il numero di connessioni (uno o più) consente l'implementazione del <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Può restituire un punto di connessione che consente una sola interfaccia <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> dal <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> metodo.  
  
4.  Un client può chiamare il `IConnection` interfaccia per ottenere l'accesso a un oggetto secondario enumeratore con il <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfaccia. Il <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfaccia può quindi essere chiamata per enumerare i punti di connessione per ogni ID (IID) dell'interfaccia in uscita.  
  
5.  `IConnection` può anche essere chiamato per ottenere l'accesso agli oggetti secondari di punto di connessione con il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaccia per ogni IID in uscita. Tramite il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaccia, un client avvia o termina un ciclo consultivo con l'oggetto collegabile e la sincronizzazione del client. Il client può chiamare anche il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaccia per ottenere un oggetto enumeratore con il <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> interfaccia per enumerare le connessioni che a conoscenza.  
  
## <a name="getting-field-descriptions-from-the-properties-window"></a> Descrizioni dei campi dalla finestra delle proprietà
Nella parte inferiore della finestra **Proprietà** è disponibile un'area per la descrizione che visualizza informazioni relative al campo della proprietà selezionata. Questa funzionalità è attivata per impostazione predefinita. Se si vuole nascondere il campo della descrizione, fare clic con il pulsante destro del mouse nella finestra **Proprietà** e fare clic su **Descrizione**. In questo modo viene anche rimosso il segno di spunta accanto al titolo **Descrizione** nella finestra del menu. È possibile visualizzare di nuovo il campo con la stessa procedura per riattivare il campo **Descrizione** .  
  
 Le informazioni nel campo Descrizione provengano da <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Per ogni metodo, interfaccia, coclasse e così via può esistere un attributo `helpstring` non localizzato nella libreria dei tipi. Il **proprietà** finestra Recupera la stringa da <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### <a name="to-specify-localized-help-strings"></a>Per specificare stringhe della Guida localizzate  
  
1.  Aggiungere l'attributo `helpstringdll` all'istruzione library nella libreria dei tipi (`typelib`).  
  
    > [!NOTE]
    >  Questo passaggio è facoltativo se la libreria dei tipi è inclusa in un file di libreria di oggetti (con estensione olb).  
  
2.  Specificare gli attributi `helpstringcontext` per le stringhe. È anche possibile specificare attributi `helpstring` .  
  
     Questi attributi sono distinti dagli attributi `helpfile` e `helpcontext` , contenuti negli argomenti della Guida nei file effettivi con estensione chm.  
  
 Per recuperare le informazioni di descrizione da visualizzare per il nome della proprietà evidenziata la **proprietà** finestra chiamate <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> per la proprietà che è selezionata, specificare l'oggetto desiderato `lcid` attributo per il stringa di output. Internamente, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> trova il file DLL specificato nel `helpstringdll` attributo e chiama `DLLGetDocumentation` su tale file con estensione dll con il contesto specificato e `lcid` attributo.  
  
 La firma e l'implementazione di `DLLGetDocumentation` sono:  
  
```cpp  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 La funzione `DLLGetDocumentation` deve essere un'esportazione definita nel file con estensione def per la DLL.  
  
 Internamente, viene creato un file con estensione olb che è in effetti una DLL. Questa DLL contiene una sola risorsa, il file della libreria dei tipi (con estensione tlb) e una funzione esportata, `DLLGetDocumentation`.  
  
 Nel caso dei file con estensione olb, l'attributo `helpstringdll` è facoltativo perché si tratta dello stesso file che contiene il file con estensione tlb.  
  
 Per recuperare le stringhe da visualizzare nel riquadro **Descrizione** , quindi, è necessario come minimo specificare l'attributo `helpstring` nella libreria dei tipi. Se si vuole localizzare le stringhe, è necessario specificare l'attributo facoltativo `helpstringdll` e l'attributo obbligatorio `helpstringcontext` , quindi implementare `DLLGetDocumentation`.  
  
 Non è necessario implementare altre interfacce quando si recuperano le informazioni localizzate tramite l'attributo `helpstringcontext` dell'istruzione IDL e `DLLGetDocumentation`.  
  
 Un altro modo per ottenere il nome localizzato e la descrizione di una proprietà è implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Per ulteriori informazioni sull'implementazione di questo metodo, vedere [campi finestra delle proprietà e le interfacce](../../extensibility/internals/properties-window-fields-and-interfaces.md).  

## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)