---
title: IMachineDebugManagerEvents::onAddApplication | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerEvents.onAddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerEvents::onAddApplication
ms.assetid: 00a54b91-36d5-430d-b654-5e2abe5300cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 887ce7f723713c335d72a6353c20765c7b695031
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagereventsonaddapplication"></a>IMachineDebugManagerEvents::onAddApplication
Gestisce l'evento quando un'applicazione viene aggiunto all'esecuzione elenco di applicazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT onAddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pda`  
 [in] Applicazione che è stata aggiunta all'esecuzione elenco di applicazioni.  
  
 `dwAppCookie`  
 [in] Il cookie specificato quando l'applicazione è stato aggiunto all'elenco di applicazioni.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo indica che un'applicazione è stata aggiunta all'esecuzione elenco di applicazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IMachineDebugManagerEvents](../../winscript/reference/imachinedebugmanagerevents-interface.md)   
 [IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)