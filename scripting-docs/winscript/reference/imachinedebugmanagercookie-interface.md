---
title: Interfaccia IMachineDebugManagerCookie | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a03b959a7eb09f3b85530bbba07d1d2dc7f8948a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagercookie-interface"></a>Interfaccia IMachineDebugManagerCookie
Simile al `IMachineDebugManager` interfaccia, il `IMachineDebugManagerCookie` interfaccia supporta i cookie di debug.  
  
 Questa interfaccia (insieme al `IDebugCookie` interface) consentono di eseguire script in un processo del debugger di script senza richiedere che il debugger di tenere traccia di tali script.  
  
 Un debugger di script chiama il `IDebugCookie::SetDebugCookie` metodo nel processo di Debug Manager (PDM). Quindi, PDM invia questo cookie insieme a qualsiasi richiesta per aggiungere o rimuovere un'applicazione di script a o dal Machine Debug Manager (MDM), utilizzando i metodi del `IMachineDebugManagerCookie` interfaccia. La gestione dei dispositivi mobili notifica quindi ogni debugger della modifica, ad eccezione di quello con tale cookie.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IMachineDebugManagerCookie` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Aggiunge un'applicazione per l'esecuzione elenco di applicazioni.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Restituisce un enumeratore dell'elenco corrente delle applicazioni in esecuzione.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Rimuove l'esecuzione di un'applicazione elenco di applicazioni.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)   
 [Interfaccia IDebugCookie](../../winscript/reference/idebugcookie-interface.md)