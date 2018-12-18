---
title: Adattamento del codice Legacy all'Editor | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e90a0f8ba27199e3837c59cd7980f027d0485a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="adapting-legacy-code-to-the-editor"></a>Adattamento del codice Legacy nell'editor
Editor di Visual Studio ha molte funzionalità che è possibile accedere da componenti di codice esistenti. Le istruzioni seguenti viene illustrato come adattare il componente non MEF, ad esempio, un VSPackage, utilizzare la funzionalità di editor. Le istruzioni mostrano inoltre come utilizzare le schede per recuperare i servizi dell'editor di codice gestito e gestito.  
  
## <a name="editor-adapters"></a>Schede editor  
 Schede editor o shim, sono wrapper per gli oggetti di editor che espongono anche le classi e le interfacce di <xref:Microsoft.VisualStudio.TextManager.Interop> API. È possibile utilizzare le schede per lo spostamento tra i servizi non di editor, ad esempio, i comandi della shell di Visual Studio e i servizi di editor. (Si tratta come l'editor è attualmente ospitato in Visual Studio). Schede anche abilitare legacy estensioni del servizio di editor e della lingua di funzionare correttamente in Visual Studio.  
  
## <a name="using-editor-adapters"></a>Utilizzo di adattatori di Editor  
 Il <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> fornisce metodi che passa tra le nuove interfacce di editor e le interfacce legacy, nonché metodi che creano schede.  
  
 Se si utilizza questo servizio in un componente MEF, è possibile importare il servizio come indicato di seguito.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Se si desidera utilizzare questo servizio in un componente non MEF, seguire le istruzioni nella sezione "Utilizzando Visual Studio Editor servizi in un Non-componente MEF" più avanti in questo argomento.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>Il passaggio tra la nuova API di Editor e l'API Legacy  
 Utilizzare i metodi seguenti per passare un oggetto editor e un'interfaccia legacy.  
  
|Metodo|Conversione|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Converte un <xref:Microsoft.VisualStudio.Text.ITextBuffer> per un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Converte un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> per un <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Converte un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> per un <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Converte un <xref:Microsoft.VisualStudio.Text.Editor.ITextView> per un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Converte un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## <a name="creating-adapters"></a>Creazione di adattatori  
 Utilizzare i metodi seguenti per creare adattatori per le interfacce legacy.  
  
|Metodo|Conversione|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> specificato <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per un <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Creazione di adattatori nel codice non gestito  
 Tutte le classi di adapter registrate per essere locale condiviso che è possibile creare e può essere creata un'istanza utilizzando il `VsLocalCreateInstance()` (funzione).  
  
 Tutte le schede vengono create utilizzando il GUID che sono definiti nel file vsshlids.h il... Cartella \VisualStudioIntegration\Common\Inc\ dell'installazione di Visual Studio SDK. Per creare un'istanza di VsTextBufferAdapter, utilizzare il codice seguente.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>Creazione di adattatori nel codice gestito  
 Nel codice gestito, è possibile creare condiviso gli adapter nello stesso modo come quello descritto per codice non gestito. È inoltre possibile utilizzare un servizio MEF che consente di creare e interagire con gli adapter. Questa modalità di recupero di un adapter consente un controllo più accurato rispetto a quanto disponibile quando si crea condiviso.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>Per creare un adattatore per IVsTextView  
  
1.  Aggiungere un riferimento a Microsoft.VisualStudio.Editor.dll. Assicurarsi che `CopyLocal` è impostato su `false`.  
  
2.  Creare un'istanza di <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, come indicato di seguito.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3.  Chiamare il metodo `CreateX()`.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>Con l'Editor di Visual Studio direttamente dal codice non gestito  
 Lo spazio dei nomi Microsoft.VisualStudio.Platform.VSEditor e lo spazio dei nomi Microsoft.VisualStudio.Platform.VSEditor.Interop esporre interfacce COM-callable come interfacce IVx *. Ad esempio, l'interfaccia Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer è la versione COM del <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaccia. Dal `IVxTextBuffer`, ottenere l'accesso agli snapshot di buffer, modificare il buffer, ascolto degli eventi di modifica testo nel buffer e creare punti di rilevamento e intervalli. I passaggi seguenti viene illustrato come accedere a un `IVxTextBuffer` da un `IVsTextBuffer`.  
  
#### <a name="to-get-an-ivxtextbuffer"></a>Per ottenere un oggetto IVxTextBuffer  
  
1.  Le definizioni per le interfacce IVx * sono nel file VSEditor.h il... Cartella \VisualStudioIntegration\Common\Inc\ dell'installazione di Visual Studio SDK.  
  
2.  Il codice seguente crea un'istanza di un buffer di testo usando il `IVsUserData->GetData()` metodo. Nel codice seguente, `pData` è un puntatore a un `IVsUserData` oggetto.  
  
    ```  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>Utilizzo di servizi di Editor di Visual Studio in un componente Non MEF  
 Se si dispone di un componente esistente di codice gestito che non utilizza MEF e si desidera utilizzare i servizi dell'editor di Visual Studio, è necessario aggiungere un riferimento all'assembly che contiene il ComponentModelHost VSPackage e ottenere il relativo servizio SComponentModel.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Per utilizzare i componenti dell'editor di Visual Studio da un componente non MEF  
  
1.  Aggiungere un riferimento all'assembly Microsoft.VisualStudio.ComponentModelHost.dll nel... \Common7\IDE\ cartella di installazione di Visual Studio. Assicurarsi che `CopyLocal` è impostato su `false`.  
  
2.  Aggiungere una privata `IComponentModel` membro alla classe in cui si desidera utilizzare i servizi di editor di Visual Studio, come indicato di seguito.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3.  Creare un'istanza al modello del componente nel metodo di inizializzazione per il componente.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4.  Successivamente, è possibile ottenere uno qualsiasi dei servizi di editor di Visual Studio mediante la chiamata di `IComponentModel.GetService<T>()` metodo per il servizio desiderato.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```