---
title: IDebugDisassemblyStream2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c1598ec8a6e5fca5275384c00433d74d22ce3505
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Questa interfaccia rappresenta un flusso di istruzioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un motore di debug implementa questa interfaccia per supporta il disassembly di codice di un programma.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata al [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) restituisce questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugDisassemblyStream2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Legge le istruzioni a partire dalla posizione corrente nel flusso del disassembly.|  
|[Ricerca](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Sposta il puntatore di lettura nel flusso di disassembly un determinato numero di istruzioni rispetto alla posizione specificata.|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Restituisce un identificatore del percorso di codice per un contesto di codice specifico.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Restituisce un oggetto di contesto codice corrispondente a un identificatore percorso codice specificato.|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Restituisce un identificatore di percorso di codice che rappresenta la posizione corrente del codice.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Ottiene il documento di origine associato a questo flusso disassembly.|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Ottiene l'ambito di questo flusso disassembly.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Ottiene le dimensioni del flusso disassembly.|  
  
## <a name="remarks"></a>Note  
 È possibile creare il flusso di disassembly per rappresentare l'intero spazio di indirizzi o solo una funzione o dal modulo all'interno dello spazio. Ogni istruzione è rappresentata da un [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struttura restituita da una chiamata al [lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)