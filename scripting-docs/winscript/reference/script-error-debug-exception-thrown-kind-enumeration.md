---
title: Enumerazione SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6fe5b308ea75956d9e5826b4daadaef3a823141f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="scripterrordebugexceptionthrownkind-enumeration"></a>Enumerazione SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Indica il tipo di eccezione generata. Questa enumerazione viene utilizzata per la [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) metodo.  
  
> [!IMPORTANT]
>  Queste costanti sono implementate da PDM versione 11.0 e successiva. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Valore|Descrizione|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|L'eccezione è un'eccezione first-chance.|  
|ETK_USER_UNHANDLED|0x00000001|L'eccezione non è gestita nel codice utente.|  
|ETK_UNHANDLED|0x00000002|L'eccezione non è gestita nel codice.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)