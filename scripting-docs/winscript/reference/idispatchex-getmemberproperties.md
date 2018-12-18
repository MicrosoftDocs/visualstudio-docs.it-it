---
title: IDispatchEx::GetMemberProperties | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDispatchEx.GetMemberProperties
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d216bb7b21c8895337b9925007637c00d0deb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Recupera le proprietà del membro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `id`  
 Identifica il membro. Usa `GetDispID` o `GetNextDispID` per ottenere l'identificatore di invio.  
  
 `grfdexFetch`  
 Determina le proprietà da recuperare. Può trattarsi di una combinazione dei valori elencati in `pgrfdex` e/o una combinazione dei valori seguenti:  
  
|Valore|Significato|  
|-----------|-------------|  
|grfdexPropCanAll|Combina fdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, fdexPropCanConstruct e fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Combina fdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, fdexPropCannotConstruct e fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|Combina fdexPropNoSideEffects e fdexPropDynamicType.|  
|grfdexPropAll|Combina grfdexPropCanAll, grfdexPropCannotAll e grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Indirizzo di un `DWORD` che riceve le proprietà richieste. Può trattarsi di una combinazione dei valori seguenti:  
  
|Valore|Significato|  
|-----------|-------------|  
|fdexPropCanGet|Il membro può essere ottenuto utilizzando DISPATCH_PROPERTYGET.|  
|fdexPropCannotGet|Il membro non può essere ottenuto utilizzando DISPATCH_PROPERTYGET.|  
|fdexPropCanPut|Il membro può essere impostato utilizzando DISPATCH_PROPERTYPUT.|  
|fdexPropCannotPut|Il membro non può essere impostato utilizzando DISPATCH_PROPERTYPUT.|  
|fdexPropCanPutRef|Il membro può essere impostato utilizzando DISPATCH_PROPERTYPUTREF.|  
|fdexPropCannotPutRef|Il membro non può essere impostato utilizzando DISPATCH_PROPERTYPUTREF.|  
|fdexPropNoSideEffects|Il membro non dispone di tutti gli effetti collaterali. Ad esempio, un debugger potrebbe tranquillamente get/set/chiamata di questo membro senza modificare lo stato dello script in fase di debug.|  
|fdexPropDynamicType|Il membro è dinamico e può variare nel corso della durata dell'oggetto.|  
|fdexPropCanCall|Il membro può essere chiamato come un metodo utilizzando DISPATCH_METHOD.|  
|fdexPropCannotCall|Il membro non può essere chiamato come un metodo utilizzando DISPATCH_METHOD.|  
|fdexPropCanConstruct|Il membro può essere chiamato come costruttore utilizzando DISPATCH_CONSTRUCT.|  
|fdexPropCannotConstruct|Il membro non può essere chiamato come costruttore con DISPATCH_CONSTRUCT.|  
|fdexPropCanSourceEvents|Il membro può generare eventi.|  
|fdexPropCannotSourceEvents|Il membro non può generare eventi.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|||  
|-|-|  
|`S_OK`|Operazione completata.|  
|`DISP_E_UNKNOWNNAME`|Il nome non era nota.|  
  
## <a name="example"></a>Esempio  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)