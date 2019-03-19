---
title: Interfaccia IDebugSyncOperation | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 7184be62a8ad2b65e81d1ad82f01f0ce3f4668c5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146383"
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