---
title: Avvio del debugger | Microsoft Docs
description: Informazioni sulla sequenza di metodi ed eventi con gli attributi appropriati necessari per avviare il debugger.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 67764a7f59c1b44e7e8cbc7a81befb120c541461
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094666"
---
# <a name="launch-the-debugger"></a>Avviare il debugger
Per avviare il debugger è necessario inviare la sequenza corretta di metodi ed eventi con i rispettivi attributi appropriati.

## <a name="sequences-of-methods-and-events"></a>Sequenze di metodi ed eventi

1. Gestione debug sessione (SDM) viene chiamato scegliendo **Avvia** dal menu **debug** . Per ulteriori informazioni, vedere [avviare un programma](../../extensibility/debugger/launching-a-program.md).

2. SDM chiama il metodo [alconnessione](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .

3. In base al modello di processo del motore di debug (DE), il `IDebugProgramNodeAttach2::OnAttach` metodo restituisce uno dei metodi seguenti, che determinano cosa accade successivamente.

     Se `S_FALSE` restituisce, il motore di debug (de) verrà caricato in fase di elaborazione della macchina virtuale.

     -oppure-

     Se `S_OK` restituisce, la de deve essere caricata in-process dell'SDM. Il SDM esegue quindi le attività seguenti:

    1. Chiama [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) per ottenere le informazioni sul motore di de.

    2. Consente di creare Co.

    3. Chiama il [Connetti](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. Il DE Invia un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) a SDM con un `EVENT_SYNC` attributo.

5. Il DE Invia un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) a SDM con un `EVENT_SYNC` attributo.

6. Il DE Invia un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) a SDM con un `EVENT_SYNC` attributo.

7. Il DE Invia un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) a SDM con un `EVENT_SYNC` attributo.

8. Il DE Invia un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) a SDM con un `EVENT_SYNC` attributo.

## <a name="see-also"></a>Vedi anche
- [Chiamata di eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
- [Avvio di un programma](../../extensibility/debugger/launching-a-program.md)
