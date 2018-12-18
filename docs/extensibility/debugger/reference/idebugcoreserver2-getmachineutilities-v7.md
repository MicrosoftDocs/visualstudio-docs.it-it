---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 96f374d83af705d8e9376d8767c822af82ed4d4a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Questo metodo ottiene le utilità di computer per un server.  
  
> [!NOTE]
>  Questo metodo è obsoleto: non utilizzare ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] restituisce sempre `E_NOTIMPL` se questo metodo viene chiamato). È stato conservato per motivi cronologici.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppUtil`  
 [out] Restituisce un `IDebugMDMUtil2_V7` interfaccia che rappresenta le informazioni di utilità macchina.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce sempre `E_NOTIMPL`, che indica che il metodo non implementato.  
  
## <a name="remarks"></a>Note  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Restituisce sempre `E_NOTIMPL` se questo metodo viene chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)