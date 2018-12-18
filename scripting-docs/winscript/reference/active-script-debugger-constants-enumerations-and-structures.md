---
title: Costanti del Debugger dello Script ActiveX, enumerazioni e strutture | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger structures
- Active Script Debugger enumerations
- Active Script Debugger constants
ms.assetid: b80b9207-fb19-4ee2-85fb-41f8c26e7706
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6bd41fe91fdf030b957d800248343198f2617018
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-debugger-constants-enumerations-and-structures"></a>Costanti, enumerazioni e strutture del debugger di script ActiveX
Le seguenti costanti, enumerazioni e strutture sono utilizzate dalle interfacce di debug attivo.  
  
## <a name="constants-enumerations-and-structures"></a>Costanti, enumerazioni e strutture  
  
|Costanti|Descrizione|  
|---------------|-----------------|  
|[Costanti APPBREAKFLAGS](../../winscript/reference/appbreakflags-enumeration.md)|Indicano lo stato corrente del debug delle applicazioni e dei thread.|  
|[Costanti DEBUG_TEXT](../../winscript/reference/debug-text-constants.md)|Flag utilizzati durante l'opzione [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).|  
|[Costanti TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)|Descrivono gli attributi del documento.|  
  
|Enumerazioni|Descrizione|  
|------------------|-----------------|  
|[Costanti APPBREAKFLAGS](../../winscript/reference/appbreakflags-enumeration.md)|Indicano lo stato corrente del debug delle applicazioni e dei thread.|  
|[Enumerazione APPLICATION_NODE_EVENT_FILTER](../../winscript/reference/application-node-event-filter-enumeration.md)|Indicano i nodi da escludere con un filtro.|  
|[Enumerazione BREAKPOINT_STATE](../../winscript/reference/breakpoint-state-enumeration.md)|Indica lo stato di un punto di interruzione.|  
|[Enumerazione BREAKREASON](../../winscript/reference/breakreason-enumeration.md)|Indica la causa dell'interruzione.|  
|[Enumerazione BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)|Descrive come proseguire da un punto di interruzione.|  
|[Enumerazione DOCUMENTNAMETYPE](../../winscript/reference/documentnametype-enumeration.md)|Descrive quale tipo richiedere per un documento.|  
|[Enumerazione ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)|Descrive come proseguire a seguito di un errore di runtime.|  
|[Enumerazione JS_PROPERTY_ATTRIBUTES](../../winscript/reference/js-property-attributes-enumeration.md)|Indica gli attributi di una proprietà.|  
|[Enumerazione JS_PROPERTY_MEMBERS](../../winscript/reference/js-property-members-enumeration.md)|Flag per specificare il tipo di informazioni da restituire in una richiesta per i membri di un oggetto.|  
|[Enumerazione JsDebugReadMemoryFlags](../../winscript/reference/jsdebugreadmemoryflags-enumeration.md)|Flag per specificare il comportamento durante la lettura della memoria.|  
|[Enumerazione SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md)|Indica un set di opzioni o di funzionalità che si applicano al debugger collegato.|  
|[Enumerazione SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md)|Indica il tipo di eccezione generata.|  
|[Costanti SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)|Descrivono gli attributi di un singolo carattere di un testo di origine.|  
  
|Strutture|Descrizione|  
|----------------|-----------------|  
|[Struttura DebugStackFrameDescriptor](../../winscript/reference/debugstackframedescriptor-structure.md)|Enumera gli stack frame e unisce l'output da più enumeratori sullo stesso thread.|  
|[Struttura JS_NATIVE_FRAME](../../winscript/reference/js-native-frame-structure.md)|Rappresenta uno stack frame.|  
|[Struttura JsDebugPropertyInfo](../../winscript/reference/jsdebugpropertyinfo-structure.md)|Fornisce informazioni su una proprietà.|  
|[Struttura TEXT_DOCUMENT_ARRAY](../../winscript/reference/text-document-array-structure.md)|Fornisce un set di documenti.|