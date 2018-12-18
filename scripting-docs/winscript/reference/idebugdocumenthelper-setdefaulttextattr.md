---
title: IDebugDocumentHelper::SetDefaultTextAttr | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDefaultTextAttr
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDefaultTextAttr
ms.assetid: 019a4191-0019-4376-bf70-89b33e7369de
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49b6da490e1eefe13ae21a9875952032585372f2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelpersetdefaulttextattr"></a>IDebugDocumentHelper::SetDefaultTextAttr
Imposta gli attributi predefiniti da utilizzare per il testo che non è in un blocco di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SetDefaultTextAttr(  
   SOURCE_TEXT_ATTR  staTextAttr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `staTextAttr`  
 Gli attributi di testo di origine predefinito.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 A meno che gli attributi predefiniti vengono modificati da questo metodo, gli attributi predefiniti per il testo all'esterno di un blocco di script è SOURCETEXT_ATTR_NONSOURCE. L'interfaccia utente è possibile utilizzare queste informazioni per contrassegnare il testo all'esterno di blocchi di script in sola lettura.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Enumerazione SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)