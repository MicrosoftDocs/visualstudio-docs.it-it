---
title: IDebugDocumentTextAuthor::InsertText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextAuthor.InsertText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextAuthor::InsertText
ms.assetid: ef4e6a5b-8efa-4290-b498-c0f8a6aac09b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 678e2429e98f268d65f9c29704e2e9d5a1a8538c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160719"
---
# <a name="idebugdocumenttextauthorinserttext"></a>IDebugDocumentTextAuthor::InsertText
Inserisce il nuovo testo nel documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT InsertText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToInsert,  
   OLECHAR  pcharText[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cCharacterPosition`  
 [in] Posizione in cui inserire il testo.  
  
 `cNumToInsert`  
 [in] Numero di caratteri da inserire.  
  
 `pcharText[]`  
 [in] Un buffer contenente i caratteri da inserire.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo consente di inserire nuovo testo nel documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentTextAuthor](../../winscript/reference/idebugdocumenttextauthor-interface.md)   
 [IDebugDocumentTextAuthor::RemoveText](../../winscript/reference/idebugdocumenttextauthor-removetext.md)