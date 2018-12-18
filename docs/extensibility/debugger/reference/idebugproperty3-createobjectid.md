---
title: IDebugProperty3::CreateObjectID | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty3::CreateObjectID
helpviewer_keywords: IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 337e1a4025e71a637e73b258df41828b7ddf1f43
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Crea un ID univoco per questa proprietà per assicurarsi che sia univoco tra tutte le altre proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato quando il gestore di sessione di debug desidera assicurarsi che questa proprietà viene identificata in modo univoco tra tutte le altre proprietà. Il motore di debug (DE) supporta questo metodo, a meno che le proprietà che si occupa sono già identificate. Se la Germania non supporta questo metodo, viene restituito `E_NOTIMPL`.  
  
 Qualsiasi ID univoco creato con `CreateObjectID` viene eliminato quando il [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) metodo viene chiamato; inoltre segnala la fine della necessità per identificare in modo univoco questa proprietà.  
  
> [!NOTE]
>  Nessun metodo per recuperare l'ID univoco, quindi la Germania può eseguire qualsiasi operazione per gli ID univoci quando la `CreateObjectID` metodo viene chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)