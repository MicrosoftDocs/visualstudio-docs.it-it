---
title: IActiveScriptError | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptError interface
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a403bf412a0c93a5c435e1a3184202ed68d406ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripterror"></a>IActiveScriptError
Oggetto che implementa questa interfaccia viene passato per il [IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md) metodo ogni volta che il motore di script rileva un errore non gestito. L'host chiama quindi i metodi su questo oggetto per ottenere informazioni sull'errore che si è verificato.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|Recupera le informazioni sull'errore.|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|Recupera la posizione nel codice sorgente in cui si è verificato un errore.|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|Recupera la riga nel file di origine in cui si è verificato un errore.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)