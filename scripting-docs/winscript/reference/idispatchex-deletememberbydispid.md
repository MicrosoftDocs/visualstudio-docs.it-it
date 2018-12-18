---
title: IDispatchEx::DeleteMemberByDispID | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.DeleteMemberByDispID
apilocation: scrobj.dll
helpviewer_keywords: DeleteMemberByDispID method
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 573eb60dc901e43706835c4d627b25bd54bbe751
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexdeletememberbydispid"></a>IDispatchEx::DeleteMemberByDispID
Elimina un membro da DISPID.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `id`  
 Identificatore del membro. Usa `GetDispID` o `GetNextDispID` per ottenere l'identificatore di invio.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|||  
|-|-|  
|`S_OK`|Operazione completata.|  
|`S_FALSE`|Membro esiste ma non può essere eliminato.|  
  
## <a name="remarks"></a>Note  
 Se il membro viene eliminato, deve rimanere valido per il DISPID `GetNextDispID`.  
  
 Se un membro con un nome specificato viene eliminato e successivamente viene ricreato a un membro con lo stesso nome, il DISPID deve essere lo stesso. (Se i nomi dei membri che differiscono solo per i casi sono "stesso" è dipendente dall'oggetto).  
  
## <a name="example"></a>Esempio  
  
```  
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)