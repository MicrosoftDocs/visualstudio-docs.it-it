---
title: Come è possibile accedere ai codici di errore di Win32? | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7299139d05a47c079e1aeb29f3b61433cff33bb6
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658423"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Come è possibile accedere ai codici di errore di Win32?
Il file WINERROR.H nella directory INCLUDE della directory di installazione di sistema predefinita contiene le definizioni dei codici di errore per le funzioni API Win32.

 È possibile cercare un codice di errore digitando tale codice nella finestra **Espressioni di controllo** o nella finestra di dialogo **Controllo immediato**. Ad esempio:

`0x80000004,hr`

## <a name="see-also"></a>Vedere anche
- [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)