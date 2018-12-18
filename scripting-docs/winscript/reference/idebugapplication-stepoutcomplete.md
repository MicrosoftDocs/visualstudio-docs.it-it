---
title: IDebugApplication::StepOutComplete | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.StepOutComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::StepOutComplete
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c344f0316bda6ed5ef895c1b88ae7b1a6465e73
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
Notifica al gestore di debug di processo che un motore di lingua in modalità passo a passo sta per restituire al chiamante.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Motori di linguaggio chiamano questo metodo in modalità passo a passo, prima di restituire al chiamante. Il gestore di debug del processo utilizza questa opportunità per notificare a tutti gli altri motori di script che si devono interrompersi alla prima opportunità. Questa tecnica è il passaggio di più lingue vengono implementate le modalità.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)