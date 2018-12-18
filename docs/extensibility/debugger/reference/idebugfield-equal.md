---
title: IDebugField::Equal | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::Equal
helpviewer_keywords: IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f6cba643f6d1b0f5f1d1c9fff23c8636bd12caca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Questo metodo confronta questo campo con il campo specificato per verificarne l'uguaglianza.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pField`  
 [in] Il campo da confrontare con questo.  
  
## <a name="return-value"></a>Valore restituito  
 Se i campi sono uguali, restituisce `S_OK`. Se i campi sono diversi, restituisce `S_FALSE.` in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)