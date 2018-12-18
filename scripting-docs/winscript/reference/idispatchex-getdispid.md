---
title: IDispatchEx::GetDispID | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93595cd2d0f88244866ab7363ecd68c6d8073b48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Associa un nome singolo membro per il DISPID corrispondente, che può quindi essere usato nelle chiamate successive a `IDispatchEx::InvokeEx`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
 HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `bstrName`  
 Passato nel nome devono essere mappati.  
  
 `grfdex`  
 Determina le opzioni per ottenere l'identificatore del membro. Può trattarsi di una combinazione dei valori seguenti:  
  
|Valore|Significato|  
|-----------|-------------|  
|fdexNameCaseSensitive|Richieste di effettuare la ricerca del nome in minuscolo. Può essere ignorata dall'oggetto che non supportano la ricerca tra maiuscole e minuscole.|  
|fdexNameEnsure|Richiede che il membro creato se non esiste già. Il nuovo membro deve essere creato con il valore `VT_EMPTY`.|  
|fdexNameImplicit|Indica che il chiamante ricerca oggetti di un membro di un determinato nome quando l'oggetto di base non è specificato in modo esplicito.|  
|fdexNameCaseInsensitive|Richieste di effettuare la ricerca del nome in minuscole. Può essere ignorata dall'oggetto che non supportano la ricerca tra maiuscole e minuscole.|  
  
 `pid`  
 Puntatore alla posizione allocata dal chiamante per ricevere il risultato DISPID. Se si verifica un errore, `pid` contiene DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|||  
|-|-|  
|`S_OK`|Operazione completata.|  
|`E_OUTOFMEMORY`|Memoria insufficiente.|  
|`DISP_E_UNKNOWNNAME`|Il nome non era nota.|  
  
## <a name="remarks"></a>Note  
 `GetDispID`può essere utilizzato al posto di `GetIDsOfNames` per ottenere il DISPID per un membro specificato.  
  
 Poiché `IDispatchEx` consente l'aggiunta e l'eliminazione di membri, il set dei DispId non rimane costante per la durata di un oggetto.  
  
 Inutilizzata `riid` parametro `IDispatch::GetIDsOfNames` è stato rimosso.  
  
## <a name="example"></a>Esempio  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)