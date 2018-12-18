---
title: Struttura AsyncVoidMethodBuilder - membri interni | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ff9a3f380703db9906eea1b076e4e6f088d1a8c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Struttura AsyncVoidMethodBuilder - membri interni
In questo argomento vengono descritti i membri interni del <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> classe. Per informazioni generali su questa classe, vedere il <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> argomento di riferimento.  
  
 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
 Poiché è possibile accedere a questi membri interni da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Membri interni  
  
|nome|Descrizione|  
|----------|-----------------|  
|[Proprietà ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Ottiene un oggetto che può essere utilizzato per identificare in modo univoco questo generatore al debugger.|  
|[campo m_objectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Rappresenta l'oggetto con inizializzazione differita utilizzato dal debugger per identificare in modo univoco questo generatore.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [Elementi interni delle estensioni parallele per .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)