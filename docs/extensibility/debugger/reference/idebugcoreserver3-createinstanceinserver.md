---
title: IDebugCoreServer3::CreateInstanceInServer | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords: IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cbd287f5ab75374a3272ecbb34c36ffdf384ba84
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Crea un'istanza di un motore di debug nel server.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```csharp  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `szDll`  
 [in] Percorso della dll che implementa il CLSID specificato nel `clsidObject` parametro. Se si tratta di `NULL`, quindi COM `CoCreateInstance` funzione viene chiamata.  
  
 `wLangId`  
 [in] Impostazioni locali del motore di debug. Può essere 0 se il [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) metodo non deve essere chiamato.  
  
 `clsidObject`  
 [in] CLSID del motore di debug da creare.  
  
 `riid`  
 [in] ID di interfaccia dell'interfaccia specifica per recuperare l'oggetto della classe.  
  
 `ppvObject`  
 [out] `IUnknown` interfaccia dall'oggetto istanziato. Eseguire il cast o effettuare il marshalling di questo oggetto per l'interfaccia desiderata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)