---
title: IBindEventHandler::BindHandler | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IBindEventHandler.BindHandler
apilocation: scrobj.dll
helpviewer_keywords: IBindEventHandler::BindHandler
ms.assetid: 87909828-2224-4bb1-a6c9-dfe715ac4c9b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66de7cba8181ce9f3d683a90e4d7dd51e63d4779
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ibindeventhandlerbindhandler"></a>IBindEventHandler::BindHandler
Associa un evento a un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT BindHandler(  
   LPCOLESTR   pstrEvent,  
   IDispatch*  pdisp  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrEvent`  
 [in] Specifica l'evento da gestire.  
  
 `pdisp`  
 [in] Specifica l'oggetto per gestire l'evento.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo associa un evento a un oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IBindEventHandler](../../winscript/reference/ibindeventhandler-interface.md)