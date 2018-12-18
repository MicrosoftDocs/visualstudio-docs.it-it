---
title: Suggerimenti per il debug di thread in codice nativo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: c98f6bb1a738111d32b26c5b923abe41367e621e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Suggerimenti per il debug dei thread in codice nativo
Di seguito sono riportati alcuni suggerimenti che è possibile utilizzare durante il debug dei thread in codice nativo:  
  
-   È possibile visualizzare il contenuto del blocco di informazioni del Thread digitando `@TIB` nel **espressioni di controllo** finestra o **controllo immediato** la finestra di dialogo.  
  
-   È possibile visualizzare l'ultimo codice di errore per il thread corrente immettendo `@Err` nel **espressioni di controllo** finestra o **controllo immediato** la finestra di dialogo.  
  
-   Per il debug di applicazioni multithreading è possibile utilizzare le funzioni delle librerie di runtime del linguaggio C (CRT). Per altre informazioni, vedere [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).  
  
## <a name="see-also"></a>Vedere anche  
 [Il debug di applicazioni a thread multipli](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)