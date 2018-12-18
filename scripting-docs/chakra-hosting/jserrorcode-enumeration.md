---
title: Enumerazione JsErrorCode | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsErrorCode
helpviewer_keywords: JsErrorCode enumeration
ms.assetid: 4902f3f3-47a5-4e74-9c29-f96eeecbcda9
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b09babd38505c5619f414d2e349cd52b3596ceac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jserrorcode-enumeration"></a>Enumerazione JsErrorCode
Codice di errore restituito da una API di hosting Chakra.  
  
## <a name="syntax"></a>Sintassi  
  
```  
enum JsErrorCode : unsigned int;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="values"></a>Valori  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`JsErrorAlreadyDebuggingContext`|Il contesto non può essere inserito in uno stato di debug perché vi è già.|  
|`JsErrorAlreadyProfilingContext`|Il contesto non può avviare la profilatura perché è già in atto.|  
|`JsErrorArgumentNotObject`|Un'API di hosting che agisce sui valori oggetto è stata chiamata con un valore non oggetto.|  
|`JsErrorBadSerializedScript`|È stato usato uno script serializzato in modo non corretto oppure la serializzazione dello script è stata eseguita da una versione diversa del motore Chakra.|  
|`JsErrorCannotDisableExecution`|Il runtime non supporta l'interruzione affidabile di script.|  
|`JsErrorCannotSerializeDebugScript`|Gli script non possono essere serializzati in contesti di debug.|  
|`JsErrorCategoryEngine`|Categoria di errori che mette in relazione con errori che si verificano all'interno del motore stesso.|  
|`JsErrorCategoryFatal`|Categoria di errori irreversibili che indicano un errore del motore.|  
|`JsErrorCategoryScript`|Categoria di errori che mette in relazione con errori in uno script.|  
|`JsErrorCategoryUsage`|Categoria di errori che mette in relazione con l'utilizzo non corretto dell'API stessa.|  
|`JsErrorFatal`|Si è verificato un errore irreversibile nel motore.|  
|`JsErrorHeapEnumInProgress`|Un'enumerazione dell'heap è attualmente in corso nel contesto dello script.|  
|`JsErrorIdleNotEnabled`|Notifica di inattività data quando l'host non ha abilitato l'elaborazione in periodi di inattività.|  
|`JsErrorInDisabledState`|Il runtime è in uno stato disabilitato.|  
|`JsErrorInExceptionState`|Il motore è in uno stato di eccezione e nessuna API può essere chiamata finché non viene cancellata l'eccezione.|  
|`JsErrorInObjectBeforeCollectCallback`|L'operazione non è supportata in un oggetto prima del callback della raccolta.<br /><br /> Questo valore di enumerazione è supportato solo in modalità Bordo|  
|`JsErrorInProfileCallback`|Un contesto di script è al centro di un callback di profilo.|  
|`JsErrorInThreadServiceCallback`|È in corso un callback di servizio del thread.|  
|`JsErrorInvalidArgument`|Un argomento per l'API di hosting non è valido.|  
|`JsErrorNoCurrentContext`|Per l'API di hosting è necessario che un contesto sia corrente, ma non ve ne sono.|  
|`JsErrorNotImplemented`|Un'API di hosting non è ancora stata implementata.|  
|`JsErrorNullArgument`|Un argomento per l'API di hosting è Null in un contesto in cui questo valore non è consentito.|  
|`JsErrorObjectNotInspectable`|Non è possibile annullare il wrapping dell'oggetto al puntatore `IInspectable` .<br /><br /> Questo valore di enumerazione è supportato solo in modalità Bordo|  
|`JsErrorOutOfMemory`|Memoria insufficiente del motore Chakra.|  
|`JsErrorPropertyNotSymbol`|Un'API di hosting che opera su ID di proprietà simbolo è stata chiamata con un ID di proprietà non simbolo. Il codice di errore viene restituito da `JsGetSymbolFromPropertyId` se la funzione viene chiamata con ID di proprietà non simbolo.<br /><br /> Questo valore di enumerazione è supportato solo in modalità Bordo|  
|`JsErrorPropertyNotString`|Un'API di hosting che opera su ID di proprietà stringa è stata chiamata con un ID di proprietà non stringa. Il codice di errore viene restituito dalla proprietà `JsGetPropertyNamefromId` esistente se la funzione viene chiamata con ID di proprietà non stringa.<br /><br /> Questo valore di enumerazione è supportato solo in modalità Bordo|  
|`JsErrorRuntimeInUse`|Un runtime che è ancora in uso non può essere eliminato.|  
|`JsErrorScriptCompile`|Compilazione non riuscita da parte di JavaScript.|  
|`JsErrorScriptEvalDisabled`|Uno script è stato interrotto perché ha tentato di usare `eval` o `function` ed eval è disabilitato.|  
|`JsErrorScriptException`|Un'eccezione JavaScript si è verificata durante l'esecuzione di uno script.|  
|`JsErrorScriptTerminated`|Uno script è stato interrotto a causa di una richiesta di sospensione del runtime.|  
|`JsErrorWrongRuntime`|Un'API di hosting è stata chiamata con l'oggetto creato in un runtime JavaScript diverso.|  
|`JsErrorWrongThread`|Un'API di hosting è stata chiamata sul thread errato.|  
|`JsNoError`|Codice di errore riuscito.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)