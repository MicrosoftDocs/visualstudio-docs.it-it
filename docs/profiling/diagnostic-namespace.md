---
title: Spazio dei nomi diagnostic | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords: Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3fb9b831562e2d9e4ce7d686f49ac484d58f6804
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="diagnostic-namespace"></a>Spazio dei nomi diagnostic
Lo spazio dei nomi `diagnostics` offre funzionalità per l'emissione di marcatori del visualizzatore di concorrenza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
namespace diagnostic;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="classes"></a>Classi  
  
|nome|Descrizione|  
|----------|-----------------|  
|[Classe marker_series](../profiling/marker-series-class.md)|Rappresenta un canale seriale di eventi generati da un singolo provider.|  
|[Classe span](../profiling/span-class.md)|Definisce una fase dell'applicazione.|  
  
### <a name="enumerations"></a>Enumerazioni  
  
|nome|Descrizione|  
|----------|-----------------|  
|[Enumerazione marker_importance](../profiling/marker-importance-enumeration.md)|Rappresenta il livello di importanza di un marcatore del visualizzatore di concorrenza.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** cvmarkersobj.h  
  
 **Spazio dei nomi:** Concurrency  
  
## <a name="see-also"></a>Vedere anche  
 [Spazio dei nomi Concurrency (visualizzatore di concorrenza)](../profiling/concurrency-namespace-concurrency-visualizer.md)