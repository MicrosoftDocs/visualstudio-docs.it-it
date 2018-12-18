---
title: IActiveScriptSiteWindow | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptSiteWindow interface
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3043a3c36b2f1ebdf439f22b1de19dd559e50cfa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Questa interfaccia viene implementata dagli host che supporta un'interfaccia utente per l'oggetto stesso come [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) . Gli host che non supportano l'interfaccia utente, ad esempio server, non implementare il `IActiveScriptSiteWindow` interfaccia. Il motore di script accede a questa interfaccia chiamando `QueryInterface` da `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Recupera l'handle di finestra che può agire come proprietario di una finestra popup che deve visualizzare il modulo di script.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Fa sì che l'host abilitare o disabilitare la finestra principale, nonché eventuali finestre di dialogo non modale.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)