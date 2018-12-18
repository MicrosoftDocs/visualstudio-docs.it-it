---
title: "Tramite assembly di interoperabilità di Visual Studio | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: "33"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 98d579755190eaf51448ef2b1b855c087bcad358
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="using-visual-studio-interop-assemblies"></a>Tramite assembly di interoperabilità di Visual Studio
Assembly di interoperabilità Visual Studio consentono alle applicazioni gestite per l'accesso alle interfacce COM che forniscono l'estensibilità di Visual Studio. Esistono alcune differenze tra le interfacce COM e le versioni di interoperabilità. Ad esempio, HRESULT in genere vengono rappresentati come valori int e devono essere gestiti nello stesso modo come eccezioni, e i parametri (in particolare i parametri out) vengono considerati in modo diverso.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Gestione di valori HRESULT restituiti al codice gestito da COM  
 Quando si chiama un'interfaccia COM dal codice gestito, esaminare il valore HRESULT e generare un'eccezione, se necessario. Il <xref:Microsoft.VisualStudio.ErrorHandler> classe contiene il <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> metodo, che genera un'eccezione COM, a seconda del valore di HRESULT passato.  
  
 Per impostazione predefinita, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> genera un'eccezione ogni volta che viene passato un HRESULT che ha un valore minore di zero. Nei casi in cui tali valori HRESULT sono valori accettabili e non deve essere generata alcuna eccezione, i valori HRESULT aggiuntivi devono essere passati a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> dopo i valori da testare. Se il valore HRESULT testato corrisponde a qualsiasi valore HRESULT passati in modo esplicito <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, viene generata alcuna eccezione.  
  
> [!NOTE]
>  Il <xref:Microsoft.VisualStudio.VSConstants> classe contiene costanti per valori HRESULT comuni, ad esempio, <xref:Microsoft.VisualStudio.VSConstants.S_OK> e <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULT, ad esempio, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> e <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants>fornisce inoltre il <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> e <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> metodi, che corrispondono alle macro SUCCEEDED e FAILED in COM.  
  
 Ad esempio, si consideri la seguente chiamata di funzione, in cui <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> è un valore restituito accettabile, ma qualsiasi altro valore HRESULT minore di zero rappresenta un errore.  
  
 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 Se sono presenti più valori restituiti accettabili, ulteriori valori HRESULT possono solo essere aggiunto all'elenco nella chiamata a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Restituzione di valori HRESULT a COM dal codice gestito  
 Se si verifica alcuna eccezione, il codice gestito restituisce <xref:Microsoft.VisualStudio.VSConstants.S_OK> alla funzione COM che lo hanno chiamato. L'interoperabilità COM supporta eccezioni comuni fortemente tipizzate nel codice gestito. Ad esempio, un metodo che riceve un inaccettabile `null` argomento genera un <xref:System.ArgumentNullException>.  
  
 Se non si è certi quale eccezione generare, ma si conosce il valore HRESULT a cui si desidera restituire a COM, è possibile utilizzare il <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> metodo consente di generare un'eccezione appropriata. Ciò funziona anche con un errore non standard, ad esempio, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>tenta di eseguire il mapping di HRESULT passato e un'eccezione fortemente tipizzata. Se ciò non è possibile, genera un'eccezione COM generica. Il risultato finale è che il valore HRESULT passato a <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> dal codice gestito, viene restituito alla funzione COM che lo hanno chiamato.  
  
> [!NOTE]
>  Le eccezioni compromettono le prestazioni e servono per indicare condizioni anomale dei programmi. Le condizioni che si verificano spesso devono essere gestite inline, invece di generare un'eccezione.  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown parametri passati come tipo void * *  
 Cercare [i parametri definiti come tipo out] `void **` in COM interfaccia, ma che sono definiti come `[``iid_is``]` nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo del metodo assembly di interoperabilità.  
  
 In alcuni casi, un'interfaccia COM che genera un `IUnknown` oggetto e l'interfaccia COM passa quindi come tipo `void **`. Queste interfacce sono particolarmente importanti perché se la variabile viene definita come [out] nel file IDL, la `IUnknown` oggetto è con conteggio dei riferimenti con il `AddRef` metodo. Se l'oggetto non viene gestita correttamente, si verifica una perdita di memoria.  
  
> [!NOTE]
>  Un `IUnknown` l'oggetto creato dall'interfaccia COM e restituiti in una variabile [out] causa una perdita di memoria se non viene rilasciato in modo esplicito.  
  
 Metodi gestiti che gestiscono gli oggetti, è necessario considerare <xref:System.IntPtr> come un puntatore a un `IUnknown` e chiamare il <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> per ottenere l'oggetto. Il chiamante deve quindi eseguire il cast di valore restituito da qualsiasi tipo è appropriato. Quando l'oggetto non è più necessario, chiamare <xref:System.Runtime.InteropServices.Marshal.Release%2A> per rilasciarlo.  
  
 Di seguito è riportato un esempio di chiamata il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> metodo e la gestione di `IUnknown` correttamente l'oggetto:  
  
