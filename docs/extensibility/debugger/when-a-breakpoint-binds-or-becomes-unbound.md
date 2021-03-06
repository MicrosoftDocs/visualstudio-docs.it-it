---
title: Quando un punto di interruzione viene associato o non è associato | Microsoft Docs
description: Informazioni sui punti di interruzione non associati. Quando non è possibile associare un punto di interruzione nel momento in cui viene effettuata una chiamata, l'ora di associazione e l'ora di creazione del punto di interruzione sono diverse.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b6e1a6acdee89be293ab4a6dc72a3d4fd4336d88
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091409"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Quando un punto di interruzione viene associato o non associato
Quando non è possibile associare un punto di interruzione nel momento in cui viene effettuata una chiamata al metodo [IDebugPendingBreakpoint2:: CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) , i tempi di associazione e di creazione del punto di interruzione sono diversi.

## <a name="methods-called"></a>Metodi chiamati
 Il gestore di debug della sessione (SDM) chiama i metodi seguenti:

1. [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). Il valore DE restituisce un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md).

2. [IDebugPendingBreakpoint2:: Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).

3. [IDebugPendingBreakpoint2:: virtualizzate](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).

4. Il metodo [IDebugPendingBreakpoint2:: bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) e restituisce S_OK. Il DE Invia un [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) o [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).

5. Metodi [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) e [IDebugBreakpointBoundEvent2:: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) per verificare e ottenere i punti di interruzione associati.

## <a name="see-also"></a>Vedi anche
- [Chiamata di eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
