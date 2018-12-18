---
title: IDebugApplication110::CallableWaitForHandles | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b259f5296f8e0b32def793a81e4c2e1069643306
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Attende che uno degli handle specificati per ricevere il segnale consentendo chiamata tra thread a questo thread. Questo metodo deve essere chiamato dal thread del debugger.  
  
> [!IMPORTANT]
>  [Interfaccia IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) è implementata da PDM v 11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Parametri  
 `handleCount`  
 Il numero di handle di attesa.  
  
 `pHandles`  
 Il set di handle di attesa.  
  
 `pIndex`  
 Quando il valore HRESULT è S_OK, l'indice in `pHandles` per l'handle è stato segnalato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)