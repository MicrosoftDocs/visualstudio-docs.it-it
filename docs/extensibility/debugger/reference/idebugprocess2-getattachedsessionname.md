---
title: IDebugProcess2::GetAttachedSessionName | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 34e404fe33858c1db7d9dfb103df7b4e0bb9fb91
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Ottiene il nome della sessione che il debug di questo processo. L'IDE è possibile visualizzare queste informazioni a un utente che il debug di un processo specifico in un computer specifico.  
  
> [!NOTE]
>  Questo metodo è deprecato e la relativa implementazione deve sempre restituire `E_NOTIMPL`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrSessionName`  
  
## <a name="return-value"></a>Valore restituito  
 Questo metodo deve sempre restituire `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)