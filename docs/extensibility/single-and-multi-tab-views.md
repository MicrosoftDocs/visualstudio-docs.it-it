---
title: Visualizzazioni singole e multi-scheda | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f20e5d251d8d6ef31289fb1b9ee8b9420ff9146a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="single-and-multi-tab-views"></a>Singole e multi-scheda viste
Un editor è possibile creare diversi tipi di viste. Un esempio è una finestra dell'editor di codice, un altro è una finestra di progettazione del form.  
  
 Una visualizzazione a schede è una vista che è presenti più schede. Ad esempio, l'editor HTML è disponibili due schede nella parte inferiore: **progettazione** e **origine**, ognuna una vista logica. Visualizzazione Progettazione consente di visualizzare una pagina web, mentre l'altro consente di visualizzare il codice HTML che include la pagina web.  
  
## <a name="accessing-physical-views"></a>L'accesso a visualizzazioni fisiche  
 Le visualizzazioni fisiche ospitano gli oggetti di visualizzazione di documenti, ognuno dei quali rappresenta una visualizzazione dei dati nel buffer, ad esempio di codice o un form. Di conseguenza, ogni oggetto visualizzazione del documento dispone di una visualizzazione fisica (identificato da un elemento noto come una stringa di visualizzazione fisica) e in genere una singola visualizzazione logica.  
  
 In alcuni casi, tuttavia, una visualizzazione fisica può avere due o più visualizzazioni logiche. Alcuni esempi sono un editor che dispone di una finestra divisa con viste side-by-side o una finestra di progettazione di form che dispone di una visualizzazione grafica/progettazione e una codice-behind-di-visualizzazione form.  
  
 Per attivare l'editor accedere a tutte le visualizzazioni fisiche disponibili, è necessario creare una stringa di visualizzazione fisica univoco per ogni tipo di oggetto visualizzazione del documento che è possibile creare il factory editor. Ad esempio, il [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] factory editor può creare documento gli oggetti di visualizzazione per una finestra del codice e una finestra di progettazione del form.  
  
## <a name="creating-multi-tabbed-views"></a>Creazione di viste a schede  
 Se un oggetto visualizzazione del documento deve essere associato a una visualizzazione fisica tramite una stringa di visualizzazione fisica univoco, è possibile inserire più schede all'interno della visualizzazione fisica per attivare la visualizzazione dei dati in modi diversi. In questa configurazione di più schede, tutte le schede sono associate con la stessa stringa di visualizzazione fisica, ma ogni scheda viene fornita una vista logica diversi GUID.  
  
 Per creare una visualizzazione a schede per un editor, implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> interfaccia e quindi associare una vista logica diversi GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) con ogni scheda è creare.  
  
 L'editor di Visual Studio HTML è un esempio di un editor con una visualizzazione di multi-scheda. Ha **progettazione** e **origine** schede. A tale scopo, è associata a ogni scheda, una vista logica diversa `LOGICALVIEWID_TextView` per il **progettazione** scheda e `LOGICALVIEWID_Code` per il **origine** scheda.  
  
 Specificando una vista logica appropriata, un pacchetto VSPackage può accedere alla visualizzazione che corrisponde a uno scopo specifico, ad esempio si progetta un modulo, la modifica del codice o il debug di codice. Tuttavia, una delle finestre deve essere identificata dalla stringa NULL e deve corrispondere alla vista logica primaria (`LOGVIEWID_Primary`).  
  
 Nella tabella seguente sono elencati i valori di visualizzazione logica disponibile e il relativo utilizzo.  
  
