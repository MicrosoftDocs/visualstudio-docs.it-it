---
title: Interfaccia IActiveScriptSiteDebug32 | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: a752851aa6afd903747dc58fed79d2bc5b27e3e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug32-interface"></a>Interfaccia IActiveScriptSiteDebug32
Implementare smart host il `IActiveScriptSiteDebug32` interfaccia per eseguire la gestione dei documenti e deve far parte di debug. Il `IActiveScriptSite` oggetto in genere fornisce un'implementazione del `IActiveScriptSiteDebug32` interfaccia. Se questa operazione, chiamare il `IActiveScriptSite::QueryInterface` per ottenere il `IActiveScriptSiteDebug32` interfaccia.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IActiveScriptSiteDebug32` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Restituisce l'oggetto di debug dell'applicazione associata a questo sito di script.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Utilizzato dal motore di linguaggio per delegare `IDebugCodeContext::GetSourceContext`.|