---
title: Interfaccia IDebugSyncOperation | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSyncOperation interface
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3724ad50771ca49460e130bf93ebc244681bd782
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349604"
---
# <a name="idebugsyncoperation-interface"></a>Interfaccia IDebugSyncOperation
Consente a un motore di script eseguire un'astrazione di un'operazione (ad esempio, valutazione delle espressioni) che deve essere eseguita mentre è annidata in un thread bloccato specifico. L'interfaccia fornisce inoltre un meccanismo per l'annullamento di operazioni che non risponde.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugSyncOperation` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|Restituisce il thread dell'applicazione di destinazione per questa operazione sincrona.|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|In modo sincrono esegue l'operazione e restituisce.|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|Annulla un'operazione in corso in un altro thread.|