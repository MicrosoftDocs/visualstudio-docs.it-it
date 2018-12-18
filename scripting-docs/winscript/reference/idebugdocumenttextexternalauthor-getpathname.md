---
title: IDebugDocumentTextExternalAuthor::GetPathName | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentTextExternalAuthor.GetPathName
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentTextExternalAuthor::GetPathName
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93e5c27422d6b348d8c961d1555bfce07183e9e4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
Restituisce il nome di file e percorso completo del documento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrLongName`  
 [out] Stringa contenente il nome di file e percorso completo.  
  
 `pfIsOriginalFile`  
 [out] Valore booleano che indica se il nome di percorso e il riferimento al documento originale.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Impossibile creare il file di origine o determinato.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce il nome di file e percorso completo del documento.  
  
 Se `pfIsOriginalFile` è FALSE, il percorso e nome file in `pbstrLongName` fare riferimento a un file temporaneo appena creato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentTextExternalAuthor](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)