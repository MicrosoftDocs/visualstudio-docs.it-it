---
title: IDebugDocumentHelper::Init | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Init
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45cd57e4ba9e86bf84f927f487c637d61aa5339b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
Il `Init` metodo inizializza un helper del documento di debug con un nome e attributi iniziali.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pda`  
 [in] L'applicazione di debug associata a questo documento.  
  
 `pszShortName`  
 [in] Stringa con terminazione null contenente il nome breve del documento.  
  
 `pszLongName`  
 [in] Stringa con terminazione null contenente il nome lungo del documento.  
  
 `docAttr`  
 [in] Specifica gli attributi di documento di testo.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo inizializza un helper del documento di debug con un nome e attributi iniziali.  
  
 Questo documento non viene visualizzato nella struttura solo `IDebugDocumentHelper::Attach` viene chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Costanti TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)