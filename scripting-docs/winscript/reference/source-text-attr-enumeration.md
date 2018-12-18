---
title: Enumerazione SOURCE_TEXT_ATTR | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f21bbfacc4918ff0e67731d5efd5521f371cbdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="sourcetextattr-enumeration"></a>Enumerazione SOURCE_TEXT_ATTR
Descrivono gli attributi di un singolo carattere di un testo di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Valore|Descrizione|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|Il carattere è parte di una parola chiave del linguaggio, ad esempio, la parola chiave VBScript `While`.|  
|SOURCETEXT_ATTR_COMMENT|0x0002|Il carattere è parte di un blocco di commento.|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|Il carattere non fa parte del testo di origine di linguaggio compilato. Ad esempio, il codice HTML che racchiudono un blocco di script.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|Il carattere è parte di un operatore di linguaggio. Ad esempio:, l'operatore aritmetico  **+** .|  
|SOURCETEXT_ATTR_NUMBER|0x0010|Il carattere è parte di una costante numerica di linguaggio.  Ad esempio, la costante 3,14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|Il carattere è parte di una costante di stringa di lingua. Ad esempio, la stringa "Hello World".|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|Il carattere indica l'inizio di un blocco di funzioni|  
  
## <a name="remarks"></a>Note  
 In genere, il `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes`, e `IActiveScriptDebug::GetScriptTextAttributes` metodi restituiscono un attributo di testo per ogni carattere, a meno che:  
  
-   È impostato il flag GETATTRTYPE_DEPSCAN, nel qual caso il metodo può restituire il flag SOURCETEXT_ATTR_IDENTIFIER e SOURCETEXT_ATTR_MEMBERLOOKUP,  
  
-   È impostato il flag GETATTRFLAG_THIS, nel qual caso il metodo può restituire il flag SOURCETEXT_ATTR_THIS,  
  
-   Il flag GETATTRFLAG_HUMANTEXT è impostato, nel qual caso il metodo può restituire il flag SOURCETEXT_ATTR_HUMANTEXT.  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)