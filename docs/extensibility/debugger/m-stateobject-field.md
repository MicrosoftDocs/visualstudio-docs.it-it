---
title: Campo m_stateObject | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 79313460d380b2b505f6fa75f35351811ddaa470
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mstateobject-field"></a>m_stateObject campo
Oggetto che rappresenta i dati che verrà utilizzata l'azione.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
 Poiché è possibile accedere a questo membro interno di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Note  
 Si tratta di `state` parametro il <xref:System.Threading.Tasks.Task.%23ctor%2A> costruttore. È anche il campo sottostante per il <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe dell'attività](../../extensibility/debugger/task-class-internal-members.md)