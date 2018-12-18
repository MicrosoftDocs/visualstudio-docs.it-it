---
title: IDebugPortRequest2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortRequest2
helpviewer_keywords: IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5b47a9bde47049c957af9f60e1d09d03b55c2359
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Questa interfaccia descrive una porta. Questa descrizione viene utilizzata per aggiungere la porta a un fornitore di porta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio è in genere implementa questa interfaccia nel processo di recupero di una porta di debug da un fornitore di porta.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene passata in [Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) per creare una porta di debug. Una chiamata a [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) restituisce questa interfaccia, che rappresenta la richiesta utilizzata per creare la porta in primo luogo.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugPortRequest2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Ottiene il nome della porta da creare.|  
  
## <a name="remarks"></a>Note  
 In genere, un motore di debug non interagisce con un fornitore di porta e non disporrà di alcuna utilità per l'interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)