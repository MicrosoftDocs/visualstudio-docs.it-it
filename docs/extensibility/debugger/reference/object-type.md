---
title: OBJECT_TYPE | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OBJECT_TYPE
helpviewer_keywords: OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 441cd9569ef38d210c7f1611b718973b6cc0dc4a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="objecttype"></a>OBJECT_TYPE
Specifica il tipo di un oggetto dall'analizzatore di espressioni.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
typedef DWORD OBJECT_TYPE;  
```  
  
```csharp  
public enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
```  
  
## <a name="members"></a>Membri  
 OBJECT_TYPE_BOOLEAN  
 Indica che l'oggetto è un valore booleano.  
  
 OBJECT_TYPE_CHAR  
 Indica che l'oggetto è un carattere.  
  
 OBJECT_TYPE_I1  
 Indica che l'oggetto è un intero con segno a 1 byte.  
  
 OBJECT_TYPE_U1  
 Indica che l'oggetto è un intero senza segno a 1 byte.  
  
 OBJECT_TYPE_I2  
 Indica che l'oggetto è un intero con segno a 2 byte.  
  
 OBJECT_TYPE_U2  
 Indica che l'oggetto è un intero senza segno a 2 byte.  
  
 OBJECT_TYPE_I4  
 Indica che l'oggetto è un intero con segno a 4 byte.  
  
 OBJECT_TYPE_U4  
 Indica che l'oggetto è un intero senza segno a 4 byte.  
  
 OBJECT_TYPE_I8  
 Indica che l'oggetto è un intero con segno a 8 byte.  
  
 OBJECT_TYPE_U8  
 Indica che l'oggetto è un intero senza segno a 8 byte.  
  
 OBJECT_TYPE_R4  
 Indica che l'oggetto è un numero a virgola mobile a 4 byte.  
  
 OBJECT_TYPE_R8  
 Indica che l'oggetto è un numero a virgola mobile a 8 byte.  
  
 OBJECT_TYPE_OBJECT  
 Indica che l'oggetto è un oggetto.  
  
 OBJECT_TYPE_NULL  
 Indica che l'oggetto è NULL.  
  
 OBJECT_TYPE_CLASS  
 Indica che l'oggetto è una classe.  
  
## <a name="remarks"></a>Note  
 Passata come argomento per il [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) e [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) metodi.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)