---
title: IDebugProgramNode2::GetProgramName | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2fd9fd883b1416d19f6525800723572e2384798
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramnode2getprogramname"></a>IDebugProgramNode2::GetProgramName
Ottiene il nome del programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetProgramName (   
   BSTR* pbstrProgramName  
);  
```  
  
```csharp  
int GetProgramName (   
   out string pbstrProgramName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrProgramName`  
 [out] Restituisce il nome del programma.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il nome di un programma non è la stessa operazione come il percorso del programma, anche se il nome del programma può essere parte di tale percorso.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per una semplice `CProgram` oggetto che implementa il [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia. Il `MakeBstr` una copia della stringa specificata come BSTR viene allocata dalla funzione.  
  
```cpp  
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {    
   if (!pbstrProgramName)    
      return E_INVALIDARG;    
  
   // Assign the member program name to the passed program name.    
   *pbstrProgramName = MakeBstr(m_pszProgramName);    
   return NOERROR;    
}    
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)