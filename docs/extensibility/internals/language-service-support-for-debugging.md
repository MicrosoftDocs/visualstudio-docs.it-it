---
title: Supporto del servizio di linguaggio per il debug | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 955c8fd4e9499fbacfc0f97ba6112803ef1e6d4a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="language-service-support-for-debugging"></a>Supporto del servizio di linguaggio per il debug
Un servizio di linguaggio può fornire funzionalità che supportano un debugger tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interfaccia. Queste funzionalità includono la convalida dei punti di interruzione e fornire un elenco di espressioni per la **Auto** finestra.  
  
 Tuttavia, è necessario disporre di un analizzatore di espressioni per eseguire il debug del linguaggio. L'analizzatore di espressioni è responsabile per la valutazione di espressioni per produrre valori durante il debug. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere:  
  
-   [Analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Esempio analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Output del compilatore  
 Il tipo di compilatore determina cosa è necessario eseguire per implementare il debug per il linguaggio. Se il compilatore è destinato il sistema operativo Windows e scrive un file con estensione pdb, è possibile eseguire il debug di programmi con il motore è integrato in Visual Studio di debug di codice nativo. Se il compilatore produce Microsoft intermediate language (MSIL), è possibile eseguire il debug di programmi con il codice gestito, debug di motore, è inoltre integrato in Visual Studio. Se il compilatore destinato a un sistema operativo proprietario o un ambiente di runtime diversi, è necessario scrivere il proprio motore di debug.  
  
 Per ulteriori informazioni sull'implementazione di debug per la lingua, vedere [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) in Visual Studio Debugging SDK.