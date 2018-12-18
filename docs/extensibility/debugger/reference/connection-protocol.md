---
title: CONNECTION_PROTOCOL | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e1e1dc8cd22b529eafd6183578be7de6ffe69549
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="connectionprotocol"></a>CONNECTION_PROTOCOL
Indica il protocollo utilizzato per la comunicazione tra un server di debug e il pacchetto di debug (DE).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef enum tagCONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
} CONNECTION_PROTOCOL;  
```  
  
```csharp  
public enum CONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 CONNECTION_NONE  
 Non è è stata stabilita alcuna connessione a un server.  
  
 CONNECTION_UNKNOWN  
 È stata stabilita una connessione, ma è di tipo sconosciuto.  
  
 CONNECTION_LOCAL  
 Connessione è a un server locale.  
  
 CONNECTION_PIPE  
 Connessione viene eseguita tramite una named pipe.  
  
 CONNECTION_TCPIP  
 Connessione utilizza TCP/IP.  
  
 CONNECTION_HTTP  
 Connessione utilizza HTTP (tramite un server Web).  
  
 CONNECTION_OTHER  
 Un altro tipo di connessione è stato stabilito (questo valore non viene attualmente utilizzato).  
  
## <a name="remarks"></a>Note  
 Questi valori sono restituiti dal [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)