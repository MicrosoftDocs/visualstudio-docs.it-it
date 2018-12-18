---
title: Interfaccia IActiveScriptErrorDebug | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptErrorDebug interface
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ff2dda33c1e406f87a157173c41015acf96e62a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripterrordebug-interface"></a>Interfaccia IActiveScriptErrorDebug
Fornisce informazioni sul contesto di documento per gli errori in fase di compilazione ed eccezioni di runtime. Il `IActiveScriptError::QueryInterface` metodo supporta il `IActiveScriptErrorDebug` interfaccia.  
  
 Oltre ai metodi ereditati da `IActiveScriptError`, `IActiveScriptErrorDebug` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Fornisce il contesto di documento per questo errore.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Fornisce lo stack frame che è validi per gli errori di runtime.|