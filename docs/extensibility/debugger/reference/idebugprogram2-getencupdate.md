---
title: IDebugProgram2::GetENCUpdate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09caf056b01efa9c09e07362d2c195599f53be51
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962891"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Questo metodo ottiene l'aggiornamento di modifica e Continuazione per il programma. Un motore di debug personalizzato restituisce sempre `E_NOTIMPL`.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetENCUpdate(   
   IUnknown** ppUpdate  
);  
```  
  
```csharp  
int GetENCUpdate(  
   out object ppUpdate  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppUpdate`  
 [out] Restituisce un'interfaccia interna che può essere utilizzata per aggiornare il programma.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
> [!NOTE]
>  Un motore di debug personalizzato deve sempre restituire `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)