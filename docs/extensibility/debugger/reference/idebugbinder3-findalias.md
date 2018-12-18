---
title: IDebugBinder3::FindAlias | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder3::FindAlias
helpviewer_keywords: IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b88ae0da5f90da45d33ec56169665e9c8430846c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Questo metodo individua un alias, un nome. Si cercherà tutti gli alias nel programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcstrName`  
 [in] Nome di alias da trovare.  
  
 `ppAlias`  
 [out] Alias (se presente) è rappresentato dal [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interfaccia.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` (se non viene trovato alias) o un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo inizializza l'oggetto di destinazione a null prima di chiamare il metodo. quindi verifica un valore null in seguito per determinare se l'alias è stato trovato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)