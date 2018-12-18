---
title: IPerPropertyBrowsing2::GetPredefinedStrings | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IPerPropertyBrowsing2.GetPredefinedStrings
apilocation: scrobj.dll
helpviewer_keywords: IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e07d52eca9434acc7e54f3b35b111cf12af0a871
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Consente al chiamante di inserire una casella di riepilogo con una matrice di puntatori di stringa che rappresentano i valori possibili per questa proprietà conteggiata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dispid`  
 [in] ID dispatch della proprietà per cui il chiamante richiede l'elenco di stringhe.  
  
 `pCaStrings`  
 [out] Puntatore a una struttura di matrice allocata dal chiamante a conteggio che contiene il numero di elementi e l'indirizzo di una matrice allocata al metodo di puntatori di stringa. Se il metodo non riesce, non viene allocata memoria e il contenuto della struttura non è definito.  
  
 `pCaCookies`  
 [out] Puntatore alla struttura che contiene il numero di elementi e l'indirizzo di una matrice allocata al metodo di DWORD matrice allocata dal chiamante e conteggiato. Se il metodo non riesce, non viene allocata memoria e il contenuto della struttura non è definito.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un oggetto valido `HRESULT`, in genere `S_OK`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)