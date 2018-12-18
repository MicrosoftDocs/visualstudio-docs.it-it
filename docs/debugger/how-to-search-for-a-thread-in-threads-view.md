---
title: 'Procedura: cercare un Thread nella visualizzazione thread | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b5eee67e195821f89dbd820f930288eb24f20a11
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Procedura: cercare un thread nella visualizzazione thread
È possibile cercare un thread specifico nella visualizzazione thread da utilizzare come il relativo thread ID o un modulo criteri di ricerca. È inoltre possibile specificare la direzione iniziale della ricerca. I campi nella finestra di dialogo verranno visualizzati gli attributi del thread selezionato nell'albero del thread.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Per cercare un thread nella visualizzazione thread  
  
1.  Disporre le finestre in modo che Spy + + e attivo [visualizzazione thread](../debugger/threads-view.md) finestra sono visibili.  
  
2.  Dal **ricerca** menu, scegliere **trova Thread**.  
  
     Il [dialogo Ricerca Thread](../debugger/thread-search-dialog-box.md) apre.  
  
3.  Digitare l'ID del thread o un modulo come criterio di ricerca.  
  
4.  Deselezionare tutti i campi per cui non si desidera specificare i valori.  
  
    > [!TIP]
    >  Per trovare tutti i thread di proprietà di un modulo, cancellare il **Thread** casella di testo e il modulo di tipo nome nel **modulo** casella. Utilizzare quindi **Trova successivo** per continuare la ricerca per i thread.  
  
5.  Scegliere **backup** o **verso il basso** per la direzione iniziale della ricerca.  
  
6.  Fare clic su **OK**.  
  
 Se il thread corrispondente viene trovato, evidenziarlo nella finestra di visualizzazione thread.