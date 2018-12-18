---
title: IPerPropertyBrowsing2::GetDisplayString | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IPerPropertyBrowsing2.GetDisplayString
apilocation: scrobj.dll
helpviewer_keywords: IPerPropertyBrowsing2::GetDisplayString
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be6f665d1f63966b3828868f4fb8fbf1cae002e9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
Ottiene una stringa da visualizzare i tipi che non sono visualizzabili intrinsecamente testo restituito è un nome che descrive le proprietà e può essere visualizzata nell'interfaccia utente del chiamante.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dispid`  
 [in] ID dispatch della proprietà il cui nome visualizzato è richiesta.  
  
 `pBstr`  
 [out] Puntatore al `BSTR` contenente il nome visualizzato per la proprietà identificata da `dispID`.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un oggetto valido `HRESULT`, in genere `S_OK`.  
  
## <a name="remarks"></a>Note  
 La stringa restituita non è un valore valido della proprietà. È semplicemente una visualizzazione di stringa della proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)