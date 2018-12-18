---
title: IScriptEntry::GetSignature | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.GetSignature
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 062f069bb6a19c24f26a6a0bc6a9f4de2292d88f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Restituisce informazioni sul tipo per un `IScriptEntry` oggetto funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppti`  
 [out] Digitare le informazioni associate a questo `IScriptEntry` oggetto funzione.  
  
 `piMethod`  
 [out] Indice di metodo nel `ITypeInfo` oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Impostare le informazioni sul tipo utilizzando [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) o [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Informazioni sul tipo può essere generati anche dalla voce basata sulla rappresentazione funzione interna.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)