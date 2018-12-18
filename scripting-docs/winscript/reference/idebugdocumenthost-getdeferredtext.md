---
title: IDebugDocumentHost::GetDeferredText | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHost.GetDeferredText
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ace3bdbfef143a3307d81455788a1e81788cb50b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Restituisce un intervallo di caratteri che sono stati aggiunti tramite il `IDebugDocumentHelper::AddDeferredText` (metodo), nel documento host originale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwTextStartCookie`  
 [in] Cookie definito host che rappresenta la posizione iniziale del testo.  
  
 `pcharText`  
 [in, out] Un buffer di testo di carattere. Questo metodo non restituisce i caratteri se questo parametro è `NULL`.  
  
 `pstaTextAttr`  
 [in, out] Un buffer di attributi del carattere. Questo metodo non restituisce gli attributi se questo parametro è `NULL`.  
  
 `pcNumChars`  
 [in, out] Indica il numero effettivo di caratteri/attributi restituiti. Questo parametro deve essere impostato su zero prima di chiamare questo metodo.  
  
 `cMaxChars`  
 [in] Numero massimo di caratteri da restituire.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|Il metodo non è implementato.|  
  
## <a name="remarks"></a>Note  
 Questo metodo può restituire `E_NOTIMPL`, se l'host non chiama `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
>  Questo metodo restituisce il testo del documento originale. L'host non tenere traccia delle modifiche o altre modifiche al documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Enumerazione SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)