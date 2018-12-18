---
title: Campo m_children | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e71bc592e77daac877b571b14acd2d62a8657b9f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mchildren-field"></a>m_children campo
L'elenco di attività figlio che sono registrati con questa attività.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
 Poiché è possibile accedere a questo membro interno di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Note  
 Durante l'esecuzione dell'attività, solo il thread che esegue l'attività deve accedere a questa matrice.  
  
 Se l'attività è stata completata, altri thread può accedere in questo campo, purché non aggiunge nulla a esso o rimuovere qualsiasi elemento da esso.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)