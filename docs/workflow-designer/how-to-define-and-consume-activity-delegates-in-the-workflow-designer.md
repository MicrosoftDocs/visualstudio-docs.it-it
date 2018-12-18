---
title: "Procedura: definire e utilizzare delegati di attività nella finestra di progettazione del flusso di lavoro | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: "3"
ms.author: sdanie
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 47bca660b28c82b870946fb436b92c13a5aab485
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Procedura: definire e utilizzare delegati di attività in Progettazione del flusso di lavoro
In [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] è inclusa una nuova finestra di progettazione predefinita dell'attività di <xref:System.Activities.Statements.InvokeDelegate>. Questa finestra di progettazione può essere usata per assegnare i delegati all'attività che derivano da <xref:System.Activities.ActivityDelegate>, come <xref:System.Activities.ActivityAction> o <xref:System.Activities.ActivityFunc%601>.  
  
### <a name="define-an-activity-delegate"></a>Definire un delegato dell'attività  
  
1.  In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]selezionare **File**, **New**, **progetto**. Selezionare il **flusso di lavoro** nodo a sinistra e **applicazione Console flusso di lavoro** modello sulla destra. Nome del progetto (se necessario) e fare clic su **Ok**.  
  
2.  Pulsante destro del mouse sul progetto in **Esplora** e selezionare **Aggiungi**, **nuovo elemento...** . Selezionare il **flusso di lavoro** nodo a sinistra e **attività** modello sulla destra. Nome alla nuova attività **Myforeach** e fare clic su **Ok**. L'attività verrà visualizzata nella finestra di progettazione flussi di lavoro.  
  
3.  Nella finestra di progettazione del flusso di lavoro, fare clic su di **argomenti** scheda.  
  
4.  Fare clic su **Crea argomento**. Denominare il nuovo argomento **elementi**.  
  
5.  Nel **tipo di argomento** colonna, selezionare **matrice di T []**.  
  
6.  Nel browser dei tipi, selezionare **oggetto**. Click **Ok**.  
  
7.  Fare clic su **Crea argomento** nuovamente. Denominare il nuovo argomento **corpo**. Nel **direzione** colonna per il nuovo argomento, selezionare **proprietà**.  
  
8.  Nella colonna di tipo di argomento, selezionare **Cerca tipi...**  
  
9. Nel browser dei tipi, immettere **ActivityAction** nel **nome del tipo** campo. Selezionare **ActivityAction\<T >** nella visualizzazione albero. Selezionare **oggetto** nell'elenco a discesa che viene visualizzato per assegnare il tipo **ActivityAction\<oggetto >** all'argomento.  
  
10. Trascinare un <xref:System.Activities.Statements.While> attività di **flusso di controllo** sezione della casella degli strumenti all'area di progettazione.  
  
11. Selezionare il <xref:System.Activities.Statements.While> attività e selezionare il **variabili** scheda.  
  
12. Selezionare **creare variabile**. Nome della nuova variabile **indice**.  
  
13. Nel **tipo di variabile** colonna, selezionare **Int32**. Lasciare il **ambito** come **mentre**e **predefinito** colonna vuota.  
  
14. Impostare il **condizione** proprietà del <xref:System.Activities.Statements.While> attività **indice < Items.Length;**.  
  
15. Trascinare un <xref:System.Activities.Statements.InvokeDelegate> attività dal **primitive** sezione della casella degli strumenti per la **corpo** del <xref:System.Activities.Statements.While> attività.  
  
16. Selezionare **corpo** nell'elenco a discesa delegato.  
  
17. Nel **proprietà** griglia per il <xref:System.Activities.Statements.InvokeDelegate> attività, fare clic su di **...**  pulsante il **argomenti del delegato** proprietà.  
  
18. Nel **valore** colonna dell'argomento denominato **argomento**, immettere **Items [Index]**. Fare clic su **Ok** per chiudere la **DelegateArguments** finestra di dialogo.  
  
19. Trascinare un'attività di <xref:System.Activities.Statements.Assign> sulla riga orizzontale al di sotto dell'attività di <xref:System.Activities.Statements.InvokeDelegate>. Il <xref:System.Activities.Statements.Assign> verrà creata l'attività e un <xref:System.Activities.Statements.Sequence> attività verrà creato automaticamente per contenere le due attività nel **corpo** sezione la **MyForEach** attività. La sequenza è necessaria poiché il **corpo** sezione può contenere solo una singola attività. La creazione automatica di una nuova attività <xref:System.Activities.Statements.Sequence> è una nuova funzionalità di [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)].  
  
20. Impostare il **a** proprietà del <xref:System.Activities.Statements.Assign> attività **indice**. Impostare il **valore** proprietà del **assegnare** attività **index + 1**.  
  
 L'oggetto personalizzato **MyForEach** attività richiamerà un'attività arbitraria una volta per ogni valore passato tramite la **elementi** insieme con i valori nella raccolta come input per l'attività.  
  
### <a name="use-the-custom-activity-in-a-workflow"></a>Usare l'attività personalizzata in un flusso di lavoro  
  
1.  Compilare il progetto premendo **Ctrl + MAIUSC + B**.  
  
2.  In **Esplora**aprire **Workflow1** nella finestra di progettazione.  
  
3.  Trascinare un **MyForEach** attività dalla casella degli strumenti all'area di progettazione. L'attività si troverà in una sezione della casella degli strumenti con lo stesso nome del progetto.  
  
4.  Impostare il **elementi** proprietà del **MyForEach** attività **new Object [] {1, "abc"}**.  
  
5.  Trascinare un <xref:System.Activities.Statements.WriteLine> attività dal **primitive** sezione della casella degli strumenti per la **Delegate: Body** sezione del **MyForEach** attività.  
  
6.  Impostare il **testo** proprietà del <xref:System.Activities.Statements.WriteLine> attività **argument**.  
  
 Quando il flusso di lavoro viene eseguito, nella console verrà visualizzato quanto segue:  
  
 **1**   
**ABC**