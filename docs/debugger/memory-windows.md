---
title: Visualizzazione di memoria per le variabili nel Debugger | Documenti Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
caps.latest.revision: "32"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 96a4dc22f4f5c96d3dd9d40a565c2656ffe6e283
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger"></a>Utilizzare le finestre di memoria nel Debugger di Visual Studio
Il **memoria** finestra fornisce una visualizzazione nello spazio di memoria utilizzata dall'applicazione. Il **espressioni di controllo** finestra **controllo immediato** nella finestra di dialogo **Auto** finestra e **variabili locali** finestra Mostra il contenuto delle variabili, che sono archiviati in percorsi specifici in memoria. Ma la **memoria** finestra viene fornita un'immagine. Questa visualizzazione può essere opportuna quando si intende esaminare grandi porzioni di dati, ad esempio buffer o stringhe di notevoli dimensioni, che non vengono visualizzate adeguatamente nella altre finestre. Tuttavia, il **memoria** finestra non è limitata alla visualizzazione dei dati. Nella finestra Memoria viene visualizzato ogni tipo di contenuto dello spazio di memoria, sia che si tratti di dati, di codice o di contenuto eliminato e collocato casualmente in spazio di memoria non assegnato.  
  
 Il **memoria** è disponibile solo se il debug a livello di indirizzo è attivato nella finestra di **opzioni** nella finestra di dialogo **debug** nodo. Il **memoria** finestra non è disponibile per uno Script o SQL, sono linguaggi che supportano il concetto di memoria.  
  
## <a name="opening-a-memory-window"></a>Apertura di una finestra Memoria  
  
#### <a name="to-open-a-memory-window"></a>Per aprire una finestra Memoria  
  
1.  Avviare il debug, se la modalità di debug non è ancora attiva.  
  
