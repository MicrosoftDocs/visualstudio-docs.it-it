---
title: Sequenza di inizializzazione dei sottotipi di progetto | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: db259b7bc5f9935b229f4f6522ae14a4496f0e15
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="initialization-sequence-of-project-subtypes"></a>Sequenza di inizializzazione dei sottotipi di progetto
L'ambiente crea un progetto chiamando l'implementazione della factory del progetto di base <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. La costruzione di un sottotipo di progetto inizia quando l'ambiente determina che l'elenco GUID di tipo di progetto per l'estensione del file di progetto non è vuoto. L'estensione di file di progetto e il GUID di progetto specificare se il progetto è un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] tipo di progetto. Ad esempio, l'estensione vbproj e {F184B08F-C81C-45F6-A57F-5ABD9991F28F} identificare un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] progetto.  
  
## <a name="environments-initialization-of-project-subtypes"></a>Inizializzazione dell'ambiente dei sottotipi di progetto  
 La procedura seguente illustra in dettaglio la sequenza di inizializzazione per un sistema di progetto aggregato da diversi sottotipi di progetto.  
  
1.  L'ambiente chiama il progetto di base <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, mentre il progetto analizza il file di progetto viene rilevata non è il tipo di progetto aggregato GUID elenco `null`. Il progetto interrompe la creazione diretta di progetto.  
  
2.  Le chiamate di progetto `QueryService` su <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> servizio da creare mediante l'implementazione dell'ambiente di un sottotipo di progetto di <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> (metodo). All'interno di questo metodo l'ambiente effettua chiamate di funzione ricorsiva per le implementazioni di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` e <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> metodi mentre verifica l'elenco di progetto di tipo GUID, a partire dal sottotipo del progetto più esterno.  
  
     Di seguito in dettaglio i passaggi dell'inizializzazione.  
  
    1.  L'implementazione dell'ambiente del <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> chiamate al metodo ' HrCreateInnerProj ' ' (metodo) con la dichiarazione di funzione seguente:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
         Quando questa funzione viene chiamata per la prima volta, ovvero, per il sottotipo di progetto più esterna, i parametri `pOuter` e `pOwner` vengono passati come `null` e la funzione imposta il sottotipo del progetto più esterno `IUnknown` a `pOuter`.  
  
    2.  Successivamente l'ambiente chiama `HrCreateInnerProj` funzione con il secondo progetto GUID del tipo nell'elenco. Questo GUID corrisponde al sottotipo di progetto interna secondo l'esecuzione di istruzioni per il progetto di base nella sequenza di aggregazione.  
  
    3.  Il `pOuter` fa riferimento a questo punto il `IUnknown` del sottotipo di progetto più esterno, e `HrCreateInnerProj` chiama l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> seguita da una chiamata all'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. In <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> metodo si passa il controllo `IUnknown` del sottotipo di progetto più esterno, `pOuter`. Proprietà progetto (sottotipo di progetto interna) deve creare l'oggetto di progetto aggregato qui. Nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> si passa un puntatore all'implementazione del metodo di `IUnknown` del progetto interno da aggregare. Questi due metodi di creazione dell'oggetto di aggregazione e le implementazioni devono rispettare le regole di aggregazione COM per garantire che un sottotipo di progetto non finire che contiene un conteggio dei riferimenti a se stesso.  
  
    4.  `HrCreateInnerProj`chiama l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. In questo metodo, il sottotipo del progetto esegue le operazioni di inizializzazione. È possibile, ad esempio, registrare gli eventi della soluzione in <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.  
  
    5.  `HrCreateInnerProj`viene chiamato in modo ricorsivo fino a quando non viene raggiunto il GUID ultimo (il progetto di base) nell'elenco. Per ognuna di queste chiamate, vengono ripetuti i passaggi c e d. `pOuter`punta al sottotipo di progetto più esterno `IUnknown` per ogni livello di aggregazione.  
  
 Nell'esempio seguente viene illustrato il processo a livello di codice in una rappresentazione approssimativa del <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> il metodo viene implementato dall'ambiente. Il codice è solo un esempio; non è progettato per essere compilato e controllo degli errori di tutti è stato rimosso per maggiore chiarezza.  
  
## <a name="example"></a>Esempio  
  
### <a name="code"></a>Codice  
  
```  
HRESULT CreateAggregateProject  
(  
    LPCOLESTR lpstrGuids,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    REFIID iidProject,   
    void **ppvProject)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpunkProj;  
    CComPtr<IVsAggregatableProject> srpAggProject;  
    CComBSTR bstrGuids = lpstrGuids;  
    BOOL fCanceled = FALSE;  
    *ppvProject = NULL;  
  
    HrCreateInnerProj(  
         bstrGuids, NULL, NULL, pszFilename, pszLocation,   
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);  
    srpunkProj->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggProject));  
    srpAggProject->OnAggregationComplete();  
    srpunkProj->QueryInterface(iidProject, ppvProject);  
}  
  
HRESULT HrCreateInnerProj  
(  
    WCHAR *pwszGuids,   
    IUnknown *pOuter,   
    IVsAggregatableProject *pOwner,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    IUnknown **ppInner,   
    BOOL *pfCanceled  
)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpInner;  
    CComPtr<IVsAggregatableProject> srpAggInner;  
    CComPtr<IVsProjectFactory> srpProjectFactory;  
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;  
    GUID guid = GUID_NULL;  
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');  
    WCHAR wszText[_MAX_PATH+150] = L"";  
  
    if (pwszNextGuids)  
    {  
        *pwszNextGuids++ = 0;  
    }  
  
    CLSIDFromString(pwszGuids, &guid);  
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(  
        guid, &srpProjectFactory);  
    srpProjectFactory->QueryInterface(  
        IID_IVsAggregatableProjectFactory,   
        (void **)&srpAggPF);  
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);  
    srpInner->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggInner);  
  
    if (pOwner)  
    {  
        IfFailGo(pOwner->SetInnerProject(srpInner));  
    }  
  
    if (pwszNextGuids)  
    {  
        CComPtr<IUnknown> srpNextInner;  
        HrCreateInnerProj(  
            pwszNextGuids, pOuter ? pOuter : srpInner,   
            srpAggInner, pszFilename, pszLocation, pszName,   
            grfCreateFlags, &srpNextInner, pfCanceled);  
    }  
  
    return srpAggInner->InitializeForOuter(  
        pszFilename, pszLocation, pszName, grfCreateFlags,   
        IID_IUnknown, (void **)ppInner, pfCanceled);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)