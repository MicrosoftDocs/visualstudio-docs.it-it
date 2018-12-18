---
title: Enumerazione SCRIPTSTATE | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: SCRIPTSTATE
apilocation: scrobj.dll
helpviewer_keywords: SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35e062a9c2f3076144063ffb77895c8a03ecc4ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="scriptstate-enumeration"></a>Enumerazione SCRIPTSTATE
Specifica lo stato di un motore di scripting. Questa enumerazione viene utilizzata per la [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) , e [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metodi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## <a name="enumeration-values"></a>Valori di enumerazione  
  
|||  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|Script è stato appena creato, ma non è ancora stato inizializzato con un `IPersist*` interfaccia e [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Script è stato inizializzato, ma non è in esecuzione (la connessione ad altri oggetti o sink di eventi) o esecuzione di codice. È possibile eseguire query codice per l'esecuzione chiamando il [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md) metodo.|  
|SCRIPTSTATE_STARTED|Script può eseguire codice, ma non è ancora l'elaborazione di eventi di oggetti aggiunti dal [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metodo.|  
|SCRIPTSTATE_CONNECTED|Script è stato caricato e connesso per sink di eventi.|  
|SCRIPTSTATE_DISCONNECTED|Script viene caricato e lo stato di una fase di esecuzione, ma è stato disconnesso temporaneamente dal sink di eventi.|  
|SCRIPTSTATE_CLOSED|Script è stato chiuso. Il motore di scripting non funziona più e restituisce gli errori per la maggior parte dei metodi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e codici di errore dello script ActiveX](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)