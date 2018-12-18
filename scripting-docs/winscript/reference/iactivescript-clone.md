---
title: IActiveScript::Clone | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.Clone
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b0b83bcf86bcc56701d11f22640df966334697b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Clona il motore di script corrente (meno qualsiasi stato corrente dell'esecuzione), la restituzione di un motore di script caricato che non dispone di alcun sito nel thread corrente. Le proprietà di questo nuovo motore di script sarà identiche alle proprietà del che motore di script originale sarà nella se ne sono stati eseguita la transizione allo stato inizializzato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppscript`  
 [out] Indirizzo di una variabile che riceve un puntatore di [IActiveScript](../../winscript/reference/iactivescript.md) interfaccia del motore di scripting clonato. L'host deve creare un sito e chiamare il [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) metodo sul nuovo motore di scripting affinché sia nello stato non inizializzato e quindi utilizzabile.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_NOTIMPL`|Questo metodo non è supportato.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di script non è ancora caricato o inizializzato).|  
  
## <a name="remarks"></a>Note  
 Il `IActiveScript::Clone` metodo è un'ottimizzazione di `IPersist*::Save`, `CoCreateInstance`, e `IPersist*::Load`, pertanto lo stato del motore di script nuovo deve essere lo stesso come se lo stato del motore di scripting originale sono stato salvato e caricato in un nuovo motore di scripting. Gli elementi denominati vengono duplicati nel motore di scripting clonato, ma puntatori a oggetti specifici per ogni elemento sono dimenticati e vengono forniti con il [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) metodo. In questo modo un modello a oggetti identici con punti di ingresso per ogni thread (un modello di apartment) da utilizzare.  
  
 Questo metodo viene utilizzato per gli host server multithreading che è possono eseguire più istanze dello stesso script. Il motore di script può restituire `E_NOTIMPL`, nel qual caso l'host può ottenere lo stesso risultato duplicando allo stato persistente e creare una nuova istanza del motore di script con un `IPersist*` interfaccia.  
  
 Questo metodo può essere chiamato dal thread non di base senza callout non in base a oggetti host o al [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)