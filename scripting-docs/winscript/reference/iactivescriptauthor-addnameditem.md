---
title: IActiveScriptAuthor::AddNamedItem | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83d2597f8468bb97d20da655a56a751191ec4b55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Aggiunge il nome di un elemento di livello radice per lo script di creazione dello spazio dei nomi del motore. Oggetto *elemento di livello radice* è un oggetto che può contenere proprietà e metodi e che possono inoltre contenere un'origine evento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszName`  
 [in] Il nome dell'elemento visualizzato dallo script. Il nome deve essere univoco e persistente.  
  
 `dwFlags`  
 [in] I flag associati all'elemento denominato. Può essere una combinazione dei valori seguenti:  
  
|Costante|Valore|Descrizione|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Indica che il nome dell'elemento è disponibile nello spazio dei nomi dello script. Ciò consente di accedere a proprietà, metodi ed eventi dell'elemento.<br /><br /> Per convenzione, le proprietà dell'elemento includono membri figlio dell'elemento. Pertanto, tutte le proprietà di oggetto figlio e i metodi (e i relativi membri figlio, in modo ricorsivo) sono accessibili.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Indica gli eventi dell'origine dell'elemento che lo script può avere i gestori di eventi di script.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Indica che l'elemento è una raccolta di proprietà globali e i metodi che sono associati lo script. Come i metodi e variabili globali vengono creati i relativi membri.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Indica che l'elemento deve essere salvato se viene salvato lo script del motore di creazione.|  
|SCRIPTITEM_CODEONLY|0x00000200|Indica che l'elemento denominato rappresenta un oggetto solo codice e non dispone di un membro da creare.|  
|SCRIPTITEM_NOCODE|0x00000400|Indica che l'elemento denominato è un nome viene aggiunto e dispone di nessun elemento da creare.|  
  
 `pdisp`  
 [in] Il `IDispatch` del `NamedItem` oggetto utilizzato per raccogliere i metodi, proprietà o l'origine evento.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)