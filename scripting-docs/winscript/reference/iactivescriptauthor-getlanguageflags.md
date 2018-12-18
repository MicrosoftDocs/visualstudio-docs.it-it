---
title: IActiveScriptAuthor::GetLanguageFlags | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetLanguageFlags
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6137f1cd77d2f305a9ff9d51ac49c214e4c4237b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Restituisce informazioni relative alla lingua.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pgrfasa`  
 [out] I flag che contengono informazioni relative alla lingua. Può essere una combinazione dei valori seguenti:  
  
|Costante|Valore|Descrizione|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|Il linguaggio preferenziale creazione dello script del gestore eventi tramite lo script di creazione motore invece che all'applicazione.|  
|fasaSupportInternalHandler|0x0002|Il linguaggio supporta i gestori di eventi di script creati dallo script del motore di creazione.|  
|fasaCaseSensitive|0x0004|Il linguaggio di scripting viene fatta distinzione tra maiuscole e minuscole.|  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Se lo script di creazione motore gestisce i gestori eventi, l'applicazione deve chiamare `CreateChildHandler` da un `IScriptEntry` oggetto. Crea un `IScriptScriptlet` oggetto che corrisponde al gestore dell'evento. Il motore aggiunge anche un gestore eventi per la voce di script. Il gestore dell'evento è una funzione vuota che contiene le informazioni sulla firma specificato.  
  
 Se l'applicazione gestisce i gestori eventi, questo deve chiamare `CreateChildHandler` da un `IScriptNode` oggetto che rappresenta un scriptlet gestore dell'evento. Crea un `IScriptScriptlet` oggetto che è associato lo scriptlet gestore dell'evento. L'applicazione dispone anche di aggiungere una funzione vuota come un evento gestore a un nuovo o esistente `IScriptEntry` oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)