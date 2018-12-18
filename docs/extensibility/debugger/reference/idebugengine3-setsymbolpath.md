---
title: IDebugEngine3::SetSymbolPath | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5a79cfd817be1a665f0008a39420e7cb39cc50b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Imposta il percorso o i percorsi in cui vengono ricercati i simboli di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```csharp  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`szSymbolSearchPath`|[in] Stringa contenente il percorso di ricerca di simboli o i percorsi. Per informazioni dettagliate, vedere "la sezione Osservazioni". Non può essere null.|  
|`szSymbolCachePath`|[in] Stringa contenente il percorso locale in cui possono essere memorizzati nella cache i simboli. Non può essere null.|  
|`Flags`|[in] Non è utilizzato; sempre impostato su 0.|  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 La stringa `szSymbolSearchPath` è un elenco di uno o più percorsi, separati da punti e virgola, di cercare simboli. Questi percorsi possono essere un percorso locale, un percorso UNC in stile o un URL. Questi percorsi possono anche essere una combinazione di tipi diversi. Se il percorso UNC (ad esempio, \\\Symserver\Symbols), quindi il motore di debug deve determinare se il percorso è a un server di simboli e deve essere in grado di caricare i simboli dai server memorizzarli nella cache nel percorso specificato da `szSymbolCachePath`.  
  
 Il percorso dei simboli può anche contenere uno o più percorsi di cache. Memorizza nella cache è elencati in ordine di priorità, con la cache di priorità più alta per primi e separati da * simboli. Ad esempio:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 Il [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) metodo esegue il carico effettivo dei simboli.  
  
## <a name="see-also"></a>Vedere anche  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)