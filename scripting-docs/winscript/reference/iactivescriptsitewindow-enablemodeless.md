---
title: IActiveScriptSiteWindow::EnableModeless | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSiteWindow.EnableModeless
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7099fe7d13a1cb3231e67049104722af9373d7a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
Fa sì che l'host abilitare o disabilitare la finestra principale, nonché eventuali finestre di dialogo non modale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `fEnable`  
 [in] Flag che, se `TRUE`, consente la finestra principale e le finestre di dialogo non modale o, se `FALSE`, li disabilita.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se ha esito positivo, o `E_FAIL` se si è verificato un errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo è identico per i `IOleInPlaceFrame::EnableModeless` metodo.  
  
 Chiamate a questo metodo possono essere nidificate.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)