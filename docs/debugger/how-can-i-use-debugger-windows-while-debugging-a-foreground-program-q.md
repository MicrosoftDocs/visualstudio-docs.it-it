---
title: "Come è possibile utilizzare le finestre debugger mentre si esegue il debug di un programma in primo piano? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.background
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ff822f88873ace2fe264a10dded5c0f0d252f5ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Come è possibile utilizzare le finestre debugger mentre si esegue il debug di un programma in primo piano?
## <a name="problem-description"></a>Descrizione del problema  
 Si sta tentando di effettuare il debug di un problema relativo a un disegno dello schermo. Per osservare questo problema è necessario mantenere il programma in primo piano, ma in questo modo è impossibile accedere alle finestre di debug. Come è possibile procedere?  
  
## <a name="solution"></a>Soluzione  
 Se si dispone di un secondo computer, sarà possibile ricorrere al debug remoto. Con una configurazione su due computer sarà possibile osservare il disegno dello schermo sul computer remoto mentre si esegue il debugger sull'host. Per ulteriori informazioni sul debug remoto, vedere [il debug remoto](../debugger/remote-debugging.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul codice nativo debug](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)