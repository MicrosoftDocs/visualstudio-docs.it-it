---
title: IDebugPortSupplier2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier2
helpviewer_keywords: IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 257bbf334adbdfd3a93cf172de0b15bf63cb3217
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Questa interfaccia fornisce porte al gestore di sessione di debug (SDM).  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un fornitore di porta personalizzato implementa questa interfaccia per rappresentare un fornitore di porta.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a `CoCreateInstance` con un fornitore di porta `GUID` restituisce questa interfaccia (questo è il modo consueto per ottenere questa interfaccia). Ad esempio:  
  
```cpp  
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)  
{  
    IDebugPortSupplier2 *pPS = NULL;  
    if (pPortSupplierGuid != NULL) {  
        CComPtr<IDebugPortSupplier2> spPortSupplier;  
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);  
        if (spPortSupplier != NULL) {  
            pPS = spPortSupplier.Detach();  
        }  
    }  
    return (pPS);  
}  
```  
  
 Una chiamata a [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) restituisce questa interfaccia, che rappresenta il fornitore della porta corrente utilizzato da [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) restituisce questa interfaccia, che rappresenta il fornitore che ha creato la porta della porta.  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) rappresenta un elenco di `IDebugPortSupplier` interfacce (il `IEnumDebugPortSuppliers` interfaccia viene ottenuta da [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), che rappresenta tutti i fornitori di porta registrato con [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]).  
  
 Un motore di debug in genere non interagiscono con un fornitore di porta.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugPortSupplier2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Ottiene il nome della porta fornitore.|  
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Ottiene l'identificatore fornitore porta.|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Ottiene una porta da un fornitore di porta.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Enumera le porte che esistono già.|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Verifica che un fornitore della porta supporta l'aggiunta di nuove porte.|  
|[Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Aggiunge una porta.|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Rimuove una porta.|  
  
## <a name="remarks"></a>Note  
 Un fornitore di porta può identificarsi per nome e ID, aggiungere e rimuovere le porte ed enumerare tutte le porte che fornisce il fornitore della porta.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)