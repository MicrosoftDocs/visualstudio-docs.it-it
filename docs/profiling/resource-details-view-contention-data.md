---
title: 'Visualizzazione Dettagli risorsa: dati sui conflitti | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcedetails
helpviewer_keywords:
- Resource Details view
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac06fa18ee9459d8dc43bd0c536b68f9d027c97d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="resource-details-view---contention-data"></a>Visualizzazione Dettagli risorsa: dati sui conflitti
La visualizzazione Dettagli risorsa presenta un grafico della sequenza temporale degli eventi di blocco causati dai conflitti relativi a una risorsa selezionata. Si verifica un evento di blocco quando un thread viene indotto a sospendere l'esecuzione perché un altro thread ha bloccato l'accesso alla risorsa.  
  
 In questa visualizzazione la sequenza temporale dell'esecuzione di ciascun thread è rappresentata come una barra orizzontale, mentre ogni evento di blocco è rappresentato come una barra verticale nella sequenza temporale del thread. Se necessario, è possibile ingrandire una sezione della sequenza temporale per visualizzare i singoli eventi. Per visualizzare il percorso di esecuzione (stack di chiamate) delle funzioni che hanno condotto all'evento, fare clic sulla barra dell'evento. Le funzioni verranno visualizzate nella finestra **Stack di chiamate**. Quando è disponibile il codice sorgente per una funzione, è possibile fare clic sul nome della funzione per modificare il file di origine nell'interfaccia per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-magnify-a-timeline-segment"></a>Per ingrandire un segmento della sequenza temporale  
  
-   Trascinare il puntatore del mouse su un'area della sequenza temporale.  
  
     Quando si rilascia il pulsante del mouse, il segmento temporale selezionato viene ingrandito. È possibile ripetere il processo per ingrandire ulteriormente il segmento. La casella di scorrimento sulla barra di scorrimento temporale rappresenta la dimensione relativa del segmento di tempo che compare nella visualizzazione.  
  
#### <a name="to-zoom-out-on-a-timeline"></a>Per eseguire lo zoom avanti o indietro in una sequenza temporale  
  
-   Effettuare uno dei passaggi indicati di seguito.  
  
    -   Fare clic su **Zoom indietro** per tornare al livello di zoom precedente.  
  
    -   Fare clic su **Reimposta Zoom** per mostrare l'intera sequenza temporale nella visualizzazione.  
  
#### <a name="to-view-the-call-stack-of-an-event"></a>Per visualizzare lo stack di chiamate di un evento  
  
-   Nel grafico della sequenza temporale fare clic sulla barra dell'evento.  
  
#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Per visualizzare o modificare il codice sorgente di una funzione nello stack di chiamate  
  
-   Nella finestra **Stack di chiamate** fare clic sul nome della funzione.  
  
 Il codice sorgente della funzione deve far parte del progetto corrente.  
  
#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>Per visualizzare l'albero delle chiamate degli eventi di conflitto per la risorsa  
  
-   Nel grafico della sequenza temporale fare clic su **Totale**.  
  
     Viene visualizzata la visualizzazione Conflitti per la risorsa. Per altre informazioni, vedere [Visualizzazione relativa ai conflitti di risorse](../profiling/resource-contentions-view-contention-data.md).  
  
#### <a name="to-view-all-the-contention-events-of-a-thread"></a>Per visualizzare tutti gli eventi di conflitto di un thread  
  
-   Nel grafico della sequenza temporale fare clic sul nome o sull'ID del thread.  
  
     Viene visualizzata la visualizzazione Dettagli thread per il thread selezionato. Per altre informazioni, vedere [Visualizzazione Dettagli thread](../profiling/thread-details-view-contention-data.md).