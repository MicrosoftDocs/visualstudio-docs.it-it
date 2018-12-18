---
title: Interfaccia IDebugStackFrameSniffer | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 250c104d24f27900a6ff0eb8e8f72644f820bf5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesniffer-interface"></a>Interfaccia IDebugStackFrameSniffer
Consente di enumerare i frame di stack logico noti da un componente. Motori di script è in genere implementano questa interfaccia. Il processo debug manager non utilizza questa interfaccia per trovare tutti gli stack frame associato a un determinato thread.  
  
> [!NOTE]
>  Il debugger chiama questa interfaccia dall'interno del thread di interesse. Il motore di script deve identificare il thread corrente e restituisce un enumeratore appropriato.  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi ereditati da `IUnknown`, `IDebugStackFrameSniffer` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Restituisce un enumeratore di stack frame per il thread corrente.|