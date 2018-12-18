---
title: IDebugPointerObject::Dereference | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPointerObject::Dereference
helpviewer_keywords: IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3e743f5a312e437ca48a5e36fb202783f41b934d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Ottiene l'oggetto a cui punta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwIndex`  
 [in] Un offset di byte semplici dall'inizio dell'oggetto a cui punta.  
  
 `ppObject`  
 [out] Restituisce un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) dell'oggetto che rappresenta l'oggetto a cui punta più offset, se presente.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore. Restituisce E_FAIL se questo oggetto non fa riferimento a un altro oggetto.  
  
## <a name="remarks"></a>Note  
 L'oggetto a cui puntata può essere primitivo o un tipo più complesso, ad esempio una classe o struttura.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)