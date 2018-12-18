---
title: IDiaStackWalkHelper::put_registerValue | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eec04b3ab02f10d6eb9d745c21d2d0872df0ab8b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackwalkhelperputregistervalue"></a>IDiaStackWalkHelper::put_registerValue
Imposta il valore di un registro.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `index`  
 [in] Un valore di [CV_HREG_e (enumerazione)](../../debugger/debug-interface-access/cv-hreg-e.md) enumerazione che specifica il registro in cui scrivere.  
  
 `NewVal`  
 [in] Il nuovo valore di registro.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Nonostante le dimensioni del valore, un'implementazione deve archiviare solo ciò che la registrazione in genere contiene. Ad esempio, un registro a 8 bit conterrebbe solo il più basso 8 bit del valore specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV_HREG_e (enumerazione)](../../debugger/debug-interface-access/cv-hreg-e.md)