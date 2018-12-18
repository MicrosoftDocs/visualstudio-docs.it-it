---
title: IScriptNode::CreateChildHandler | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode.CreateChildHandler
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff2ba40d1570e23f0256bd34ca8aff0f8d77ce5c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Aggiunge un scriptlet come istanza figlio di un `IScriptNode`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszDefaultName`  
 [in] L'indirizzo del nome predefinito per associare lo scriptlet.  
  
 `prgpszNames`  
 [in, size_is (`cpszNames`)] elenco degli identificatori di specificare il nome completo dell'host.  
  
 `cpszNames`  
 [in] Il numero di identificatori nel `prgpszNames` parametro.  
  
 `pszEvent`  
 [in] L'indirizzo del buffer che identifica il nome dell'evento associato lo scriptlet.  
  
 `pszDelimiter`  
 [in] L'indirizzo del delimitatore di fine-di--blocco di script. Per l'analisi, l'host Usa in genere un delimitatore (ad esempio due virgolette singole), per individuare la fine del blocco di script.  
  
 Il delimitatore consente la pre-elaborazione dallo script del motore di creazione. Il motore potrebbe sostituire, ad esempio, una virgoletta singola con due virgolette singole da utilizzare come delimitatore. Il motore determina la modalità in cui viene utilizzato il delimitatore.  
  
 Se non viene utilizzato alcun delimitatore per identificare la fine del blocco di script, impostato su NULL.  
  
 `ptiSignature`  
 [in] Le informazioni sul tipo per un oggetto funzione.  
  
 `iMethodSignature`  
 [in] L'indice di una funzione di `ITypeInfo``ptiSignature` parametro.  
  
 `isn`  
 [in] Indice dell'elemento figlio dell'elemento padre.  
  
 `dwCookie`  
 [in] Un valore definito dall'applicazione che viene utilizzato per associare la voce con l'oggetto host.  
  
 `ppse`  
 [out] L'indirizzo di una variabile che riceve un puntatore di `IScriptEntry` interfaccia dell'istanza figlio.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Scriptlet specifica un gestore eventi. Questo metodo crea scriptlet se viene chiamato un `IScriptNode` oggetto che rappresenta una pagina Web. Questo metodo non riesce se viene chiamato da altre interfacce.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)