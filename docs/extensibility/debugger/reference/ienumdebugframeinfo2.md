---
title: IEnumDebugFrameInfo2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugFrameInfo2
helpviewer_keywords: IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fce74b91512ee22eda7ce8c3e61de0ac03636d2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Questa interfaccia enumera [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per fornire un elenco di strutture che descrive lo stack di chiamate corrente.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamate di Visual Studio [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) per ottenere questa interfaccia ogni volta che un punto di interruzione, un'eccezione o l'arresto si verifica in un programma in fase di debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugFrameInfo2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Recupera un numero specificato di [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Ignora un numero specificato di [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture in una sequenza di enumerazione.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Ottiene il numero di [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture in un enumeratore.|  
  
## <a name="remarks"></a>Note  
 Visual Studio consente di ottenere questa interfaccia come primo passaggio per la gestione di un punto di interruzione, un'eccezione o sospendere generati dall'utente nel programma sottoposto a debug. L'elenco di [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture rappresenta lo stack di chiamate corrente, con la chiamata di funzione corrente all'inizio dell'elenco e la funzione meno recente di chiamate alla fine dell'elenco. Ogni `FRAMEINFO` rappresenta uno stack frame, un contesto in cui le espressioni possono essere valutate e le variabili locali viene esaminato.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)