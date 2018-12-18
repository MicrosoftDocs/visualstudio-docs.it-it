---
title: IDebugDocumentTextEvents::onReplaceText | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onReplaceText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onReplaceText
ms.assetid: 3cb053c4-1f7f-4aed-aee6-f8a9e9e69d29
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1cbe022113e8a97dc31b4cf5a2286ec0b5096d3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttexteventsonreplacetext"></a>IDebugDocumentTextEvents::onReplaceText
Indica che è stato sostituito il testo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT onReplaceText(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToReplace  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cCharacterPosition`  
 [in] Posizione del carattere del primo carattere è stato sostituito.  
  
 `cNumToReplace`  
 [in] Il numero di caratteri sostituiti.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo indica che è stato sostituito il testo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)