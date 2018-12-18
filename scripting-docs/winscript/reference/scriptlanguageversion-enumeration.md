---
title: Enumerazione SCRIPTLANGUAGEVERSION | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4cee2966b326ca7b4c258ffdb85b6fa71d90992
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="scriptlanguageversion-enumeration"></a>Enumerazione SCRIPTLANGUAGEVERSION
Specifica i possibili versioni di scripting.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Valori di enumerazione  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|La versione predefinita. Il valore intero è 0.|  
|SCRIPTLANGUAGEVERSION_5_7|Gli script di Windows versione 5.7. Il valore intero è 1.|  
|SCRIPTLANGUAGEVERSION_5_8|Versione 5.8 gli script di Windows. Il valore intero è 2.|  
|SCRIPTLANGUAGEVERSION_MAX|La versione massima. Il valore intero è 255.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e codici di errore dello script ActiveX](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)