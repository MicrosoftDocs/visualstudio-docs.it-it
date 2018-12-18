---
title: Interfaccia IDebugStackFrameSnifferEx | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSnifferEx interface
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56d6e63c41db274634b2593989800ea0392b93a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesnifferex-interface"></a>Interfaccia IDebugStackFrameSnifferEx
Consente di enumerare i frame di stack logico noti da un componente. Motori di script è in genere implementano questa interfaccia. Il processo debug manager non utilizza questa interfaccia per trovare tutti gli stack frame associato a un determinato thread.  
  
> [!NOTE]
>  Questa interfaccia viene chiamata dall'interno il thread di interesse. L'implementazione dell'interfaccia deve identificare il thread corrente e restituisce un enumeratore appropriato.  
  
 Oltre ai metodi ereditati da `IDebugStackFrameSniffer`, `IDebugStackFrameSnifferEx` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Restituisce un enumeratore di stack frame per il thread corrente.|