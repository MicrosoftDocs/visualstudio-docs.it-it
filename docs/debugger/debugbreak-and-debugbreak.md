---
title: DebugBreak e DebugBreak | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DebugBreak
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 83128e4d5bd274013db1e7195e8182d021c257d5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak e __debugbreak
È possibile chiamare la funzione DebugBreak Win32 o [DebugBreak](/cpp/intrinsics/debugbreak) intrinseco in qualsiasi punto nel codice. `DebugBreak` e `__debugbreak` hanno lo spesso effetto dell'impostazione di un punto di interruzione nella stessa posizione.  
  
 Poiché `DebugBreak` è una chiamata a una funzione di sistema, è necessario che siano installati i simboli di debug del sistema per garantire che vengano visualizzate le informazioni corrette sullo stack di chiamate dopo l'interruzione. In alternativa, le informazioni sullo stack di chiamate visualizzate dal debugger possono essere spostate di un frame. Se si usa `__debugbreak`, i simboli non sono obbligatori.  
  
## <a name="see-also"></a>Vedere anche  
 [Intrinseci del compilatore](/cpp/intrinsics/compiler-intrinsics)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)   
 [Specificare i simboli (PDB) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)