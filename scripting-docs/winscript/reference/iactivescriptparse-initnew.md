---
title: IActiveScriptParse::InitNew | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptParse.InitNew
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_InitNew
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e34094bcc25c0316fa670f570d8b2664acc0ba78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Inizializza il motore di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se ha esito positivo, o `E_FAIL` se si è verificato un errore durante l'inizializzazione.  
  
## <a name="remarks"></a>Note  
 Prima di poter utilizzare il motore di script, è necessario chiamare uno dei metodi seguenti: `IPersist*::Load`, `IPersist*::InitNew`, o `IActiveScriptParse::InitNew`. La semantica di questo metodo è identica a `IPersistStreamInit::InitNew`, in quanto questo metodo indica al motore di scripting per l'inizializzazione. Si noti che non è valido di chiamare `IPersist*::InitNew` o `IActiveScriptParse::InitNew` e `IPersist*::Load`, non è consentito chiamare `IPersist*::InitNew`, `IActiveScriptParse::InitNew`, o `IPersist*::Load` più volte.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)