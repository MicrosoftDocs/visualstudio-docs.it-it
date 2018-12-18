---
title: IDebugDocumentHelper::SetShortName | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.SetShortName
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::SetShortName
ms.assetid: 811a444b-0ea4-4374-9d4c-4f7713bdd1ff
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 69674b5639c7d59a4551192177d9ebdafd27ac99
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelpersetshortname"></a>IDebugDocumentHelper::SetShortName
Imposta il nome breve per il documento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SetShortName(  
   LPCOLESTR  pszShortName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszShortName`  
 [in] Stringa con terminazione null contenente il nome breve del documento.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo imposta un nuovo nome breve per il documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)