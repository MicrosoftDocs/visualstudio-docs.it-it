---
title: IApplicationDebuggerUI::BringDocumentToTop | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IApplicationDebuggerUI.BringDocumentToTop
apilocation: scrobj.dll
helpviewer_keywords: IApplicationDebuggerUI::BringDocumentToTop
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57b76f44eeeaad1946d40435c770b0687b82fd17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
Visualizza la finestra contenente il documento di debug specificata verso l'alto nel debugger interfaccia utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pddt`  
 [in] Eseguire il debug di documento per portare in primo piano nell'interfaccia utente del debugger.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_INVALIDARG`|Il documento non è noto.|  
  
## <a name="remarks"></a>Note  
 Questo metodo visualizza la finestra che contiene il documento di debug specificata verso l'alto nel debugger di interfaccia utente.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)