---
title: Programma di controllo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 244f6c2113aef3b3c3576288a0c403d702d8b17a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="program-control"></a>Controllo del programma
In Visual Studio il debug, tutte le istruzioni seguenti e continuando routine si verificano a livello di programma:  
  
-   Imposta istruzione successiva, vale a dire l'impostazione di computer alla successiva istruzione da eseguire in un ambiente particolare fotogramma  
  
-   L'esecuzione, vale a dire, continuando a uscire dalla modalità di esecuzione di istruzioni  
  
-   L'esecuzione di istruzioni per l'istruzione successiva  
  
-   Continuare con la modalità di debug passo a passo corrente  
  
-   Sospensione di thread di contenuti dal programma  
  
-   Ripresa di thread di contenuti dal programma  
  
> [!NOTE]
>  Visualizzare lo stack di chiamate viene implementata a livello di thread. Per enumerare le informazioni di frame quando si visualizza lo stack di chiamate per un thread, è necessario implementare tutti i metodi del [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfaccia.  
  
## <a name="methods-of-program-control"></a>Metodi di controllo del programma  
 Nella tabella seguente sono illustrati i metodi di [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) che deve essere implementata per un motore di debug minima funzionale (DE) e il controllo dell'esecuzione.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continua l'esecuzione di tutti i thread contenuti da un programma da uno stato di arresto. Obbligatorio per il controllo dell'esecuzione.|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continua l'esecuzione di tutti i thread contenuti da un programma da uno stato di arresto. Obbligatorio per il controllo dell'esecuzione.|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Esegue un passaggio sul thread specificato. Continua l'esecuzione di tutti gli altri thread contenuti dal programma. Obbligatorio per il controllo dell'esecuzione.|  
  
 Per programmi con multithreading, è necessario implementare anche il [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) (metodo) e tutti i metodi del [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)