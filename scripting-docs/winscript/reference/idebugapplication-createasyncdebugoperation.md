---
title: IDebugApplication::CreateAsyncDebugOperation | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.CreateAsyncDebugOperation
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::CreateAsyncDebugOperation
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8714f4401249d73cf09d241ebf4c2b2115911d6b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationcreateasyncdebugoperation"></a>IDebugApplication::CreateAsyncDebugOperation
Fornisce l'accesso asincrono a un'operazione di debug sincrono specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `psdo`  
 [in] Oggetto operazione sincrona di debug.  
  
 `ppado`  
 [out] L'oggetto debug asincrono dell'operazione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo consente di motori di linguaggio valutare le espressioni in modo asincrono, senza sincronizzazione in modo esplicito con il thread del debugger. Per ulteriori informazioni, vedere [interfaccia IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md) e [interfaccia IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interfaccia IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)   
 [Interfaccia IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)