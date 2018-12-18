---
title: Contesto del documento | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f97df9bc3c0a40a44379ba37f1b36d79cffb74e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="document-context"></a>Contesto di documento
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, un **contesto del documento**:  
  
-   Rappresenta una posizione in un file di origine. Per le lingue in cui il file di origine non può essere presente, un contesto di documento identifica una posizione in un documento in genere generato dall'ambiente di runtime. Ad esempio, un motore di script potrebbe generare un documento da script. Per ulteriori informazioni, vedere [posizione documento](../../extensibility/debugger/document-position.md).  
  
-   Descrive una posizione in un documento di origine che corrisponde a un contesto di codice. Il gestore di simboli esegue il mapping di un contesto di codice al contesto di documentazione, utilizzando le informazioni generate da un compilatore o un interprete.  
  
-   Viene implementata da un [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Contesto del codice](../../extensibility/debugger/code-context.md)   
 [Provider di simboli](../../extensibility/debugger/symbol-provider.md)   
 [Interfacce del Provider di simboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)