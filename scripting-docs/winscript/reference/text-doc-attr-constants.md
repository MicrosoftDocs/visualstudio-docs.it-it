---
title: Costanti TEXT_DOC_ATTR | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- TEXT_DOC_ATTR
apilocation:
- scrobj.dll
helpviewer_keywords:
- TEXT_DOC_ATTR constants
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 130895e0e70b1044fab5d5ab406f940b036c37f0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="textdocattr-constants"></a>Costanti TEXT_DOC_ATTR
Descrivono gli attributi del documento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## <a name="constants"></a>Costanti  
  
|Costante|Valore|Descrizione|  
|--------------|-----------|-----------------|  
|TEXT_DOC_ATTR_READONLY|0x00000001|Il documento è di sola lettura.|  
|TEXT_DOC_ATTR_TYPE_PRIMARY|0x00000002|Il documento è il file primario di questa struttura documento.|  
|TEXT_DOC_ATTR_TYPE_WORKER|0x00000004|Il documento è un processo di lavoro.|  
|TEXT_DOC_ATTR_TYPE_SCRIPT|0x00000008|Il documento è un file di script.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)