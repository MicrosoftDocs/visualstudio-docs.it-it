---
title: IDebugExceptionEvent2::GetException | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4cd3c8e18408dafc73729dafff330435e4e2d4f2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925656"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene una descrizione dettagliata dell'eccezione che ha generato questo evento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetException(   
   EXCEPTION_INFO* pExceptionInfo  
);  
```  
  
```csharp  
int GetException(   
   EXCEPTION_INFO[] pExceptionInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pExceptionInfo`  
 [in, out] Un' [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struttura compilata con la descrizione dell'eccezione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 [Solo C++] Il chiamante è responsabile della liberazione tutte le stringhe nel [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struttura, nonché di rilasciare la [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto nella struttura.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

