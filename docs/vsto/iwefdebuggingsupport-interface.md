---
title: Interfaccia IWefDebuggingSupport | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8e8a1bc770ce030902691a8ee4f2634c79cbab9a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="iwefdebuggingsupport-interface"></a>Interfaccia IWefDebuggingSupport
  Implementata da un ambiente di debug, ad esempio Visual Studio, per semplificare il debug di App per Office. L'applicazione di Office, ad esempio Word o Excel, ottiene l'interfaccia da Visual Studio e quindi chiama i metodi dell'interfaccia in determinati momenti durante la sessione di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi che definisce l'interfaccia IWefDebuggingSupport.  
  
|nome|Descrizione|  
|----------|-----------------|  
|[Metodo GetAutoInsertExtensions](../vsto/getautoinsertextensions-method.md)|Ottiene informazioni sulle App per Office che devono essere inseriti automaticamente durante il debug.|  
|[Metodo SetWefProcessId](../vsto/setwefprocessid-method.md)|Fornisce l'identificatore di processo che verrà eseguito il contenuto Web estensioni Framework (WEF).|  
  
  