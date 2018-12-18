---
title: IProvideExpressionContexts::EnumExpressionContexts | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IProvideExpressionContexts.EnumExpressionContexts
apilocation: jscript.dll
helpviewer_keywords: IProvideExpressionContexts::EnumExpressionContexts
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c47619fface892e7e0d80141d7d4be53398a356e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Restituisce un enumeratore dei contesti di espressione noto da questo componente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppedec`  
 [out] Un enumeratore di contesti di espressione noto da questo componente.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Il gestore di debug del processo utilizza questo metodo per trovare tutti i contesti di espressione globale associati a un determinato thread.  
  
> [!NOTE]
>  Questo metodo viene chiamato dall'interno del thread di interesse. È responsabilità dell'implementatore per identificare il thread corrente e restituisce un enumeratore appropriato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IProvideExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-interface.md)