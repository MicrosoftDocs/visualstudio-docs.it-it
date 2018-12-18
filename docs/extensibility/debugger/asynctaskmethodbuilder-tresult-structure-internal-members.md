---
title: AsyncTaskMethodBuilder&lt;TResult&gt; struttura - membri interni | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4b5c9c3b0ff653384ff7a14487899d8205975cd5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult&gt; struttura - membri interni
In questo argomento vengono descritti i membri interni del <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> classe. Per informazioni generali su questa classe, vedere il <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> argomento di riferimento.  
  
 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
 Poiché è possibile accedere a questi membri interni da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Membri interni  
  
|nome|Descrizione|  
|----------|-----------------|  
|[Proprietà ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Ottiene un oggetto che può essere utilizzato per identificare in modo univoco questo generatore al debugger.|  
|[campo m_task](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Rappresenta l'inizializzazione differita compilato attività.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [Elementi interni delle estensioni parallele per .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)