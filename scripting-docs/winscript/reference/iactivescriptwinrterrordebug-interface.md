---
title: Interfaccia IActiveScriptWinRTErrorDebug | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug Interface
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 34fcc4f1dc3ebc21f9303ba49f1709f2d023a29a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptwinrterrordebug-interface"></a>Interfaccia IActiveScriptWinRTErrorDebug
Implementata dal motore JavaScript per fornire informazioni di errore estese Windows Runtime da un [enumerazione BREAKREASON](../../winscript/reference/breakreason-enumeration.md) evento. È possibile eseguire un QueryInterface per far sì che da un [IActiveScriptError](../../winscript/reference/iactivescripterror.md) oggetto.  
  
> [!IMPORTANT]
>  Questa interfaccia è implementata da PDM v11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 L'interfaccia `IActiveScriptWinRTErrorDebug` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Restituisce la funzionalità di SID per l'errore di Runtime di Windows, se disponibile.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Restituisce il Runtime di Windows limitato stringa di riferimento di errore, se disponibile.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Restituisce il Runtime di Windows limitato stringa di errore, se disponibile.|