---
title: Interfaccia IActiveScriptDebug | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptDebug interface
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1e1d0c1cf51c63f1bb3fcd90ae72520da907e50
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebug-interface"></a>Interfaccia IActiveScriptDebug
Implementata dai motori di script che supportano il debug. In genere, un oggetto che implementa il `IActiveScriptDebug` interfaccia anche implementa il `IActiveScript` interfaccia. In questo caso, chiamare il `IActiveScript::QueryInterface` per ottenere il `IActiveScriptDebug` interfaccia.  
  
 Il `IActiveScriptDebug` interfaccia fornisce i mezzi per:  
  
-   SmartHost ad assumere la gestione dei documenti.  
  
-   Gestione di debug di processo per sincronizzare il debug di più motori di script.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IActiveScriptDebug` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|Restituisce gli attributi di testo per un blocco di testo dello script arbitrario.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|Restituisce gli attributi di testo per un scriptlet arbitrario.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|Delega a `IDebugDocumentContext::EnumCodeContexts`.|