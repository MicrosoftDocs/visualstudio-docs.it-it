---
title: IDebugExpressionContext::GetLanguageInfo | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExpressionContext.GetLanguageInfo
apilocation: jscript.dll
helpviewer_keywords: IDebugExpressionContext::GetLanguageInfo
ms.assetid: 35e25662-0b2a-4c3f-bce4-f01726bc04a8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68c22d5dfcd16fb3d8f1dc3750bbfb23c4821176
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressioncontextgetlanguageinfo"></a>IDebugExpressionContext::GetLanguageInfo
Restituisce un nome e GUID per la lingua a cui appartiene questo contesto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetLanguageInfo(  
   BSTR*  pbstrLanguageName,  
   GUID*  pLanguageID  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrLanguageName`  
 [out] Il nome della lingua.  
  
 `pLanguageID`  
 [out] Id univoco per la lingua.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce un nome e GUID per la lingua a cui appartiene questo contesto.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugExpressionContext](../../winscript/reference/idebugexpressioncontext-interface.md)