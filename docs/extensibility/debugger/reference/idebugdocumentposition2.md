---
description: Questa interfaccia rappresenta una posizione astratta in un file di origine.
title: IDebugDocumentPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b7c4c8e469dff76e2af631c4943305b0e3ee8e7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066399"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Questa interfaccia rappresenta una posizione astratta in un file di origine.

## <a name="syntax"></a>Sintassi

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 In genere questa interfaccia viene implementata in Visual Studio. Un motore di debug (DE) implementa anche questa interfaccia se deve fornire il proprio codice sorgente, ad esempio quando il DE implementa l'interfaccia [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene passata come argomento a [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). Viene inoltre fornito come parte di un'Unione [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) (in particolare, una struttura [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) ) che fa parte della struttura [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , che viene utilizzata per la creazione di un punto di interruzione in sospeso.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugDocumentPosition2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Ottiene il nome file del file di origine che contiene la posizione del documento.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Ottiene il documento contenitore.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Determina se questa posizione è contenuta nel documento specificato.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Ottiene l'intervallo per questa posizione del documento.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
