---
title: IDebugProgram2::CanDetach | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08387df82b20ef38380fe6302a5ca1f5d0bcbc9c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
Determina se un motore di debug (DE) è possibile disconnettersi dal programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CanDetach(  
   void  
);  
```  
  
```csharp  
int CanDetach();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se possibile scollegare restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `S_FALSE` se non è possibile scollegare la Germania dal programma.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)