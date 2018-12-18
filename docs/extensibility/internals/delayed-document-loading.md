---
title: Documento caricamento ritardato | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc10d7807633433b38fa8587d41c2ac3c0273ebe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="delayed-document-loading"></a>Documento caricamento ritardato
Quando un utente riapre una soluzione di Visual Studio, è possibile che la maggior parte dei documenti associati non vengono caricata immediatamente. La cornice della finestra documento viene creata in uno stato in sospeso inizializzazione e un documento di segnaposto (denominato frame dello stub) viene inserito nel documento di tabella in esecuzione (RDT).  
  
 L'estensione potrebbe documenti del progetto da caricare inutilmente eseguendo una query di elementi nei documenti prima che vengano caricati. Ciò può aumentare il footprint di memoria globale per Visual Studio.  
  
## <a name="document-loading"></a>Caricamento di documenti  
 Il frame di stub e il documento sono completamente inizializzati quando l'utente accede al documento, ad esempio, selezionare la scheda della cornice della finestra. Il documento può inoltre essere inizializzato da un'estensione che richiede i dati del documento, l'accesso di RDT direttamente per acquisire i dati del documento o accede indirettamente il RDT effettuando una delle seguenti chiamate:  
  
-   La cornice della finestra show (metodo): <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
-   La cornice della finestra metodo GetProperty <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> in qualsiasi delle proprietà seguenti:  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 Se l'estensione utilizza il codice gestito, non è necessario chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> a meno che non si è certi che il documento non è nello stato in sospeso inizializzazione o si desidera che il documento sia completamente inizializzata... Infatti, questo metodo restituisce sempre il documento oggetto dati, creandolo se necessario. In alternativa, è necessario chiamare uno dei metodi sull'interfaccia IVsRunningDocumentTable4.  
  
 Se l'estensione Usa C++, è possibile passare `null` per i parametri non desiderate.  
  
 È possibile evitare il caricamento di documenti non necessari chiamando uno dei metodi seguenti prima di richiedere le proprietà rilevanti: prima di inserire altre proprietà.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Questo metodo restituisce un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> oggetto che include un valore per <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> se il documento non è ancora stato inizializzato.  
  
 Per sapere quando è stato caricato un documento tramite la sottoscrizione all'evento RDT che viene generato quando un documento è completamente inizializzato. Esistono due possibilità:  
  
-   Se il sink di evento implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, è possibile sottoscrivere <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
-   In caso contrario, è possibile sottoscrivere <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
 Di seguito è riportato uno scenario di accesso del ipotetica documento. Visual Studio estensione da visualizzare alcune informazioni sui documenti aperti, ad esempio la modifica è bloccare conteggio e qualcosa i dati del documento. Enumera i documenti nel RDT utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, quindi chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> per ogni documento per recuperare i dati di conteggio e documento di blocco modifica. Se il documento è nello stato in sospeso inizializzazione, che richiede i dati del documento rende inutilmente da inizializzare.  
  
 Un modo più efficace di procedere consiste nell'usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> per ottenere il conteggio dei blocchi di modifica e quindi usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> per determinare se il documento è stato inizializzato. Se non si include il flag <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, il documento è già stato inizializzato e la richiesta con i dati del documento <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> non determina le operazioni di inizializzazione non necessari. Se si include il flag <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, l'estensione deve evitare di richiedere i dati del documento fino a quando non viene inizializzato il documento. Questa condizione può essere rilevata nel gestore dell'evento OnAfterAttributeChange(Ex).  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Test di estensioni per vedere se forzano l'inizializzazione  
 Non vi è alcun riferimento visivo per indicare se un documento è stato inizializzato, pertanto può essere difficile sapere se l'estensione sta forzando l'inizializzazione. È possibile impostare una chiave del Registro di sistema che semplifica la verifica, perché altrimenti il titolo di ogni documento che non è completamente inizializzato per il testo `[Stub]` nel titolo.  
  
 In **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]**, impostare **StubTabTitleFormatString** a **{0} [Stub]**.