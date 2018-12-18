---
title: Interfaccia IDebugStackFrame | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrame interface
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36fa0ba2d1b4049ad41ff0502ed33be0a706d9f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframe-interface"></a>Interfaccia IDebugStackFrame
Rappresenta un frame di stack logico sullo stack di thread. Chiamare il `IDebugStackFrame::QueryInterface` per ottenere il `IDebugExpressionContext` interfaccia, che consente di espressione di valutazione ed espressioni di controllo di windows.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IDebugStackFrame` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|Restituisce il contesto corrente codice associato al frame dello stack.|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|Restituisce una descrizione breve o lungo testuale dello stack frame.|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|Restituisce una descrizione testuale lungo o breve della lingua.|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|Restituisce il thread associato a questo stack frame.|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|Restituisce un visualizzatore di proprietà per il fotogramma corrente.|