```  
MyClass myclass;  
Object object;  
IntPtr pObj;  
Guid iid = Typeof(MyClass).Guid;  
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);     
if (NativeMethods.Succeeded(hr))   
{  
    try   
    {  
        object = Marshal.GetObjectForIUnknown(pObj);  
        myclass = object;  
    }  
    finally   
    {  
        Marshal.Release(pObj);  
    }  
}  
else   
{  
    // error calling QueryViewInterface  
}  
```  
  
> [!NOTE]
>  I metodi seguenti sono note come passare `IUnknown` oggetto puntatori come tipo <xref:System.IntPtr>. Come descritto in questa sezione è necessario gestirle.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>[Out] parametri facoltativi  
 Cercare i parametri che sono definiti come [out] tipo di dati (`int`, `object`e così via) in COM interfaccia, ma che sono definiti come matrici dello stesso tipo di dati nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo del metodo assembly di interoperabilità.  
  
 Interfacce di alcuni COM, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, considerare [i parametri come facoltativi out]. Se non è necessario un oggetto, le interfacce COM restituiscono un `null` come il valore del parametro anziché creare l'oggetto [out] puntatore. Si tratta di un comportamento correlato alla progettazione. Per queste interfacce, `null` i puntatori vengono considerati come parte del comportamento corretto del pacchetto VSPackage e viene restituito alcun errore.  
  
 Poiché Common Language Runtime non consente il valore di parametro [out] per essere `null`, parte del comportamento di queste interfacce progettato non sono disponibili direttamente nel codice gestito. Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metodi di assembly di interoperabilità per interfacce interessati aggirare il problema definendo i parametri come matrici, perché Common Language Runtime consente il passaggio di `null` matrici.  
  
 Le implementazioni gestite di questi metodi devono inserire una `null` matrice nel parametro quando non c'è niente da restituire. In caso contrario, creare una matrice a un elemento del tipo corretto e inserire il valore restituito nella matrice.  
  
 Metodi che ricevono informazioni da interfacce con [out] facoltativo gestiti i parametri ricevono il parametro sotto forma di matrice. Esaminare solo il valore del primo elemento della matrice. Se non è `null`, considerare il primo elemento, come se fosse il parametro originale.  
  
## <a name="passing-constants-in-pointer-parameters"></a>Costanti di passaggio nei parametri di puntatore  
 Cercare i parametri che sono definiti come [in] i puntatori a interfaccia COM, ma che sono definiti come un <xref:System.IntPtr> digitare il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo del metodo assembly di interoperabilità.  
  
 Un problema analogo si verifica quando un'interfaccia COM passa un valore speciale, ad esempio 0, -1 o -2, anziché un puntatore all'oggetto. A differenza di [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], Common Language Runtime non consente le costanti eseguire il cast come oggetti. Al contrario, il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] assembly di interoperabilità definisce il parametro come un <xref:System.IntPtr> tipo.  
  
 Le implementazioni gestite di questi metodi devono sfruttare il fatto che il <xref:System.IntPtr> classe dispone di entrambi `int` e `void *` costruttori per creare un <xref:System.IntPtr> da un oggetto o una costante integer, come appropriato.  
  
 Metodi che ricevono gestiti <xref:System.IntPtr> devono utilizzare i parametri di questo tipo di <xref:System.IntPtr> operatori di conversione per gestire i risultati di tipo. Prima di convertire il <xref:System.IntPtr> a `int` ed eseguirne il test su costanti integer pertinente. Se non corrispondono, convertirlo in un oggetto del tipo richiesto e continuare.  
  
 Per esempi di questo tipo, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE restituiscono i valori passati come [parametri out]  
 Cerca i metodi che hanno un `retval` valore restituito dell'interfaccia COM, ma che hanno un `int` valore restituito e un altro [parametro di matrice in out] il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo del metodo assembly di interoperabilità. Dovrebbe essere chiaro che questi metodi richiedono una gestione speciale in quanto il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipi di assembly di interoperabilità metodo dispongono di un parametro di più rispetto ai metodi di interfaccia COM.  
  
 Molte interfacce COM che gestiscono attività OLE inviano informazioni sullo stato OLE al programma chiamante archiviato nel `retval` restituito dell'interfaccia. Anziché utilizzare un valore restituito, corrispondente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] al programma chiamante archiviato in [out] i metodi di assembly di interoperabilità inviano le informazioni di parametro di matrice.  
  
 Le implementazioni gestite di questi metodi devono creare una matrice a elemento singolo dello stesso tipo del parametro [out] e inserirlo nel parametro. Il valore dell'elemento della matrice deve essere lo stesso come il componente COM appropriato `retval`.  
  
 Metodi gestiti che chiamano le interfacce di questo tipo devono effettuare il pull del primo elemento dalla matrice [out]. Questo elemento può essere considerato come se fosse un `retval` valore restituito dall'interfaccia COM corrispondente.  
  
## <a name="see-also"></a>Vedere anche  
 [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)