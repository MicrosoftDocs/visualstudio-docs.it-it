---
title: IDebugProgramProvider2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ec46442757d7e4b59437db310a45500b2e9d0906
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Questa interfaccia registrata consente il debug di sessione manager (SDM) per ottenere informazioni sui programmi "pubblicati" tramite la [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgramProvider2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per fornire informazioni sui programmi in corso il debug. Questa interfaccia è registrata nella sezione del Registro di sistema utilizzando la metrica DE `metricProgramProvider`, come descritto in [SDK helper per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamata COM `CoCreateInstance` utilizzabile con il `CLSID` del provider viene ottenuto dal Registro di sistema. Vedere l'esempio.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Ottiene informazioni sui programmi in esecuzione, filtrati in modi diversi.|  
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Ottiene un nodo, viene assegnato un ID di processo specifico.|  
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Stabilisce un callback per il controllo degli eventi del provider associati a tipi specifici di processi.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Stabilisce una lingua per tutte le risorse specifiche della lingua necessarie per la Germania.|  
  
## <a name="remarks"></a>Note  
 In genere, un processo utilizza questa interfaccia per scoprire i programmi in esecuzione in tale processo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Esempio  
  
```cpp  
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)  
{  
    // This is typically defined globally.  For this example, it is  
    // defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugProgramProvider2 *pProvider = NULL;  
    if (pDebugEngineGuid != NULL) {  
        CLSID clsidProvider = { 0 };  
        ::GetMetric(NULL,  
                    metrictypeEngine,  
                    *pDebugEngineGuid,  
                    metricProgramProvider,  
                    &clsidProvider,  
                    strRegistrationRoot);  
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {  
            CComPtr<IDebugProgramProvider2> spProgramProvider;  
            spProgramProvider.CoCreateInstance(clsidProvider);  
            if (spProgramProvider != NULL) {  
                pProvider = spProgramProvider.Detach();  
            }  
        }  
    }  
    return(pProvider);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)