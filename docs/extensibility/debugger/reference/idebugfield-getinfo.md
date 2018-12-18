---
title: IDebugField::GetInfo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6738306abd991062c5091f95375972ffe0d3384e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Questo metodo ottiene informazioni visualizzabili sul campo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetInfo(   
   FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO* pFieldInfo  
);  
```  
  
```csharp  
int GetInfo(  
   enum_FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO[] pFieldInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFields`  
 [in] Una combinazione di [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) le costanti che consente di selezionare informazioni da visualizzare. Se il campo rappresenta un simbolo, questo viene in genere il nome del simbolo e il tipo.  
  
 `pFieldInfo`  
 [out] Restituisce le informazioni nel fornito [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struttura.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)