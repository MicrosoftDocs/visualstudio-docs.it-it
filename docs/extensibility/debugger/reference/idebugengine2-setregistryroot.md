---
title: IDebugEngine2::SetRegistryRoot | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 606ddb5380da2bfe0c75d20bc70bf0da911ea4e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
Imposta la radice del Registro di sistema per il motore di debug (DE).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetRegistryRoot(   
   LPCOLESTR pszRegistryRoot  
);  
```  
  
```csharp  
int SetRegistryRoot(   
   string pszRegistryRoot  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszRegistryRoot`  
 [in] La radice del Registro di sistema da utilizzare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo consente [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] per specificare una radice del Registro di sistema alternativo che la Germania deve utilizzare per ottenere le impostazioni del Registro di sistema; ad esempio, "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp".  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)