2.  Nel **Debug** dal menu **Windows**. Quindi, scegliere **memoria** e quindi fare clic su **memoria 1**, **memoria 2**, **memoria 3**, o **memoria 4**. (Le edizioni di livello inferiore [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un solo **memoria** finestra. Se si utilizza una di queste edizioni, fare clic su **memoria**.)  
  
## <a name="paging-in-the-memory-window"></a>Paging nella finestra Memoria  
 Il **memoria** finestra dispone di una barra di scorrimento verticale che funziona in modo non conforme allo standard. Poiché lo spazio degli indirizzi di un moderno computer è molto ampio, trascinando il cursore su una posizione casuale sarebbe facile perderne la posizione. Per questa ragione, la casella di scorrimento è fluttuante e rimane sempre al centro della barra di scorrimento. Nelle applicazioni in codice nativo è possibile spostarsi verso l'alto o verso il basso dello spazio di memoria, ma non è consentito lo scorrimento casuale.  
  
 Gli indirizzi di memoria superiori vengono visualizzati nella parte inferiore della finestra. Per visualizzare un indirizzo superiore, spostarsi verso il basso, non verso l'alto.  
  
#### <a name="to-page-up-or-down-in-memory"></a>Per spostarsi verso l'alto o verso il basso di una pagina di memoria  
  
1.  Per spostarsi verso il basso, ovvero verso un indirizzo di memoria superiore, fare clic sulla barra di scorrimento verticale sotto il cursore.  
  
2.  Per spostarsi verso l'alto, ovvero verso un indirizzo di memoria inferiore, fare clic sulla barra di scorrimento verticale sopra il cursore.  
  
## <a name="selecting-a-memory-location"></a>Selezione di un indirizzo di memoria  
 Se si desidera spostarsi immediatamente in una posizione selezionata in memoria, è possibile farlo tramite un'operazione di trascinamento e rilascio o modificando il valore di **indirizzo** casella. Il **indirizzo** casella accetta non solo valori numerici, ma anche espressioni che restituiscono indirizzi. Per impostazione predefinita, il **memoria** finestra considera un **indirizzo** espressione come un'espressione attiva, rivalutata durante l'esecuzione del programma. Le espressioni attive possono rivelarsi molto utili. Ad esempio, possono essere utilizzate per visualizzare la memoria selezionata da un puntatore.  
  
#### <a name="to-select-a-memory-location-by-dragging-and-dropping"></a>Per selezionare un indirizzo di memoria mediante trascinamento e rilascio  
  
1.  Da qualsiasi finestra selezionare un indirizzo di memoria o una variabile puntatore contenente un indirizzo di memoria.  
  
2.  Trascinare l'indirizzo o il puntatore di **memoria** finestra.  
  
#### <a name="to-select-a-memory-location-by-editing"></a>Per selezionare una posizione di memoria mediante modifica  
  
1.  Nel **memoria** finestra, seleziona il **indirizzo** casella.  
  
2.  Digitare o incollare l'indirizzo a cui si desidera visualizzare e quindi premere **invio**.  
  
## <a name="changing-the-way-the-memory-window-displays-information"></a>Modifica della modalità di visualizzazione delle informazioni nella finestra Memoria  
 È possibile personalizzare la modalità di **memoria** finestra viene visualizzato il contenuto della memoria. Per impostazione predefinita, il contenuto della memoria viene visualizzato come dati integer a 1 byte in formato esadecimale e con un numero di colonne determinato automaticamente dalla larghezza corrente della finestra.  
  
#### <a name="to-change-the-format-of-the-memory-contents"></a>Per cambiare il formato del contenuto della memoria  
  
1.  Fare doppio clic su di **memoria** finestra.  
  
2.  Scegliere il formato desiderato.  
  
#### <a name="to-change-the-number-of-columns-in-the-memory-window"></a>Per modificare il numero di colonne nella finestra Memoria  
  
1.  Nella barra degli strumenti nella parte superiore del **memoria** finestra, individuare il **colonne** elenco.  
  
2.  Nel **colonne** , selezionare il numero di colonne che si desidera visualizzare oppure selezionare **Auto** per l'adattamento alla larghezza della finestra.  
  
 Se non si desidera il contenuto del **memoria** finestra per modificare il programma viene eseguito, è possibile disattivare la valutazione dell'espressione in tempo reale.  
  
#### <a name="to-toggle-live-evaluation"></a>Per attivare o disattivare la valutazione diretta  
  
1.  Fare doppio clic su di **memoria** finestra.  
  
2.  Menu di scelta rapida, fare clic su **Rivaluta automaticamente**.  
  
     Se la valutazione diretta è attiva, l'opzione risulterà selezionata e facendo clic su di essa la valutazione diretta verrà disattivata. Se la valutazione diretta non è attiva, l'opzione risulterà deselezionata e facendo clic su di essa verrà attivata.  
  
 È possibile nascondere o visualizzare la barra degli strumenti nella parte superiore del **memoria** finestra. Non è possibile accedere alla casella Indirizzo o ad altri strumenti quando la barra degli strumenti è nascosta.  
  
#### <a name="to-toggle-the-toolbar"></a>Per attivare o disattivare la barra degli strumenti  
  
1.  Fare doppio clic su un **memoria** finestra.  
  
2.  Menu di scelta rapida, fare clic su **Mostra barra degli strumenti**.  
  
     La barra degli strumenti verrà visualizzata o nascosta, a seconda del precedente stato.  
  
## <a name="following-a-pointer-through-memory"></a>Come seguire il movimento di un puntatore in memoria  
 Nelle applicazioni in codice nativo è inoltre possibile utilizzare i nomi di registro come espressioni attive. È possibile, ad esempio, utilizzare il puntatore dello stack per seguire lo stack.  
  
#### <a name="to-follow-a-pointer-through-memory"></a>Per osservare il movimento di un puntatore in memoria  
  
1.  Nel **memoria** finestra **indirizzo** , digitare un'espressione puntatore. La variabile puntatore deve trovarsi nell'ambito corrente. A seconda del linguaggio, può essere necessario dereferenziarla.  
  
2.  Premere **INVIO**.  
  
     A questo punto, quando si utilizza un comando di esecuzione, ad esempio **passaggio**, l'indirizzo di memoria visualizzato cambierà automaticamente seguendo lo spostamento del puntatore.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)