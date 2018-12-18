---
title: IDebugProperty::GetExtendedInfo | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugProperty.GetExtendedInfo
apilocation: scrobj.dll
helpviewer_keywords: IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc549ecc4cfa3b3cbbb754585c751b16df2fd8a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Ottiene le informazioni per la proprietà estese.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cInfos`  
 [in] Numero di oggetti informazioni estese.  
  
 `rgguidExtendedInfo`  
 [in] Matrice di `GUID`s viene passato in modo che più elementi di informazioni estese possono essere recuperati allo stesso tempo.  
  
 `pExtendedInfo`  
 [out] Restituisce una matrice di `VARIANT`che può essere utilizzato per recuperare le informazioni sulle proprietà estese.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un oggetto valido `HRESULT`, in genere `S_OK`.  
  
## <a name="remarks"></a>Note  
 Questa interfaccia ottiene estese informazioni per questo oggetto. L'API esiste solo allo scopo di recupero di informazioni che non si prestano a recuperati dall'uso di `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)