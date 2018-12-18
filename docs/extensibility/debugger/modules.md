---
title: I moduli | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f587e015263336436588d14edeeb5c6935872950
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="modules"></a>Moduli
In termini di architettura del debugger, un **modulo**:  
  
-   È un contenitore fisico di codice, ad esempio un file eseguibile o una DLL.  
  
-   Possibile ricaricare i simboli e descrivere se stesso. Descrizioni dei moduli vengono visualizzati nella finestra moduli dell'IDE.  
  
-   È rappresentato da un [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interfaccia, creato da un motore di debug per descrivere il modulo.  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti di debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)