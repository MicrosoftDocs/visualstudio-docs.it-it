---
title: StartTrackingContextWithRoot | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- StartTrackingContextWithRoot
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: da93697f273257d166bf377e9c84b03d59d06f78
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot
Avvia un contesto di verifica usando un file di risposta che specifica un marcatore radice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp 
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### <a name="parameters"></a>Parametri  
 [in] `intermediateDirectory`  
 Directory in cui archiviare il log di rilevamento.  
  
 [in] `taskName`  
 Identifica il contesto di verifica. Questo nome viene usato per creare il nome del file di log.  
  
 [in] `rootMarkerResponseFile`  
 Percorso di un file di risposta che contiene un marcatore radice. Il nome radice viene usato per raggruppare tutte le verifiche relative a un contesto.  
  
## <a name="return-value"></a>Valore restituito  
 **HRESULT** con il bit **SUCCEEDED** impostato se il contesto di rilevamento è stato creato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** FileTracker.h  
  
## <a name="see-also"></a>Vedere anche  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)