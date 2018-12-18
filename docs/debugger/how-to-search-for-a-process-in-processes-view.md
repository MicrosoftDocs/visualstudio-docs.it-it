---
title: 'Procedura: cercare un processo nella visualizzazione processi | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 542c560805ef33e33519c055a6ed4a59285d0db9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Procedura: cercare un processo nella visualizzazione processi
È possibile cercare un processo specifico nella visualizzazione processi utilizzando la relativa stringa di ID o un modulo di processo come criterio di ricerca. È inoltre possibile specificare la direzione iniziale della ricerca. I campi nella finestra di dialogo verranno visualizzati gli attributi del processo selezionato nell'albero del processo.  
  
### <a name="to-search-for-a-process-in-processes-view"></a>Per cercare un processo nella visualizzazione processi  
  
1.  Disporre le finestre in modo che Spy + + e attivo [visualizzazione processi](../debugger/processes-view.md) finestra sono visibili.  
  
2.  Dal **ricerca** menu, scegliere **Trova processo**  
  
     Il [dialogo Ricerca processi](../debugger/process-search-dialog-box.md) apre.  
  
3.  Digitare l'ID del processo o un modulo come criterio di ricerca.  
  
4.  Deselezionare tutti i campi per cui non si desidera specificare i valori.  
  
    > [!TIP]
    >  Per trovare tutti i processi appartenenti a un modulo, cancellare il **processo** e digitare il nome del modulo nel **modulo** casella. Utilizzare quindi **Trova successivo** per continuare la ricerca dei processi.  
  
5.  Scegliere **backup** o **verso il basso** per la direzione iniziale della ricerca.  
  
6.  Fare clic su **OK**.  
  
 Se viene trovato un processo di corrispondenza, viene evidenziato nel **visualizzazione processo** finestra.