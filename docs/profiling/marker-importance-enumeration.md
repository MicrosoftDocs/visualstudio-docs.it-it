---
title: Enumerazione marker_importance | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords: Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ae7bb9f300a1d57707966a3b4dbae202eea78d8c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="markerimportance-enumeration"></a>Enumerazione marker_importance
Rappresenta il livello di importanza di un marcatore del visualizzatore di concorrenza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
enum marker_importance;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="values"></a>Valori  
  
|nome|Descrizione|  
|----------|-----------------|  
|`critical_importance`|Specifica che il marcatore è di importanza critica.|  
|`high_importance`|Specifica che il marcatore è di elevata importanza.|  
|`low_importance`|Specifica che il marcatore è di scarsa importanza.|  
|`normal_importance`|Specifica che il marcatore è di normale importanza.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** cvmarkersobj.h  
  
 **Spazio dei nomi:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Vedere anche  
 [Spazio dei nomi diagnostic](../profiling/diagnostic-namespace.md)