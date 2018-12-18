---
title: FRAMEINFO_FLAGS | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ca63b23e9f87e807b3eec0e3ad35ea5414ac8dc6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
Specifica le informazioni da recuperare su un oggetto stack frame.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
typedef DWORD FRAMEINFO_FLAGS;  
```  
  
```csharp  
public enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
```  
  
## <a name="members"></a>Membri  
 FIF_FUNCNAME  
 Inizializzazione/Usa il `m_bstrFuncName` campo.  
  
 FIF_RETURNTYPE  
 Inizializzazione/Usa il `m_bstrReturnType` campo.  
  
 FIF_ARGS  
 Inizializzazione/Usa il `m_bstrArgs` campo.  
  
 FIF_LANGUAGE  
 Inizializzazione/Usa il `m_bstrLanguage` campo.  
  
 FIF_MODULE  
 Inizializzazione/Usa il `m_bstrModule` campo.  
  
 FIF_STACKRANGE  
 Inizializzazione/Usa il `m_addrMin` e `m_addrMax` campi (intervallo di stack).  
  
 FIF_FRAME  
 Inizializzazione/Usa il `m_pFrame` campo.  
  
 FIF_DEBUGINFO  
 Inizializzazione/Usa il `m_fHasDebugInfo` campo.  
  
 FIF_STALECODE  
 Inizializzazione/Usa il `m_fStaleCode` campo.  
  
 FIF_ANNOTATEDFRAME  
 Inizializzazione/Usa il `m_fAnnotatedFrame` campo.  
  
 FIF_DEBUG_MODULEP  
 Inizializzazione/Usa il `m_pModule` campo.  
  
 FIF_FUNCNAME_FORMAT  
 Formatta il nome della funzione. Il risultato viene restituito nel `m_bstrFunName` campo e non altri campi vengono compilati.  
  
 FIF_FUNCNAME_RETURNTYPE  
 Aggiunge il tipo restituito per il `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_ARGS  
 Aggiunge gli argomenti per il `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_LANGUAGE  
 Aggiunge la lingua per il `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_MODULE  
 Aggiunge il nome del modulo per il `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_LINES  
 Aggiunge il numero di righe per il `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_OFFSET  
 Aggiunge il `m_bstrFuncName` campo offset in byte dall'inizio della riga se `FIF_FUNCNAME_LINES` è specificato. Se `FIF_FUNCNAME_LINES` non viene specificato, o se i numeri di riga non sono disponibili, aggiunge l'offset in byte dall'inizio della funzione.  
  
 FIF_FUNCNAME_ARGS_TYPES  
 Aggiunge il tipo di ogni argomento di funzione per il `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_ARGS_NAMES  
 Aggiunge il nome di ogni argomento di funzione per il `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_ARGS_VALUES  
 Aggiunge il valore di ogni argomento di funzione per il `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_ARGS_ALL  
 Aggiunge il valore di tutti gli argomenti, un nome e un tipo di `m_bstrFuncName` campo.  
  
 FIF_ARGS_TYPES  
 I tipi di argomenti vengono recuperati e formattati.  
  
 FIF_ARGS_NAMES  
 I nomi degli argomenti vengono recuperati e formattati.  
  
 FIF_ARGS_VALUES  
 I valori degli argomenti vengono recuperati e formattati.  
  
 FIF_ARGS_ALL  
 Recuperare e formattare il tipo, nome e valore di tutti gli argomenti.  
  
 FIF_ARGS_NOFORMAT  
 Specifica che gli argomenti non sono formattato (ad esempio, non aggiungere apertura e chiusura di parentesi per racchiudere l'elenco di argomenti né aggiungere un separatore tra gli argomenti).  
  
 FIF_ARGS_NO_FUNC_EVAL  
 Specifica che la valutazione della funzione (proprietà) non deve essere utilizzata durante il recupero dei valori dell'argomento.  
  
 FIF_FILTER_NON_USER_CODE  
 Il motore di debug consiste nel filtrare i frame di codice non utente in modo che non sono inclusi.  
  
 FIF_ARGS_NO_TOSTRING  
 Non consentire `ToString()` funzione valutazione o la formattazione per la restituzione di argomenti della funzione.  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 Le informazioni sul frame deve essere ricevuti dal dominio dell'applicazione ospitato anziché il processo di hosting.  
  
## <a name="remarks"></a>Note  
 Questi flag vengono passati al [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) e [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) metodi per indicare quali campi devono essere inizializzati nel [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) o strutture.  
  
 Questi flag sono utilizzati anche per indicare quali campi del [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struttura sono validi e utilizzate quando viene restituita la struttura. Questi valori possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)