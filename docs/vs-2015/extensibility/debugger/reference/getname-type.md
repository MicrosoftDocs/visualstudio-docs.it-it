---
title: GETNAME_TYPE | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f616b9715904d8ffae71b083baea6f7ced3bf5a2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528941"
---
# <a name="getnametype"></a>GETNAME_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [GETNAME_TYPE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/getname-type).  
  
Specifica il tipo di nome di file da recuperare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```csharp  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## <a name="members"></a>Membri  
 GN_NAME  
 Specifica un nome descrittivo del documento o del contesto.  
  
 GN_FILENAME  
 Specifica il percorso completo del documento o del contesto.  
  
 GN_BASENAME  
 Specifica un nome di file di base anziché un percorso completo del documento o del contesto.  
  
 GN_MONIKERNAME  
 Specifica un nome univoco del documento o del contesto sotto forma di un moniker.  
  
 GN_URL  
 Specifica il nome dell'URL del documento o del contesto.  
  
 GN_TITLE  
 Specifica un titolo del documento, se presente.  
  
 GN_STARTPAGEURL  
 Ottiene l'URL della pagina iniziale per i processi.  
  
## <a name="remarks"></a>Note  
 Questi valori vengono passati come parametri per il [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), e [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) metodi per specificare il tipo di nome da restituire.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)

