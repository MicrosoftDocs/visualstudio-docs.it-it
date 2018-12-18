---
title: EndTrackingContext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 935df371b912d51ef6a5d88fdae4e9e11c449049
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="endtrackingcontext"></a>EndTrackingContext
Consente di terminare il contesto di verifica corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT WINAPI EndTrackingContext();  
```  
  
## <a name="return-value"></a>Valore restituito  
 **HRESULT** con il bit **SUCCEEDED** impostato se il contesto di verifica è terminato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** FileTracker.h  
  
## <a name="see-also"></a>Vedere anche  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)