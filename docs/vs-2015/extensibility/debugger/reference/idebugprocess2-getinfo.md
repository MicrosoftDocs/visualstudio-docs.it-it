---
title: IDebugProcess2::GetInfo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetInfo
helpviewer_keywords:
- IDebugProcess2::GetInfo
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 57944fe59bbf33f3d63a63570fcd25e25e927b6a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968567"
---
# <a name="idebugprocess2getinfo"></a>IDebugProcess2::GetInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene una descrizione del processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetInfo(  
   PROCESS_INFO_FIELDS  Fields,  
   PROCESS_INFO*        pProcessInfo  
);  
```  
  
```csharp  
int GetInfo(  
   enum_PROCESS_INFO_FIELDS  Fields,  
   PROCESS_INFO[]            pProcessInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `Fields`  
 [in] Una combinazione di valori dal [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) enumerazione che specifica quali campi del `pProcessInfo` parametro devono essere compilati.  
  
 `pProcessInfo`  
 [out] Oggetto [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struttura compilata con una descrizione del processo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
