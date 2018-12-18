---
title: IDebugEngine3 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine3
helpviewer_keywords: IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f601cd38b5546d79f97e1c15a7c33c5de7df5d03
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine3"></a>IDebugEngine3
Rappresenta un motore di debug singolo (DE) che controlla il debug di uno o più moduli.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata da un DE personalizzato (se supporta i simboli) per abilitare lo stato JustMyCode. Questa interfaccia deve essere implementata per la Germania se supporta JustMyCode e simboli.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene chiamata dal gestore di sessione di debug (SDM) per passare alle opzioni utente per percorsi da cui caricare i simboli. Viene inoltre chiamato per impostare il GUID del modulo quando ne viene creata un'istanza (questo GUID è basato su metriche di registrazione del modulo di gestione). Il SDM chiama anche questa interfaccia per impostare lo stato JustMyCode e impostare tutte le eccezioni note con il debugger a uno stato specificato.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi ereditati da [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), `IDebugEngine3` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Imposta il percorso o i percorsi che la Germania utilizzerà per la ricerca per i simboli di debug.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Carica i simboli per tutti i moduli che non sono ancora stati caricati i simboli.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Indica la Germania JustMyCode sui dati.|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Imposta il GUID DE dalle metriche.|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Impostare tutte le eccezioni in attesa su uno stato specificato.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)