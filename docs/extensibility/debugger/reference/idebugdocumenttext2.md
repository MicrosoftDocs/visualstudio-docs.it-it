---
title: IDebugDocumentText2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentText2
helpviewer_keywords: IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0c3540dc77821e6aa3fb3884d82cd0c83eee8e24
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Questa interfaccia rappresenta un documento di testo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un motore di debug (DE) implementa questa interfaccia quando il codice sorgente che è necessario fornire è in formato testo. Poiché è il caso più comune, se un Germania implementa il [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaccia, deve inoltre implementare il `IDebugDocumentText2` interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Utilizzare il `QueryInterface` per questa interfaccia da ottenere un `IDebugDocument2` interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi nel `IDebugDocument2` interfaccia, implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Recupera la dimensione del testo in questa posizione nel documento.|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Recupera il testo dalla posizione specificata nel documento.|  
  
## <a name="remarks"></a>Note  
 Oggetto che implementa questa interfaccia deve implementare anche il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaccia, che fornisce il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaccia per un [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) oggetto.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)