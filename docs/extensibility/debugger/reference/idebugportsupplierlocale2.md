---
title: IDebugPortSupplierLocale2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c1cd0160b1ec5b1c9d86c277f2b47011d1b7610c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
Fornisce il supporto delle impostazioni locali per un fornitore di porta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortSupplierLocale2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un fornitore di porta personalizzato implementa questa interfaccia per definire le impostazioni locali.  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono illustrati i metodi di **IDebugPortSupplierLocale2**.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Imposta le impostazioni locali per il fornitore della porta.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)