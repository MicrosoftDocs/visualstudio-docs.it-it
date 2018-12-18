---
title: IDebugHelper::CreatePropertyBrowserEx | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugHelper.CreatePropertyBrowserEx
apilocation: pdm.dll
helpviewer_keywords: IDebugHelper::CreatePropertyBrowserEx
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9bc219ea5c2ff9ff2860d36cd475985d825ae59
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Restituisce un visualizzatore di proprietà che esegue il wrapping di una variante e consente la conversione dei valori di variante o tipi VARTYPE personalizzata alle stringhe.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pvar`  
 [in] Variante radice per esplorare.  
  
 `bstrName`  
 [in] Nome da assegnare alla radice.  
  
 `pdat`  
 [in] Thread in cui si desidera richiedere le proprietà. Se questo parametro è NULL, non viene eseguita alcun marshalling.  
  
 `pdf`  
 [in] Oggetto che fornisce formattazione personalizzata per le varianti.  
  
 `ppdob`  
 [out] Il Visualizzatore proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce un visualizzatore di proprietà che esegue il wrapping di una variante e consente la conversione dei valori di variante o tipi VARTYPE personalizzata alle stringhe.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [Interfaccia IDebugHelper](../../winscript/reference/idebughelper-interface.md)   
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)