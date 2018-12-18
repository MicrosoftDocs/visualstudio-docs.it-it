---
title: IActiveScriptAuthor::AddScriptlet | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b21f906a73a313bf775683ba63738adb25af0007
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Aggiunge codice scriptlet come figlio del livello radice `IScriptNode` oggetto. Nell'host, il nome completo dello scriptlet può includere solo due livelli.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszDefaultName`  
 [in] L'indirizzo del nome predefinito per associare lo scriptlet.  
  
 `pszCode`  
 [in] L'indirizzo del testo scriptlet.  
  
 `pszItemName`  
 [in] Ottiene o imposta l'indirizzo del buffer dell'identificatore del nome completo scriptlet nell'host di primo livello.  
  
 `pszSubItemName`  
 [in] Ottiene o imposta l'indirizzo del buffer dell'identificatore del nome completo scriptlet nell'host di secondo livello. Impostare su NULL se il nome contiene un solo livello.  
  
 `pszEventName`  
 [in] L'indirizzo di un buffer che contiene il nome dell'evento per il quale lo scriptlet è un gestore eventi.  
  
 `pszDelimiter`  
 [in] L'indirizzo del delimitatore di fine-di--blocco di script. Quando `pszCode` viene analizzata da un flusso di testo, l'host Usa in genere un delimitatore (ad esempio due virgolette singole), per individuare la fine del blocco di script. Se un delimitatore non contrassegna la fine del blocco di script, impostare questo parametro su NULL.  
  
 `dwCookie`  
 [in] Un valore definito dall'applicazione che viene utilizzato per associare lo scriptlet con un oggetto host.  
  
 `dwFlags`  
 [in] Non usato.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)