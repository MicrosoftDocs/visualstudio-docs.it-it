---
title: IEnumDebugPorts2::GetCount | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::GetCount
helpviewer_keywords:
- IEnumDebugPorts2::GetCount
ms.assetid: d714455c-e4fc-48dc-a6d4-7e8b5d7c1bce
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46b000ffefcd8b2277b87cbda3b5c5fafba0a1c0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966617"
---
# <a name="ienumdebugports2getcount"></a>IEnumDebugPorts2::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Restituisce il numero di elementi nell'enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcelt`  
 [out] Restituisce il numero di elementi nell'enumerazione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo non fa parte dell'interfaccia di enumerazione COM facoltativa che specifica che solo le `Next`, `Clone`, `Skip`, e `Reset` devono essere implementati i metodi.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
