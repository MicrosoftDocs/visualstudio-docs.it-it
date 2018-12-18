---
title: IActiveScriptSiteWindow::GetWindow | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.GetWindow
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_GetWindow
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3257ac5632a2f3d713b6329a9a1eeebc4415851
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitewindowgetwindow"></a>IActiveScriptSiteWindow::GetWindow
Recupera l'handle a una finestra che può agire come proprietario di una finestra popup che deve visualizzare il modulo di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `phwnd`  
 [out] Indirizzo di una variabile che riceve l'handle di finestra.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se ha esito positivo, o `E_FAIL` se si è verificato un errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo è simile al `IOleWindow::GetWindow` metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)