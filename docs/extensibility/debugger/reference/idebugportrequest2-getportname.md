---
title: IDebugPortRequest2::GetPortName | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c81bdc6586766cb4a241bf29e653cb1b10f66f2f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Ottiene il nome della porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrPortName`  
 [out] Restituisce il nome della porta.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) interfaccia viene in genere passata da un pacchetto di debug (il client) a un fornitore di porta (server) per ottenere una connessione a una porta. Sia il pacchetto di debug e il fornitore della porta sono consapevoli delle possibili scelte per la porta. Se una stringa semplice può descrivere la porta, quindi il `IDebugPortRequest2::GetPortName` dispone di informazioni sufficienti per stabilire la connessione. In caso contrario, le interfacce aggiuntive possono essere fornite tramite il client, che può essere ottenuto tramite il server `IDebugPortRequest2::QueryInterface`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)