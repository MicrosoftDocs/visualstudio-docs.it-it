---
title: Enumerazione DOCUMENTNAMETYPE | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DOCUMENTNAMETYPE
apilocation:
- scrobj.dll
helpviewer_keywords:
- DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0bd21dddd209f21ae64ea2775bbaa0da226f077
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="documentnametype-enumeration"></a>Enumerazione DOCUMENTNAMETYPE
Descrive quale tipo richiedere per un documento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,} DOCUMENTNAMETYPE;  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|Ottiene il nome visualizzato nella struttura dell'applicazione.|  
|DOCUMENTNAMETYPE_TITLE|Ottiene il nome visualizzato sulla barra del titolo del visualizzatore.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Ottiene il nome del file senza percorso.|  
|DOCUMENTNAMETYPE_URL|Ottiene l'URL del documento.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Ottiene il titolo con enumerazione per l'identificazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)