|GUID LOGVIEWID|Utilizzo consigliato|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Visualizzazione predefinita o primario di factory dell'editor.<br /><br /> Tutte le factory editor devono supportare questo valore. Questa vista è necessario utilizzare la stringa NULL come stringa di visualizzazione fisica. A questo valore, è necessario impostare almeno una vista logica.|  
|`LOGVIEWID_Debugging`|Visualizzazione di debug. In genere, `LOGVIEWID_Debugging` esegue il mapping alla stessa vista come `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Visualizzazione avviata per il **Visualizza codice** comando.|  
|`LOGVIEWID_Designer`|Visualizzazione avviata per il **Visualizza modulo** comando.|  
|`LOGVIEWID_TextView`|Visualizzazione dell'editor di testo. Si tratta della visualizzazione che restituisce <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, da cui è possibile accedere a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Richiede all'utente di scegliere quale visualizzazione per usare.|  
|`LOGVIEWID_ProjectSpecificEditor`|Passato per il **Apri con** finestra di dialogo<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Quando l'utente sceglie la voce "(editor predefinito progetto)".|  
  
 Anche se la vista logica GUID sono estendibili, è possibile utilizzare solo i GUID di visualizzazione logica definiti nel pacchetto VSPackage.  
  
 Al momento della chiusura, Visual Studio consente di mantenere il GUID del factory dell'editor e le stringhe di visualizzazione fisica associate alla finestra di documento in modo che può essere utilizzato per aprire nuovamente le finestre di documento quando la soluzione viene riaperto. Solo le finestre che risultano aperte al momento della chiusura di una soluzione vengono rese persistenti nel file di soluzione (con estensione suo). Questi valori corrispondono al `VSFPROPID_guidEditorType` e `VSFPROPID_pszPhysicalView` valori passati il `propid` parametro il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> (metodo).  
  
## <a name="example"></a>Esempio  
 Questo frammento viene illustrato come la <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> oggetto viene utilizzato per accedere a una vista che implementa `IVsCodeWindow`. In questo caso, il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> servizio viene utilizzato per chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> e richiesta `LOGVIEWID_TextView`, quale ottiene un puntatore a una cornice di finestra. Un puntatore all'oggetto documento view viene ottenuto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> e specificando un valore di `VSFPROPID_DocView`. Dall'oggetto visualizzazione documento, `QueryInterface` viene chiamato per `IVsCodeWindow`. La previsione è in questo caso che viene restituito un editor di testo e pertanto l'oggetto visualizzazione del documento restituito nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodo è una finestra del codice.  
  
```cpp  
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)  
{  
  HRESULT hr;  
  if (NULL == szFile || !*szFile)  
    return E_INVALIDARG;  
  
  if (iLine == -1L)  
    return S_FALSE;  
  
  VSITEMID                  itemid;  
  VARIANT                   var;  
  RECT                      rc;  
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;  
  IVsCodeWindow *           pCodeWin    = NULL;  
  IVsTextView *             pTextView   = NULL;  
  IVsUIHierarchy *          pHierarchy  = NULL;  
  IVsWindowFrame *          pFrame      = NULL;  
  IUnknown *                pUnk        = NULL;  
  IVsHighlight *            pHighlight  = NULL;  
  
  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));  
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));  
  pFrame->Show();  
  VariantInit(&var);  
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));  
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }  
  pUnk = V_UNKNOWN(&var);  
  if (NULL != pUnk)  
  {  
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));  
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||  
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )  
    {  
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);  
      // uncover selection  
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));  
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));  
      UncoverSelectionRect(&rc);  
    }  
  }  
  
Error:  
  CLEARINTERFACE(pHighlight);  
  CLEARINTERFACE(pTextView);  
  CLEARINTERFACE(pCodeWin);  
  CLEARINTERFACE(pUnk);  
  CLEARINTERFACE(pFrame);  
  CLEARINTERFACE(pOpenDoc);  
  CLEARINTERFACE(pHierarchy);  
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);  
  return hr;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Supporta più viste di documento](../extensibility/supporting-multiple-document-views.md)   
 [Procedura: collegare viste per documentare i dati](../extensibility/how-to-attach-views-to-document-data.md)   
 [Creazione di finestre di progettazione ed editor personalizzati](../extensibility/creating-custom-editors-and-designers.md)