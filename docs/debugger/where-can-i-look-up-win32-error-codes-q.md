---
title: Come è possibile accedere ai codici di errore di Win32? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81d919733f1caf654460cf342da05f2549dfa167
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Come è possibile accedere ai codici di errore di Win32?
Il file WINERROR.H nella directory INCLUDE della directory di installazione di sistema predefinita contiene le definizioni dei codici di errore per le funzioni API Win32.  
  
 È possibile cercare un codice di errore digitando il codice di **espressioni di controllo** finestra o **controllo immediato** la finestra di dialogo. Ad esempio:  
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul codice nativo debug](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)