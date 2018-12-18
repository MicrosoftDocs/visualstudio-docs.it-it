---
title: IDebugApplicationNode100::GetExcludedDocuments | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::GetExcludedDocuments
ms.assetid: d44583a7-0b0b-4799-b075-837ad1da1946
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ad8e8e2bbe8c643385bb4a989367d58d7c38725
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode100getexcludeddocuments"></a>IDebugApplicationNode100::GetExcludedDocuments
Ottiene i documenti di testo che sono nascosti per il filtro specificato.  
  
> [!IMPORTANT]
>  [Interfaccia IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) è implementata da PDM v di 10.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetExcludedDocuments(        [in] APPLICATION_NODE_EVENT_FILTER filter,        [out] TEXT_DOCUMENT_ARRAY* pDocuments        );  
```  
  
#### <a name="parameters"></a>Parametri  
 `filter`  
 Filtro.  
  
 `pDocuments`  
 Il set di documenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md)