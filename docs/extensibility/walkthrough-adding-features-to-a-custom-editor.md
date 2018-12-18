---
title: "Procedura dettagliata: Aggiunta di funzionalità a un Editor personalizzato | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f3c207b80686a66d9a06b8c50321b4dce2257ada
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>Procedura dettagliata: Aggiunta di funzionalità a un Editor personalizzato
Dopo aver creato un editor personalizzato, è possibile aggiungere ulteriori funzionalità a esso.  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>Per creare un editor per un pacchetto VSPackage  
  
1.  Creare un editor personalizzato utilizzando il modello di progetto di pacchetto di Visual Studio.  
  
     Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un Editor personalizzato](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Decidere se l'editor per supportare una singola visualizzazione o più visualizzazioni.  
  
     Un editor che supporta il **nuova finestra** comando o con visualizzazione form e visualizzazione di codice, richiede gli oggetti dati documento separato e oggetti di visualizzazione documento. In un editor che supporta una sola visualizzazione, l'oggetto dati del documento e l'oggetto visualizzazione del documento possono essere implementati nello stesso oggetto.  
  
     Per un esempio di più visualizzazioni, vedere [di supporto di più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md).  
  
3.  Implementare una factory dell'editor mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaccia.  
  
     Per ulteriori informazioni, vedere [factory Editor](../extensibility/editor-factories.md).  
  
4.  Decidere se si desidera che l'editor di utilizzare l'attivazione sul posto o semplificato di incorporamento per gestire la finestra di oggetto visualizzazione documento.  
  
     Una finestra dell'editor di incorporamento semplificato ospita una visualizzazione di documenti standard, mentre una finestra dell'editor di attivazione sul posto ospita un controllo ActiveX o un altro oggetto attivo come visualizzazione documento. Per ulteriori informazioni, vedere [incorporamento semplificato](../extensibility/simplified-embedding.md) e [attivazione sul posto](../extensibility/in-place-activation.md).  
  
5.  Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia per la gestione dei comandi.  
  
6.  Fornire la persistenza di documento e di risposta alle modifiche di file esterno effettuando le seguenti operazioni:  
  
    1.  Per mantenere il file, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> e <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> in oggetto dati del documento dell'editor.  
  
    2.  Per rispondere alle modifiche di file esterno, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> in oggetto dati del documento dell'editor.  
  
        > [!NOTE]
        >  Chiamare `QueryService` su <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> per ottenere un puntatore a `IVsFileChangeEx`.  
  
7.  Consente di coordinare gli eventi di modifica di documenti con controllo del codice sorgente. Per eseguire questa operazione:  
  
    1.  Ottenere un puntatore a `IVsQueryEditQuerySave2` chiamando `QueryService` su <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  Quando si verifica il primo evento di modifica, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metodo.  
  
         Chiede all'utente di estrarre il file se non si è già estratto. Assicurarsi di gestire una condizione di "file non estratto" per evitare errori  
  
    3.  Analogamente, prima di salvare il file, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> metodo.  
  
         Questo metodo richiede all'utente di salvare il file se non è stato salvato oppure se è stato modificato dopo l'ultimo salvataggio.  
  
8.  Abilitare il **proprietà** finestra per visualizzare le proprietà per il testo selezionato nell'editor. Per eseguire questa operazione:  
  
    1.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> selezione di testo ogni ora viene modificata, passando nell'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Chiamare `QueryService` su <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> servizio per ottenere un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Consentire agli utenti di trascinare gli elementi tra l'editor e **della casella degli strumenti**, o tra gli editor esterni (ad esempio Microsoft Word) e **della casella degli strumenti**. Per eseguire questa operazione:  
  
    1.  Implementare `IDropTarget` nell'editor per indicare all'IDE che l'editor è una destinazione di rilascio.  
  
    2.  Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interfaccia per la vista in modo l'editor è possibile abilitare e disabilitare gli elementi di **della casella degli strumenti**.  
  
    3.  Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> e chiamare `QueryService` su <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> servizio per ottenere un puntatore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> interfacce.  
  
         In questo modo il pacchetto VSPackage aggiungere nuovi elementi per il **della casella degli strumenti**.  
  
10. Se si decide le altre funzionalità facoltative per l'editor.  
  
    -   Se si desidera l'editor per supportare trovare e sostituire i comandi, implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Se si desidera utilizzare una finestra degli strumenti di struttura di documento nell'editor, implementare `IVsDocOutlineProvider`.  
  
    -   Se si desidera utilizzare una barra di stato nell'editor, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> e chiamare `QueryService` per <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> per ottenere un puntatore a `IVsStatusBar`.  
  
         Ad esempio, un editor può visualizzare riga / informazioni di colonna, la modalità di selezione (stream / casella) e modalità di inserimento (insert / sovrascrivere).  
  
    -   Se si desidera l'editor per supportare il `Undo` comando, il metodo consigliato consiste nell'utilizzare il modello di gestione di annullamento OLE. In alternativa, è possibile avere l'handle di editor la `Undo` comando direttamente.  
  
11. Creare informazioni, inclusi il GUID per il pacchetto VSPackage, i menu, l'editor e altre funzionalità del Registro di sistema.  
  
     Di seguito è un esempio di codice che si dovrà inserire nello script di file con estensione RGS per illustrare come registrare correttamente un editor generico.  
  
    ```  
    NoRemove Editors  
    {  
          ForceRemove {...guidEditor...} = s 'RTF Editor'  
          {  
             val Package = s '{...guidVsPackage...}'  
             ForceRemove Extensions  
             {  
                val rtf = d 50  
             }  
          }  
    }  
    NoRemove Menus  
    {  
          val {...guidVsPackage...} = s ',203,11'  
    }  
    ```  
  
12. Implementare il supporto della Guida sensibile al contesto.  
  
     In questo modo è possibile fornire supporto della Guida F1 e finestra Guida dinamica per gli elementi nell'editor. Per ulteriori informazioni, vedere [procedura: fornire contesto per gli editor](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Esporre un modello a oggetti da un editor di automazione mediante l'implementazione di `IDispatch` interfaccia.  
  
     Per ulteriori informazioni, vedere [che contribuiscono al modello di automazione](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Programmazione efficiente  
  
-   L'istanza dell'editor viene creato quando si chiama l'IDE di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo. Se l'editor supporta più viste, `CreateEditorInstance` vengono creati i dati del documento e gli oggetti di visualizzazione del documento. Se l'oggetto dati del documento è già aperto, un valore non null `punkDocDataExisting` valore viene passato a `IVsEditorFactory::CreateEditorInstance`. L'implementazione della factory dell'editor deve determinare se un oggetto dati del documento esistente è compatibile eseguendo una query per le interfacce appropriate su di esso. Per ulteriori informazioni, vedere [di supporto di più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md).  
  
-   Se si utilizza l'approccio di incorporamento semplificato, implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaccia.  
  
-   Se si decide di utilizzare l'attivazione sul posto, è possibile implementare le interfacce seguenti:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  Il `IOleInPlaceComponent` interfaccia viene utilizzata per evitare l'unione di menu OLE 2.  
  
     Il `IOleCommandTarget` implementazione gestisce i comandi, ad esempio **Taglia**, **copia**, e **Incolla**. Quando si implementa `IOleCommandTarget`, decidere se l'editor richiede il proprio file vsct per definire la propria struttura di menu comando o se è possibile implementare comandi standard definiti dalla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In genere, gli editor utilizzano estendono i menu dell'IDE e definiscono i propri barre degli strumenti. Tuttavia, spesso è necessario per un editor definire i proprio comandi specifici oltre all'utilizzo di set di comandi standard dell'IDE. A tale scopo, l'editor deve dichiarare i comandi standard utilizza e quindi definire qualsiasi nuovi comandi, menu di scelta rapida, menu di primo livello e le barre degli strumenti in un file con estensione vsct. Se si crea un'attivazione sul posto dell'editor, quindi implementare <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> e definire i menu e barre degli strumenti per l'editor in un file con estensione vsct anziché l'unione di menu OLE 2.  
  
-   Per evitare che il comando di menu affollare nell'interfaccia utente, utilizzare i comandi esistenti nell'IDE prima di realizzazione nuovi comandi. I comandi condivisi sono definiti in SharedCmdDef.vsct e ShellCmdDef.vsct. Questi file vengono installati per impostazione predefinita nella sottodirectory VisualStudioIntegration\Common\Inc del [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] installazione.  
  
-   `ISelectionContainer`è in grado di esprimere una o più selezioni. Ogni oggetto selezionato viene implementato come un `IDispatch` oggetto.  
  
-   L'IDE implementa `IOleUndoManager` come servizio accessibile da un <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> o come un oggetto che può essere creata un'istanza tramite <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Implementa l'editor di `IOleUndoUnit` interfaccia per ogni `Undo` azione.  
  
-   Esistono due posizioni un editor personalizzato è possibile esporre gli oggetti di automazione:  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## <a name="see-also"></a>Vedere anche  
 [Che contribuiscono al modello di automazione](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Procedura: fornire contesto per gli editor](../extensibility/how-to-provide-context-for-editors.md)