---
title: IDebugCoreServer2::GetMachineInfo | Microsoft Docs
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
- IDebugCoreServer2::GetInfo
helpviewer_keywords:
- IDebugCoreServer2::GetInfo
ms.assetid: 8fa1a1d3-9fcb-4fb3-bf4e-e7172ac08d77
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c21b908ba1397ec95ba68b38a04fa2df0f5e9aec
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222527"
---
# <a name="idebugcoreserver2getmachineinfo"></a>IDebugCoreServer2::GetMachineInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera una descrizione del computer che in cui è in esecuzione server core.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetInfo(   
   MACHINE_INFO_FIELDS Fields,  
   MACHINE_INFO*       pMachineInfo  
);  
```  
  
```csharp  
int GetInfo(   
   enum_ MACHINE_INFO_FIELDS  Fields,  
   MACHINE_INFO[]             pMachineInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `Fields`  
 [in] Una combinazione di flag dal [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) enumerazione che specificano quali campi della `pMachineInfo` sono da compilare.  
  
 `pMachineInfo`  
 [in, out] Oggetto [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) struttura compilata con una descrizione della macchina.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)

