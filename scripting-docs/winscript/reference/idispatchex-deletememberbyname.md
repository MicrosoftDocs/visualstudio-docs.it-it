---
title: IDispatchEx::DeleteMemberByName | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByName
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb9a9dfd979954c42101fde41819d7e12db59e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Elimina un membro in base al nome.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Parametri  
 `bstrName`  
 Nome del membro da eliminare.  
  
 `grfdex`  
 Determina se il nome del membro viene fatta distinzione tra maiuscole e minuscole. Può trattarsi di uno dei valori seguenti:  
  
|Valore|Significato|  
|-----------|-------------|  
|fdexNameCaseSensitive|Richieste di effettuare la ricerca del nome in minuscolo. Può essere ignorato dall'oggetto che non supportano la ricerca tra maiuscole e minuscole.|  
|fdexNameCaseInsensitive|Richieste di effettuare la ricerca del nome in minuscole. Può essere ignorato dall'oggetto che non supportano la ricerca tra maiuscole e minuscole.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|||  
|-|-|  
|`S_OK`|Operazione completata.|  
|`S_FALSE`|Membro esiste ma non può essere eliminato.|  
  
## <a name="remarks"></a>Note  
 Se il membro viene eliminato, deve rimanere valido per il DISPID `GetNextDispID`.  
  
 Se un membro con un nome specificato viene eliminato e successivamente viene ricreato a un membro con lo stesso nome, il DISPID deve essere lo stesso. (Se i membri che differiscono solo per i casi sono "stesso" è dipendente dall'oggetto).  
  
## <a name="example"></a>Esempio  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)