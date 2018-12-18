---
title: Interfaccia IDebugExpression | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39e139e09362fc392d1110e26837c52fd4c642c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpression-interface"></a>Interfaccia IDebugExpression
Rappresenta un'espressione valutata in modo asincrono. Motori di script è in genere implementano questa interfaccia. In genere, un debugger IDE utilizza questa interfaccia per abilitare una finestra di esecuzione immediata o finestra Espressioni di controllo.  
  
> [!NOTE]
>  Il `IDebugExpression` interfaccia è disponibile solo da uno stack frame.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IDebugExpression` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Avvia la valutazione dell'espressione.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Interrompe l'espressione.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Determina se l'operazione è stata completata.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Restituisce il risultato della valutazione dell'espressione come una stringa e valore restituito dell'operazione.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Restituisce il risultato della valutazione dell'espressione come una proprietà di debug e il valore restituito dell'operazione.|