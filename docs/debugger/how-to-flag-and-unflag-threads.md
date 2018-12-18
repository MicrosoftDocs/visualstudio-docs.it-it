---
title: 'Procedura: impostare e rimuovere i flag dei thread | Documenti Microsoft'
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
helpviewer_keywords: treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 489403e4ce5052cb526a361e4548ab8823a20b18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-flag-and-unflag-threads"></a>Procedura: impostare e rimuovere i flag dei thread
È possibile contrassegnare un thread che si desidera prestare particolare attenzione mediante un'icona nella **thread**, **stack in parallelo** (visualizzazione thread), **espressioni di controllo parallelo**e  **Thread GPU** windows. Questa icona può essere d'aiuto all'utente e ad altri per distinguere i thread con flag dagli altri thread.  
  
I thread con flag ricevono inoltre un trattamento speciale nel **Thread** elenco il **posizione di Debug** barra degli strumenti e le altre finestre di debug con multithreading. È possibile visualizzare tutti i thread o solo i thread con flag nel **Thread** elenco o nelle altre finestre.
  
### <a name="to-flag-or-unflag-a-thread"></a>Per aggiungere o rimuovere flag che contrassegnano un thread 
  
-   Nel **thread** o **espressioni di controllo parallelo** finestra, individuare il thread si è interessati e fare clic sull'icona del flag per selezionare o deselezionare il flag. 
-   Nel **stack in parallelo** pulsante destro del mouse su un thread o un gruppo di thread e selezionare finestra **Flag / <thread>**  o **Rimuovi flag / <thread>** .
  
### <a name="to-unflag-all-threads"></a>Per rimuovere i flag di tutti thread  
  
-   Nel **thread** , fare doppio clic su qualsiasi thread e quindi fare clic su **Rimuovi flag di tutti i thread**.
-   Nel **espressioni di controllo parallelo** finestra, seleziona tutti i thread con flag del mouse e scegliere **Rimuovi flag**.  
  
### <a name="to-display-only-flagged-threads"></a>Per visualizzare solo i thread con flag  
  
-   Scegliere il **Mostra solo con flag thread** pulsante in una delle finestre di debug con multithreading.  
  
### <a name="to-flag-just-my-code"></a>Per contrassegnare Just My Code  
  
1.  Sulla barra degli strumenti nella parte superiore del **thread** finestra, fare clic sull'icona del flag.  
  
2.  Nell'elenco a discesa, fare clic su **Contrassegna Just My Code**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Per contrassegnare thread associati ai moduli selezionati  
  
1.  Nella barra degli strumenti di **thread** finestra, fare clic sull'icona del flag.  
  
2.  Nell'elenco a discesa, fare clic su **Contrassegna selezione moduli personalizzata**.  
  
3.  Nel **Seleziona moduli** finestra di dialogo, selezionare i moduli desiderati.  
  
4.  (Facoltativo) Nel **ricerca** , digitare una stringa da cercare moduli specifici.  
  
5.  Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Introduzione al debug di applicazioni multithreading](../debugger/get-started-debugging-multithreaded-apps.md)  
 [Procedura dettagliata: Debug di applicazioni multithreading utilizzando la finestra thread](../debugger/how-to-use-the-threads-window.md)