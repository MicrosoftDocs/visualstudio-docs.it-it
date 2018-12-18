---
title: Impossibile visualizzare il codice sorgente o Disassembly | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8795ee33a5fc96c979cb67636d3ce5dd23c1b665
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Impossibile visualizzare il codice sorgente o il disassembly
Il testo del messaggio di errore è il seguente:  
  
 Impossibile visualizzare il codice sorgente o disassembly relativo alla posizione corrente in cui si è interrotta l'esecuzione.  
  
 Questo messaggio di errore può essere visualizzato in alcune situazioni:  
  
-   È possibile che sia stato raggiunto un punto di interruzione in una posizione per la quale non esiste un codice sorgente, mentre si esegue il debug di un linguaggio che non supporta il disassembly. Aprire il **i punti di interruzione** finestra, individuare il punto di interruzione ed eliminarlo.  
  
-   Se si sta eseguendo il debug di script, è possibile che sia stato raggiunto un punto di interruzione mentre non esistevano thread nel programma. Scegliere **passaggio** o **continua** dal **Debug** menu per riprendere il debug.  
  
-   È possibile che per aspetti relativi alla sicurezza il debugger non sia stato in grado di leggere lo stack, il thread, il registro e altre informazioni sul contesto dal programma di cui si sta eseguendo il debug. Questa condizione si verifica più spesso se si esegue il debug di un'applicazione Web e non si dispone dell'autorizzazione corretta per accedere alla directory virtuale. Impostare la sicurezza anonima per la directory virtuale e riprovare.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/index.md) [Tour delle funzionalità del Debugger](../debugger/debugger-feature-tour.md)   
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)