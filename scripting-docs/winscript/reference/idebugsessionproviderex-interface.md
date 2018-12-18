---
title: Interfaccia IDebugSessionProviderEx | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 545b60f13e86e59143ce0e57f454b13f61041f11
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsessionproviderex-interface"></a>Interfaccia IDebugSessionProviderEx
L'interfaccia primaria fornita da un debugger IDE per abilitare il debug avviato dall'host e lingua. Stabilisce una sessione di debug per un'applicazione in esecuzione. Questa interfaccia viene implementata dal gestore di eseguire il Debug del computer.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IDebugSessionProviderEx` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Determina se il debug JIT è possibile con l'applicazione specificata.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Avvia una sessione di debug con l'applicazione specificata.|