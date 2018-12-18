---
title: IActiveScriptAuthor::RemoveNamedItem | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.RemoveNamedItem
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::RemoveNamedItem
ms.assetid: 1173ef46-39a5-4bc1-8e0c-89259a16be16
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f3acc7d61d63ce4fb4fe53729ce43324b9718a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorremovenameditem"></a>IActiveScriptAuthor::RemoveNamedItem
Rimuove un `NamedItem` oggetto dallo spazio dei nomi dello script del motore di creazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszName`  
 [in] L'indirizzo del buffer che identifica il `NamedItem` oggetto da rimuovere.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`S_FALSE`|Il `NamedItem` oggetto non è presente nello spazio dei nomi dello script del motore di creazione.|  
  
## <a name="remarks"></a>Note  
 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) viene utilizzato per inserire il `NamedItem` oggetto nello script di creazione dello spazio dei nomi del motore.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)