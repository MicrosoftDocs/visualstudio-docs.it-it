---
title: IDebugProgramPublisher2::PublishProgram | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 67ac5bad37ad5df85022ba6572da44d32de39736
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
Questo metodo crea un programma disponibile per i motori di debug (DEs) e il gestore di sessione di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   LPCOLESTR        szFriendlyName,  
   IUnknown*        pDebuggeeInterface  
);  
```  
  
```csharp  
int PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   string           szFriendlyName,  
   object           pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `Engines`  
 [in] Matrice di GUID per la crittografia DEs che è possibile avviare o allegare a questo programma.  
  
 `szFriendlyName`  
 [in] Nome descrittivo per il programma (viene visualizzato nei menu o finestre di dialogo presentate all'utente).  
  
 `pDebuggeeInterface`  
 [in] `IUnknown` interfaccia per il programma (questo valore viene utilizzato come un cookie per identificare in modo univoco il programma; questo valore viene utilizzato per annullare "la pubblicazione" il programma)  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Per rendere non sono più disponibili per il debug di un programma, chiamare [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)