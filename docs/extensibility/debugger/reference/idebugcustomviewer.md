---
title: IDebugCustomViewer | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomViewer
helpviewer_keywords: IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9bbe546ffb3c6e61b251e8afbfc7fa9018ffa1b0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Questa interfaccia consente un analizzatore di espressioni (Java EE) per visualizzare un valore della proprietà nel formato necessario.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un EE implementa questa interfaccia per visualizzare un valore della proprietà in un formato personalizzato.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a COM `CoCreateInstance` funzione crea un'istanza di questa interfaccia. Il `CLSID` passato a `CoCreateInstance` viene ottenuto dal Registro di sistema. Una chiamata a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Ottiene il percorso del Registro di sistema. Per informazioni dettagliate, nonché l'esempio, vedere la sezione Osservazioni.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Questa interfaccia implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Disponibili DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Esegue tutte le operazioni necessarie per visualizzare un determinato valore.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene utilizzata quando un valore della proprietà non può essere visualizzato in modo normale, ad esempio, con una tabella di dati o un altro tipo di proprietà complessa. Un visualizzatore personalizzato, come rappresentato dal `IDebugCustomViewer` interfaccia, è diverso da un visualizzatore di tipo, ovvero un programma esterno per la visualizzazione dei dati di un tipo specifico, indipendentemente dal motore di esecuzione. L'analizzatore di Espressioni implementa un visualizzatore personalizzato che è specifico di tale EE. L'utente seleziona il tipo di Visualizzatore da utilizzare, sia esso un visualizzatore di tipo o un visualizzatore personalizzato. Vedere [Visualizing e visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md) per informazioni dettagliate su questo processo.  
  
 Un visualizzatore personalizzato registrato nello stesso modo come un EE e, pertanto, è necessario un GUID del linguaggio e un fornitore di GUID. La metrica esatto (o nome della voce del Registro di sistema) è noto solo al motore di esecuzione. Questa metrica viene restituita nel [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) struttura, che a sua volta, viene restituito da una chiamata a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). Il valore archiviato nella metrica è il `CLSID` che viene passata a COM `CoCreateInstance` funzione (vedere l'esempio).  
  
 Il [SDK helper per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) funzione `SetEEMetric`, può essere utilizzato per registrare un visualizzatore personalizzato. Vedere la sezione del Registro di sistema "Analizzatori di espressioni" `Debugging SDK Helpers` per chiavi di registro di sistema specifica che è necessario un visualizzatore personalizzato. Si noti che un visualizzatore personalizzato deve solo una metrica (che dipende dall'implementatore del motore di esecuzione), mentre un analizzatore di espressioni richiede alcune metriche predefinite.  
  
 In genere, un visualizzatore personalizzato fornisce una visualizzazione di sola lettura dei dati, poiché il [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia fornito a [disponibili DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) non ha metodi per modificare il valore della proprietà, ad eccezione sotto forma di stringa. Per supportare la modifica di blocchi arbitrari di dati, l'analizzatore di Espressioni implementa un'interfaccia personalizzata sullo stesso oggetto che implementa il `IDebugProperty3` interfaccia. Questa interfaccia personalizzata verrà quindi fornire i metodi necessari per modificare un blocco di dati arbitrario.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come ottenere il primo visualizzatore personalizzato da una proprietà, se tale proprietà è qualsiasi visualizzatori personalizzati.  
  
```cpp  
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)  
{  
    // This string is typically defined globally.  For this example, it  
    // is defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugCustomViewer *pViewer = NULL;  
    if (pProperty != NULL) {  
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);  
        if (pProperty3 != NULL) {  
            HRESULT hr;  
            ULONG viewerCount = 0;  
            hr = pProperty3->GetCustomViewerCount(&viewerCount);  
            if (viewerCount > 0) {  
                ULONG viewersFetched = 0;  
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };  
                hr = pProperty3->GetCustomViewerList(0,  
                                                     1,  
                                                     &viewerInfo,  
                                                     &viewersFetched);  
                if (viewersFetched == 1) {  
                    CLSID clsidViewer = { 0 };  
                    CComPtr<IDebugCustomViewer> spCustomViewer;  
                    // Get the viewer's CLSID from the registry.  
                    ::GetEEMetric(viewerInfo.guidLang,  
                                  viewerInfo.guidVendor,  
                                  viewerInfo.bstrMetric,  
                                  &clsidViewer,  
                                  strRegistrationRoot);  
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {  
                        // Instantiate the custom viewer.  
                        spCustomViewer.CoCreateInstance(clsidViewer);  
                        if (spCustomViewer != NULL) {  
                            pViewer = spCustomViewer.Detach();  
                        }  
                    }  
                }  
            }  
        }  
    }  
    return(pViewer);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)