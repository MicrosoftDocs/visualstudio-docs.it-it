---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords: IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bf5881dabea216d7226e731c169dd97d1460c7fb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]Restituisce sempre `E_NOTIMPL` se questo metodo viene chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)