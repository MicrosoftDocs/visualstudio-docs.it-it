---
title: IDebugCoreServer3 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer3
helpviewer_keywords: IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9456ddbe7588217e4864f6f8c8b994bc9323ab76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Questa interfaccia consente di accedere alle informazioni sul server che in cui viene eseguito il processo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio implementa questa interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Utilizzare [QueryInterface](/cpp/atl/queryinterface) per questa interfaccia da ottenere un [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfaccia. Una chiamata a [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) può restituire anche questa interfaccia. Questa interfaccia viene utilizzata in genere da un fornitore di porta personalizzato per avviare i programmi in un server (locale o remoto).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi nel [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfaccia, implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Recupera il nome del server.|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Recupera una versione breve del nome del server|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Indica i motori di debug specifiche connettersi automaticamente ai processi all'avvio di tali processi.|  
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Recupera un codice di errore specifico quando automatico collegamento ha esito negativo.|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Crea un'istanza di un motore di debug nel server.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Recupera un flag che indica se il server è nello stesso computer del chiamante.|  
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Recupera un valore che indica il protocollo utilizzato per comunicare con il server.|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Disabilita tutte le connessione automatica le impostazioni per tutti i motori di debug che conosce questo server.|  
  
## <a name="remarks"></a>Note  
 Un porta personalizzata di fornitore riceve il [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfaccia in una chiamata a [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md). Il `IDebugCoreServer3` interfaccia può essere ottenuta da tale interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)