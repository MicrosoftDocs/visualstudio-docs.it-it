---
title: IDebugDocumentText::GetText | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentText.GetText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a1006304974fab4959ad6313ffdc26793cdd345
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Recupera i caratteri e/o gli attributi associati a un intervallo di posizione del carattere.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cCharacterPosition`  
 [in] Posizione iniziale dell'intervallo di caratteri della posizione.  
  
 `pcharText`  
 [in, out] Un buffer di testo di carattere. Il buffer deve essere sufficientemente grande da contenere `cMaxChars` caratteri. Se questo parametro è NULL, il metodo non restituisce i caratteri.  
  
 `pstaTextAttr`  
 [in, out] Un buffer di attributi del carattere. Il buffer deve essere sufficientemente grande da contenere `cMaxChars` caratteri. Se questo parametro è NULL, il metodo non restituisce gli attributi.  
  
 `pcNumChars`  
 [in, out] Ha restituito il numero di caratteri e attributi. Questo parametro deve essere impostato su zero prima di chiamare questo metodo.  
  
 `cMaxChars`  
 [in] Numero di caratteri nell'intervallo di posizione di carattere. Specifica inoltre il numero massimo di caratteri da restituire.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo recupera i caratteri e/o gli attributi associati a un intervallo di posizione del carattere. L'intervallo di posizione del carattere è specificato da una posizione di carattere e un numero di caratteri.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [Enumerazione SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)