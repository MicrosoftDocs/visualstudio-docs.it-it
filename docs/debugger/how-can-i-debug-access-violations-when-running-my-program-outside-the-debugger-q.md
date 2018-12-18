---
title: "Come è possibile eseguire il debug di violazioni di accesso quando si esegue un programma fuori dal debugger? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0af98932a940126c8f7288d7b5c830bb40f270fe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Come è possibile eseguire il debug di violazioni di accesso quando si esegue un programma fuori dal debugger?
## <a name="problem-description"></a>Descrizione del problema  
 Il programma viene eseguito correttamente nell'ambiente di Visual Studio, ma quando viene eseguito autonomamente con il sistema operativo Windows, genera una violazione di accesso. Come è possibile effettuare il debug di questo problema?  
  
## <a name="solution"></a>Soluzione  
 Impostare il [Just-in-time debug](../debugger/just-in-time-debugging-in-visual-studio.md) opzione ed eseguire il programma autonomamente finché non si verifica la violazione di accesso. Quindi, nel **violazione di accesso** nella finestra di dialogo è possibile fare clic su **Annulla** per avviare il debugger.  
  
 Vedere inoltre l'articolo Q133174 di Knowledge Base "How to Locate Where a General Protection (GP) Fault Occurs". È possibile trovare articoli della Knowledge Base nel CD di MSDN Library o eseguendo una ricerca [http://support.microsoft.com/](http://support.microsoft.com/).  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul codice nativo debug](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)