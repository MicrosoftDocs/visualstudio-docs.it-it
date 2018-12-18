---
title: IDebugDocumentInfo::GetName | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentInfo.GetName
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentInfo::GetName
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da369c328c2f92915c60b1c50517938bf76d5202
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Restituisce il nome del documento specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dnt`  
 [in] Tipo del nome del documento da restituire.  
  
 `pbstrName`  
 [out] Stringa contenente il nome.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Il nome del documento specificato non è noto.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce il nome del documento specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [Enumerazione DOCUMENTNAMETYPE](../../winscript/reference/documentnametype-enumeration.md)