---
title: Interfaccia IJsDebugProcess | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2a81104f51ca1a66c493779146b7eaa102ea300
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugprocess-interface"></a>Interfaccia IJsDebugProcess
Fornisce routine di controllo e controllare il processo di destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint Method](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Imposta il punto di interruzione nella posizione del documento specificata.|  
|[Metodo IJsDebugProcess::CreateStackWalker](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Metodo factory per walker dello stack.|  
|[Metodo IJsDebugProcess::PerformAsyncBreak](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Inserisce il motore di script in modalità di interruzione in modo da interrompere l'esecuzione successiva istruzione di script.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)