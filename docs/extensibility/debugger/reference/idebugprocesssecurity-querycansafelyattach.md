---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe132ddbd154e04e3cef1a20e826c3634c65bdb2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Questo metodo consente il fornitore della porta visualizzare un avviso prima che l'utente si connette a un processo non sicuro.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Valore restituito  
 I valori restituiti sono come segue:  
  
-   `S_OK`: Connessione al processo sicura e non viene visualizzata alcuna finestra di dialogo di avviso.  
  
-   `S_FALSE`: Collegamento potrebbe essere un problema di sicurezza e viene visualizzata una finestra di dialogo con un messaggio di avviso.  
  
-   `FAILURE`: Connessione al processo avrà esito negativo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)