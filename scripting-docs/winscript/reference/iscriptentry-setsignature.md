---
title: IScriptEntry::SetSignature | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.SetSignature
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::SetSignature
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9ff480f8e5c3192a7e2b355d39825cc3a084370
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
Imposta tipo di informazioni per un `IScriptEntry` oggetto funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pti`  
 [in] Le informazioni sul tipo.  
  
 `iMethod`  
 [in] L'indice del metodo nel `ITypeInfo` oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Impostare le informazioni sul tipo utilizzando `IScriptEntry::SetSignature` o [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Informazioni sul tipo può essere generati anche dalla voce basata sulla rappresentazione funzione interna.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)