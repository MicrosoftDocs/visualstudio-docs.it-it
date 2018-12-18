---
title: IActiveScriptGarbageCollector::CollectGarbage | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07d5a00e04939331f85c4c74727aaf03b62814fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
L'host di Script attivo chiama questo metodo per avviare l'operazione di garbage collection.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Parametri  
 `scriptgctype`  
 [in] Il [enumerazione SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md) che specifica se la normale o completo di operazioni di garbage collection.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un valore HRESULT.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptGarbageCollector](../../winscript/reference/iactivescriptgarbagecollector-interface.md)