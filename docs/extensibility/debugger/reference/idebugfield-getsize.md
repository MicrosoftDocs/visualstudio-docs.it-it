---
title: IDebugField::GetSize | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6e7343f6d496587c3fbf69adf3ec56a9f516a9be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
Questo metodo ottiene le dimensioni di un campo, in byte.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetSize(   
   DWORD* pdwSize  
);  
```  
  
```csharp  
int GetSize(  
   out uint pdwSize  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwSize`  
 [out] Restituisce le dimensioni.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Tutti i campi sono un tipo e tutti i tipi hanno una dimensione. Ad esempio, un campo con un tipo di byte ha una dimensione di 1 byte.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)