---
title: Interfaccia IDebugAsyncOperation | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugAsyncOperation interface
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 157ed1248535855fcb53ca2eb6f49427fea94149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperation-interface"></a>Interfaccia IDebugAsyncOperation
Implementa il gestore di eseguire il Debug di processi di `IDebugAsyncOperation` interfaccia. Un motore di linguaggio chiama il `IDebugApplication::CreateAsyncDebugOperation` per ottenere un riferimento a questa interfaccia. Il motore del linguaggio è possibile utilizzare il `IDebugAsyncOperation` interfaccia per fornire l'accesso asincrono a un'operazione sincrona di debug.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IDebugAsyncOperation` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Restituisce l'operazione sincrona debug associato all'oggetto.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Fa sì che l'operazione asincrona iniziare.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Annulla un'operazione.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Determina se l'operazione di debug è stata completata.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Fornisce il valore restituito e il parametro dell'oggetto restituito dall'operazione di debug sincrono.|