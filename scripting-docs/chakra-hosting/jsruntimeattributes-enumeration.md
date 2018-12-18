---
title: Enumerazione JsRuntimeAttributes | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsRuntimeAttributes
helpviewer_keywords:
- JsRuntimeAttributes enumeration
ms.assetid: f76d82e9-a695-4d6a-96c1-b3a4d27fed68
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a7917ad5468b8d2924526f953ae444c5d8381eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsruntimeattributes-enumeration"></a>Enumerazione JsRuntimeAttributes
Attributi di un runtime.  
  
## <a name="syntax"></a>Sintassi  
  
```  
enum JsRuntimeAttributes;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="values"></a>Valori  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`JsRuntimeAttributeAllowScriptInterrupt`|Il runtime deve supportare l'interruzione affidabile dello script. In questo modo viene aumentato il numero di posizioni in cui verrà verificata una richiesta di interruzione di script da parte del runtime; questa operazione comporta un lieve calo in termini di prestazioni.|  
|`JsRuntimeAttributeDisableBackgroundWork`|Non verrà eseguita alcuna operazione (quali Garbage Collection) sui thread in background da parte del runtime.|  
|`JsRuntimeAttributeDisableEval`|L'utilizzo del costruttore `eval` o `function` genererà un'eccezione.|  
|`JsRuntimeAttributeDisableNativeCodeGeneration`|Il runtime non genererà codice nativo.|  
|`JsRuntimeAttributeEnableExperimentalFeatures`|Il runtime abiliterà tutte le funzionalità sperimentali.|  
|`JsRuntimeAttributeEnableIdleProcessing`|L'host chiamerà `JsIdle`, in modo da consentire l'elaborazione in periodi di inattività. In caso contrario, il runtime gestirà in modo leggermente più deciso la memoria.|  
|`JsRuntimeAttributeDispatchSetExceptionsToDebugger`|In seguito alla chiamata a `JsSetException` l'eccezione verrà inviata anche al debugger di script (se presente), che potrà interrompersi in corrispondenza dell'eccezione.|  
|`JsRuntimeAttributeNone`|Nessun attributo speciale.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)