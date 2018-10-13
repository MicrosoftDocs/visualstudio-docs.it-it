---
title: IDebugCoreServer3::GetConnectionProtocol | Microsoft Docs
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
- IDebugCoreServer3::GetConnectionProtocol
helpviewer_keywords:
- IDebugCoreServer3::GetConnectionProtocol
ms.assetid: 368ced5b-c5d9-4090-a5b4-26ff400d1a55
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 744648e580ae21e8a0cfcaf311f6e1a1e617447e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269714"
---
# <a name="idebugcoreserver3getconnectionprotocol"></a>IDebugCoreServer3::GetConnectionProtocol
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Restituisce un valore che indica il protocollo viene usato per stabilire la comunicazione tra il server e il pacchetto di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetConnectionProtocol(  
   CONNECTION_PROTOCOL* pProtocol  
);  
```  
  
```csharp  
int GetConnectionProtocol(  
   CONNECTION_PROTOCOL[] pProtocol  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pProtocol`  
 [out] Restituisce uno dei valori di [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md) enumerazione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md)

