---
title: Interfaccia IActiveScriptSiteDebug | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9b36054deeceb0528fb7ea399cc41d8edbbb47e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug-interface"></a>Interfaccia IActiveScriptSiteDebug Interface
Implementare smart host il `IActiveScriptSiteDebug` interfaccia per eseguire la gestione dei documenti e deve far parte di debug. Il `IActiveScriptSite` oggetto in genere fornisce un'implementazione del `IActiveScriptSiteDebug` interfaccia. Se questa operazione, chiamare il `IActiveScriptSite::QueryInterface` per ottenere il `IActiveScriptSiteDebug` interfaccia.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IActiveScriptSiteDebug` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Utilizzato dal motore di linguaggio per delegare `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Restituisce l'oggetto di debug dell'applicazione associata a questo sito di script.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Ottiene il nodo dell'applicazione nella quale script devono essere aggiunti i documenti.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Consente a un host intelligente stabilire come gestire errori di run-time.|