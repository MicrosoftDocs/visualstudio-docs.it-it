---
title: StopTrackingAndCleanup | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ffbebd651087d9aa877d0e257947352a0d0275e
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154824"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
Arresta tutte le operazioni di verifica e libera tutta la memoria usata dalla sessione di verifica.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp 
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **HRESULT** con il bit **SUCCEEDED** impostato se la verifica è stata sospesa.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** *FileTracker.h*  
  
## <a name="see-also"></a>Vedere anche  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)