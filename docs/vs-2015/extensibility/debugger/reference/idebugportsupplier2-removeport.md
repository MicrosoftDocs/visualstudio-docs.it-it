---
title: IDebugPortSupplier2::RemovePort | Microsoft Docs
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
- IDebugPortSupplier2::RemovePort
helpviewer_keywords:
- IDebugPortSupplier2::RemovePort
ms.assetid: f5c1fbf2-9084-46f2-a682-7db963928df2
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cdca1b4f3a8d2ee97b3ce3a083b5af50a84bd0ee
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940671"
---
# <a name="idebugportsupplier2removeport"></a>IDebugPortSupplier2::RemovePort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Rimuove una porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT RemovePort(   
   IDebugPort2* pPort  
);  
```  
  
```csharp  
int RemovePort(   
   IDebugPort2 pPort  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pPort`  
 [in] Un' [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) oggetto che rappresenta la porta da rimuovere.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo rimuove la porta dall'elenco di porte attive interno del fornitore della porta.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

