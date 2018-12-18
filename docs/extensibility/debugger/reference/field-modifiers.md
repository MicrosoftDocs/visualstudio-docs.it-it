---
title: FIELD_MODIFIERS | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0040795564aa1d1d599a55928b888ec7cfcfd97e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="fieldmodifiers"></a>FIELD_MODIFIERS
Specifica i modificatori per un tipo di campo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_FIELD_MODIFIERS {   
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
typedef DWORD FIELD_MODIFIERS;  
```  
  
```csharp  
public enum enum_FIELD_MODIFIERS {  
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
```  
  
## <a name="members"></a>Membri  
 FIELD_MOD_ACCESS_TYPE  
 Indica che il campo non è possibile accedere.  
  
 FIELD_MOD_ACCESS_PUBLIC  
 Indica che il campo dispone di accesso pubblico.  
  
 FIELD_MOD_ACCESS_PROTECTED  
 Indica che il campo con l'accesso protetto.  
  
 FIELD_MOD_ACCESS_PRIVATE  
 Indica che il campo con accesso privato.  
  
 FIELD_MOD_NOMODIFIERS  
 Indica che il campo non ha modificatori.  
  
 FIELD_MOD_STATIC  
 Indica che il campo è statico.  
  
 FIELD_MOD_CONSTANT  
 Indica che il campo è costante.  
  
 FIELD_MOD_TRANSIENT  
 Indica che il campo è temporaneo.  
  
 FIELD_MOD_VOLATILE  
 Indica che il campo è volatile.  
  
 FIELD_MOD_ABSTRACT  
 Indica che il campo è astratto.  
  
 FIELD_MOD_NATIVE  
 Indica che il campo è nativo.  
  
 FIELD_MOD_SYNCHRONIZED  
 Indica che il campo è sincronizzato.  
  
 FIELD_MOD_VIRTUAL  
 Indica che il campo è virtuale.  
  
 FIELD_MOD_INTERFACE  
 Indica che il campo è un'interfaccia.  
  
 FIELD_MOD_FINAL  
 Indica che il campo è finale.  
  
 FIELD_MOD_SENTINEL  
 Indica che il campo è sentinel.  
  
 FIELD_MOD_INNERCLASS  
 Indica che il campo è una classe interna.  
  
 FIELD_TYPE_OPTIONAL  
 Indica che il campo è facoltativo.  
  
 FIELD_MOD_BYREF  
 Indica che il campo è un argomento di riferimento. Si tratta in particolare per gli argomenti del metodo.  
  
 FIELD_MOD_HIDDEN  
 Indica che il campo deve essere nascosto o visualizzato in un altro contesto. ad esempio, [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] variabili locali statiche.  
  
 FIELD_MOD_MARSHALASOBJECT  
 Indica che il campo rappresenta un oggetto con un `IUnknown` interfaccia.  
  
 FIELD_MOD_SPECIAL_NAME  
 Indica che il campo ha un nome speciale, ad esempio, `.ctor` per un costruttore ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] solo).  
  
 FIELD_MOD_HIDEBYSIG  
 Indica che il campo contiene il `Overloads` (parola chiave) applicata ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] solo).  
  
 FIELD_MOD_WRITEONLY  
 Indica che il campo è di sola scrittura. Questo valore non è incluso `FIELD_MOD_ALL`, come l'uso solo di questi campi di sola scrittura per la valutazione della funzione. Un utente deve richiedere esplicitamente `FIELD_MOD_WRITEONLY` campi.  
  
 FIELD_MOD_ACCESS_MASK  
 Indica una maschera di accesso al campo.  
  
 FIELD_MOD_MASK  
 Indica una maschera per i modificatori di campo.  
  
## <a name="remarks"></a>Note  
 Utilizzato per il `dwModifiers` appartenente il [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struttura.  
  
 Questi valori vengono passati anche per il [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) metodo per filtrare i campi specifici.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)