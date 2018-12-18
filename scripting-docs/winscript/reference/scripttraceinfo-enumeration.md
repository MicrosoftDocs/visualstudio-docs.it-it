---
title: Enumerazione SCRIPTTRACEINFO | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc1902b290a8024679cef12d503e94de4923defb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="scripttraceinfo-enumeration"></a>Enumerazione SCRIPTTRACEINFO
Rappresenta l'evento di script che si sta analizzando. Utilizzato nel [metodo iactivescriptsitetraceinfo:: Sendscripttraceinfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef enum tagSCRIPTTRACEINFO {      SCRIPTTRACEINFO_SCRIPTSTART = 0,      SCRIPTTRACEINFO_SCRIPTEND   = 1,      SCRIPTTRACEINFO_COMCALLSTART    = 2,      SCRIPTTRACEINFO_COMCALLEND  = 3,      SCRIPTTRACEINFO_CREATEOBJSTART  = 4,      SCRIPTTRACEINFO_CREATEOBJEND    = 5,      SCRIPTTRACEINFO_GETOBJSTART = 6,      SCRIPTTRACEINFO_GETOBJEND   = 7,  } SCRIPTTRACEINFO ;  
```  
  
## <a name="enumeration-values"></a>Valori di enumerazione  
  
|||  
|-|-|  
|SCRIPTTRACEINFO_SCRIPTSTART|Inizio di uno script.|  
|SCRIPTTRACEINFO_SCRIPTEND|La fine dello script.|  
|SCRIPTTRACEINFO_COMCALLSTART|Inizio di una chiamata COM.|  
|SCRIPTTRACEINFO_COMCALLEND|La fine di una chiamata COM.|  
|SCRIPTTRACEINFO_CREATEOBJSTART|Inizio della creazione dell'oggetto.|  
|SCRIPTTRACEINFO_CREATEOBJEND|La fine della creazione dell'oggetto.|  
|SCRIPTTRACEINFO_GETOBJSTART|Inizio di una chiamata di GetObject.|  
|SCRIPTTRACEINFO_GETOBJEND|La fine di una chiamata di GetObject.|