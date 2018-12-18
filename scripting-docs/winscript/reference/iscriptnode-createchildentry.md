---
title: 'IScriptNode:: CreateChildEntry | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8fcc010efe8fcf30a8f467dd94befff54bc5fac5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
Aggiunge un'istanza figlio `IScriptEntry`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `isn`  
 [in] Indice dell'elemento figlio dell'elemento padre.  
  
 `dwCookie`  
 [in] Un valore definito dall'applicazione utilizzato per associare la voce figlio con l'oggetto host.  
  
 `pszDelimiter`  
 [in] L'indirizzo del delimitatore di fine-di--blocco di script. Per l'analisi, l'host Usa in genere un delimitatore (ad esempio due virgolette singole), per individuare la fine del blocco di script.  
  
 Il delimitatore consente lo script di creazione del motore per fornire la pre-elaborazione. Il motore potrebbe sostituire, ad esempio, una virgoletta singola con due virgolette singole da utilizzare come delimitatore. Il motore determina la modalità in cui viene utilizzato il delimitatore.  
  
 Se un delimitatore non contrassegnare la fine del blocco di script, impostato su NULL.  
  
 `ppse`  
 [out] L'indirizzo di una variabile che riceve un puntatore di `IScriptEntry` interfaccia dell'istanza figlio.  
  
 Per `IScriptNode` gli oggetti che rappresentano una pagina Web, questo parametro restituisce un `IScriptEntry` istanza che specifica un blocco di script.  
  
 Per `IScriptEntry` gli oggetti che rappresentano un blocco di script, questo parametro restituisce un `IScriptEntry` istanza che specifica un oggetto funzione.  
  
 Per `IScriptEntry` gli oggetti che rappresentano una funzione dell'oggetto, questo metodo ha esito negativo.  
  
 Per `IScriptScriptlet` oggetti, questo metodo ha esito negativo.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Il `IScriptNode` interfaccia rappresenta una pagina Web o sui suoi elementi. Il `IScriptEntry` interfaccia (derivata da `IScriptNode`) rappresenta un blocco di script o un oggetto funzione. Il `IScriptScriptlet` interfaccia (derivata da `IScriptEntry`) rappresenta un gestore eventi.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)