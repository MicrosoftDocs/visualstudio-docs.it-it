---
title: Interfaccia IApplicationDebuggerUI | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IApplicationDebuggerUI interface
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbaa04f6790ffc4d80447a6745ca82cc8dba6802
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggerui-interface"></a>Interfaccia IApplicationDebuggerUI
Implementata dall'ambiente di sviluppo integrato (IDE) di debugger (oltre a `IApplicationDebugger`) per fornire maggiore controllo sull'interfaccia utente (UI) del debugger di un componente esterno.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IApplicationDebuggerUI` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Visualizza la finestra contenente il documento di debug specificata verso l'alto nel debugger interfaccia utente.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Apre la finestra contenente il contesto del documento specificata verso l'alto nell'interfaccia utente del debugger e scorre la finestra nel contesto.|