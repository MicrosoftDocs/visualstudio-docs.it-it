---
title: IDebugApplication::RemoveGlobalExpressionContextProvider | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.RemoveGlobalExpressionContextProvider
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::RemoveGlobalExpressionContextProvider
ms.assetid: ace638a3-ed34-4d20-8404-45c684aaaf1a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 791d6a3a237c36c123aea662dc4bb933b97d35d3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationremoveglobalexpressioncontextprovider"></a>IDebugApplication::RemoveGlobalExpressionContextProvider
Rimuove un provider di contesto dell'espressione globale da questa applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT RemoveGlobalExpressionContextProvider(  
   DWORD_PTR  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwCookie`  
 [in] Il cookie restituito dal `AddGlobalExpressionContextProvider` metodo quando il provider di contesto globale è stato aggiunto.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Il `RemoveGlobalExpressionContextProvider` metodo rimuove un provider di contesto dell'espressione globale da questa applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)   
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)