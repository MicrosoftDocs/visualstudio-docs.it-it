---
title: IEnumDebugPorts2::Reset | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugPorts2::Reset
helpviewer_keywords:
- IEnumDebugPorts2::Reset
ms.assetid: 67da406c-eadb-421e-ae12-e26e9866f262
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 11fe76ff8a0856d8376fb025a1746ae7b4e8dbc7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748597"
---
# <a name="ienumdebugports2reset"></a>IEnumDebugPorts2::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Reimposta l'enumerazione sul primo elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Dopo che questo metodo viene chiamato, la chiamata successiva per la [successivo](../../../extensibility/debugger/reference/ienumdebugports2-next.md) metodo restituisce il primo elemento dell'enumerazione.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)

