---
title: IActiveScriptParse32::InitNew | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 31de8258ae13855741c6dd5ca9e4ff2c589e97bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Inizializza il motore di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se ha esito positivo, o `E_FAIL` se si è verificato un errore durante l'inizializzazione.  
  
## <a name="remarks"></a>Note  
 Prima di poter utilizzare il motore di script, è necessario chiamare uno dei metodi seguenti: `IPersist*::Load`, `IPersist*::InitNew`, o `IActiveScriptParse32::InitNew`. La semantica di questo metodo è identica a `IPersistStreamInit::InitNew`, in quanto questo metodo indica al motore di scripting per l'inizializzazione. Si noti che non è valido di chiamare `IPersist*::InitNew` o `IActiveScriptParse32::InitNew` e `IPersist*::Load`, non è consentito chiamare `IPersist*::InitNew`, `IActiveScriptParse32::InitNew`, o `IPersist*::Load` più volte.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)