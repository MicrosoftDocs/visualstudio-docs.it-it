---
title: IDebugSymbolProvider | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: de77e30f0e9f52af10eef1757048a078d6d4a583
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Questa interfaccia rappresenta un provider di simboli che fornisce tipi, che vengono restituiti come campi e simboli.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un provider di simboli debba implementare questa interfaccia per fornire i simboli e informazioni sui tipi per un analizzatore di espressioni.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene ottenuta tramite COM `CoCreateInstance` funzione (per i provider di simboli non gestito) o caricando appropriata gestiti assembly di codice e creazione di provider il simbolo basato le informazioni contenute in tale assembly. Il motore di debug crea un'istanza di provider di simboli per lavorare insieme con l'analizzatore di espressioni. Vedere l'esempio per un approccio alla creazione di istanze di questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugSymbolProvider`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|`Initialize`|Deprecato. Non usare.|  
|`Uninitialize`|Deprecato. Non usare.|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Ottiene il campo che contiene l'indirizzo di debug.|  
|`GetField`|Deprecato. Non usare.|  
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Esegue il mapping di una posizione del documento in una matrice di indirizzi di debug.|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Esegue il mapping di un contesto di documento in una matrice di indirizzi di debug.|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Esegue il mapping di un indirizzo di debug in un contesto di documento.|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Ottiene la lingua utilizzata per compilare il codice in corrispondenza dell'indirizzo di debug.|  
|`GetGlobalContainer`|Deprecato. Non usare.|  
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Ottiene il campo che rappresenta un nome di metodo completo.|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Ottiene il tipo di campo di classe che rappresenta un nome completo della classe.|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Crea un enumeratore per gli spazi dei nomi associato all'indirizzo di debug.|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Nome di un simbolo viene eseguito il mapping a un tipo di simbolo.|  
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Ottiene l'indirizzo di debug che segue un indirizzo di debug specificata in un metodo.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene eseguito il mapping delle posizioni di documento in indirizzi di debug e viceversa.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come creare un'istanza del provider di simboli, dato il relativo GUID (motore di debug deve conoscere questo valore).  
  
```cpp  
// A debug engine uses its own symbol provider and would know the GUID  
// of that provider.  
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)  
{  
    // This is typically defined globally.  For this example, it is  
    // defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugSymbolProvider *pProvider = NULL;  
    if (pSymbolProviderGuid != NULL) {  
        CLSID clsidProvider = { 0 };  
        ::GetSPMetric(*pSymbolProviderGuid,  
                      storetypeFile,  
                      metricCLSID,  
                      &clsidProvider,  
                      strRegistrationRoot);  
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {  
            // No file type provider, try metadata provider.  
            ::GetSPMetric(*pSymbolProviderGuid,  
                          ::storetypeMetadata,  
                          metricCLSID,  
                          &clsidProvider,  
                          strRegistrationRoot);  
        }  
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {  
            CComPtr<IDebugSymbolProvider> spSymbolProvider;  
            spSymbolProvider.CoCreateInstance(clsidProvider);  
            if (spSymbolProvider != NULL) {  
                pProvider = spSymbolProvider.Detach();  
            }  
        }  
    }  
    return(pProvider);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)