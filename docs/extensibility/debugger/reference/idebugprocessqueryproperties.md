---
title: IDebugProcessQueryProperties | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 66c2c3800d5f571595d7aec1a1e145cbccd38ff5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Questa interfaccia è implementata da un'interfaccia di estensione [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) i responsabili dell'implementazione. Consente all'implementatore ottenere informazioni sull'ambiente dei processi di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Implementare questa interfaccia per ottenere informazioni sull'ambiente di esecuzione di un processo di debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugProcessQueryProperties`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Query per un valore della proprietà.|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Query per i valori delle proprietà.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene implementata raramente.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)