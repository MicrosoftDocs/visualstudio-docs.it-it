---
title: IDebugDocumentHelper::DefineScriptBlock | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.DefineScriptBlock
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b6ec86dacc2e3a8f3d9e28a6db744b778ff01eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Indica che un determinato intervallo di caratteri è un blocco di script che viene gestito dal motore di script specificato per il supporto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ulCharOffset`  
 [in] Posizione di inizio del blocco di script.  
  
 `cChars`  
 [in] Numero di caratteri nel blocco di script.  
  
 `pas`  
 [in] Il motore di script per questo blocco di script.  
  
 `fScriptlet`  
 [in] Flag che indica se il blocco di script è scriptlet.  
  
 `pdwSourceContext`  
 [out] Il contesto di origine per il blocco di script.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Uno smart host è possibile utilizzare questo metodo quando i documenti contengono blocchi di script incorporati. Un motore di lingua è possibile utilizzare questo metodo quando il codice contiene script incorporati per le altre lingue.  
  
 Il motore di script è responsabile di tutte le sintassi colorazione del codice contesto ricerche e nel blocco di script.  
  
 Il `DefineScriptBlock` deve essere chiamato dopo il testo è stato aggiunto (ad esempio, usando il `IDebugDocumentHelper::AddDBCSText` (metodo)) ma lo script prima di blocco è stato analizzato (ad esempio, usando il `IActiveScriptParse ::ParseScriptText` (metodo)).  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)