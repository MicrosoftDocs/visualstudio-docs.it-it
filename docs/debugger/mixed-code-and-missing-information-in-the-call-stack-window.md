---
title: Codice misto e informazioni mancanti nella finestra Stack di chiamate | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b2733cbf5d9b833ac23ee573e1f39e9c8750224
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Codice misto e informazioni mancanti nella finestra Stack di chiamate
A causa delle differenze tra gli stack di chiamate per il codice gestito e il codice nativo, il debugger non è sempre in grado di visualizzare lo stack di chiamate completo in caso di tipi di codice misti. Quando il codice nativo chiama codice gestito, è possibile notare le seguenti discrepanze nel **Stack di chiamate** finestra:  
  
-   Il frame nativo situato immediatamente di sopra del codice gestito è possibile che manchi il **Stack di chiamate** finestra. Per ulteriori informazioni, vedere [procedura: uscire da codice gestito quando sono visualizzati frame nativi dalla finestra Stack di chiamate](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
-   Per le applicazioni in modalità mista avviate all'esterno del debugger, il **Stack di chiamate** finestra può visualizzare solo il codice gestito e nessuno dei frame nativi saranno visibili.  
  
 Entrambi i casi sono piuttosto rari. Nella maggior parte delle chiamate native a codice gestito gli stack di chiamate verranno visualizzati in modo corretto.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Usare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md)