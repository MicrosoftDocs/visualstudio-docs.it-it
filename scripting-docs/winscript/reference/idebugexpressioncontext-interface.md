---
title: Interfaccia IDebugExpressionContext | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugExpressionContext Interface
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext interface
ms.assetid: 52af82e8-0dec-49e2-a7f3-d00f66ca1401
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c55a2f270e4c82c578450092e5066b19fe9e606
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressioncontext-interface"></a>Interfaccia IDebugExpressionContext
Rappresenta un contesto in cui è possano valutare le espressioni. L'oggetto stack frame implementa questa interfaccia.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IDebugExpressionContext` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)|Crea un'espressione di debug per il testo specificato.|  
|[IDebugExpressionContext::GetLanguageInfo](../../winscript/reference/idebugexpressioncontext-getlanguageinfo.md)|Restituisce un nome e GUID per la lingua a cui appartiene questo contesto.|