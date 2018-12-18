---
title: I server (Visual Studio SDK) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2904641e8188abc6ef2382b2da272a9f96fd0f81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="servers-visual-studio-sdk"></a>Server (Visual Studio SDK)
In termini di architettura del debugger, un **server**:  
  
-   È un contenitore di porte e i fornitori di porte e viene utilizzato per comunicare le porte e i fornitori di porte con gestore di sessione di debug (SDM) e motori di debug.  
  
-   Possibile identificarsi in base al nome ed enumerare le porte e i fornitori di porte.  
  
-   È rappresentato da un [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interfaccia, che viene implementato solo da Visual Studio (un'istanza di un server per ogni istanza di esecuzione di Visual Studio).  
  
## <a name="see-also"></a>Vedere anche  
 [Porte](../../extensibility/debugger/ports.md)   
 [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)   
 [Concetti di debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)