---
title: Interfaccia IDebugSyncOperation | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugSyncOperation interface
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6705c2aa990aef3cf551a94546bf78a64026cecc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsyncoperation-interface"></a>Interfaccia IDebugSyncOperation
Consente un motore di script eseguire un'astrazione di un'operazione (ad esempio la valutazione di espressioni) che deve essere eseguita mentre annidato in un determinato thread bloccati. Inoltre, l'interfaccia fornisce un meccanismo per l'annullamento di operazioni che non risponde.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IDebugSyncOperation` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|Restituisce il thread dell'applicazione di destinazione per l'operazione sincrona.|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|In modo sincrono, esegue l'operazione e restituisce.|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|Annulla un'operazione in corso in un altro thread.|