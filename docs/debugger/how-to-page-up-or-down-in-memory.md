---
title: 'Procedura: PGSU o verso il basso nella memoria | Documenti Microsoft'
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
- JScript
helpviewer_keywords:
- debugger, paging up or down in memory
- memory, paging up or down
- Disassembly window, viewing memory space
- Memory window, paging up or down in memory
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0499fbf29e9bb16d0f5ff99c42f031d06e4fb4de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-page-up-or-down-in-memory"></a>Procedura: spostare verso l'alto o verso il basso una pagina di memoria
Quando si visualizza il contenuto della memoria in un **memoria** finestra o **Disassembly** finestra, è possibile utilizzare la barra di scorrimento verticale per spostarsi verso l'alto o verso il basso nello spazio di memoria.  
  
### <a name="to-page-up-or-down-in-memory"></a>Per spostarsi verso l'alto o verso il basso di una pagina di memoria  
  
1.  Per spostarsi verso il basso, ossia verso un indirizzo di memoria superiore, fare clic sulla barra di scorrimento verticale sotto la casella di scorrimento.  
  
2.  Per spostarsi verso l'alto, ossia verso un indirizzo di memoria inferiore, fare clic sulla barra di scorrimento verticale sopra la casella di scorrimento.  
  
 La barra di scorrimento verticale presenta un funzionamento particolare. Poiché lo spazio degli indirizzi di un moderno computer è molto ampio, trascinando la casella di scorrimento su una posizione casuale sarebbe facile perderne la posizione. Per questa ragione, la casella di scorrimento è fluttuante e rimane sempre al centro della barra di scorrimento. Nelle applicazioni in codice nativo è possibile spostarsi verso l'alto o verso il basso dello spazio di memoria, ma non è consentito lo scorrimento casuale.  
  
 Nelle applicazioni gestite, il disassembly è limitato a una sola funzione e lo scorrimento della finestra funziona in modo normale.  
  
 Gli indirizzi più alti sono visualizzati nella parte inferiore della finestra. Per visualizzare un indirizzo superiore, spostarsi verso il basso, non verso l'alto.  
  
#### <a name="to-move-up-or-down-one-instruction"></a>Per spostarsi verso l'alto o verso il basso di un'istruzione  
  
-   Fare clic sulla freccia all'estremità superiore o inferiore della barra di scorrimento verticale.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra memoria](../debugger/memory-windows.md)   
 [Procedura: utilizzare la finestra Disassembly](../debugger/how-to-use-the-disassembly-window.md)   
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)