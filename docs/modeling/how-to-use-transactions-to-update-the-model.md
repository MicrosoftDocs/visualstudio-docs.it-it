---
title: 'Procedura: utilizzare le transazioni per aggiornare il modello | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ecd9645bfb202d83bf672d03d3c6903a889677f9
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Procedura: utilizzare le transazioni per aggiornare il modello
Le transazioni assicurarsi che le modifiche apportate all'archivio vengono considerate come un gruppo. Le modifiche che vengono raggruppate possono essere eseguito il commit o rollback come unità singola.  
  
 Ogni volta che il codice del programma modifica, aggiunge o elimina qualsiasi elemento nell'archivio [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK deve essere eseguita all'interno di una transazione. Deve esistere un'istanza attiva di <xref:Microsoft.VisualStudio.Modeling.Transaction> associato all'archivio quando avviene la modifica. Questo vale per tutti gli elementi del modello, relazioni, forme, diagrammi e le relative proprietà.  
  
 Il meccanismo delle transazioni consente di evitare stati incoerenti. Se si verifica un errore durante una transazione, vengano eseguito il rollback di tutte le modifiche. Se l'utente esegue un comando di annullamento, ogni transazione di recente viene considerato come un unico passaggio. L'utente non è possibile annullare le parti di una modifica recente, a meno che non è in modo esplicito che tali in transazioni separate.  
  
## <a name="opening-a-transaction"></a>Apertura di una transazione  
 Il metodo più semplice di gestire una transazione è con un `using` istruzione racchiusa tra una `try...catch` istruzione:  
  
```  
Store store; ...  
try  
{  
  using (Transaction transaction =  
    store.TransactionManager.BeginTransaction("update model"))  
    // Outermost transaction must always have a name.  
  {  
    // Make several changes in Store:  
    Person p = new Person(store);  
    p.FamilyTreeModel = familyTree;  
    p.Name = "Edward VI";  
    // end of changes to Store  
  
    transaction.Commit(); // Don't forget this!  
  } // transaction disposed here  
}  
catch (Exception ex)  
{  
  // If an exception occurs, the Store will be   
  // rolled back to its previous state.  
}  
```  
  
 Se un'eccezione che impedisce finale `Commit()` si verifica durante le modifiche, l'archivio verrà reimpostato lo stato precedente. Questo permette di assicurarsi che gli errori non sia il modello in uno stato incoerente.  
  
 È possibile apportare qualsiasi numero di modifiche all'interno di una transazione. È possibile aprire nuove transazioni all'interno di una transazione attiva. Le transazioni nidificate devono eseguire il commit o il rollback prima della fine delle transazioni che lo contiene. Per ulteriori informazioni, vedere l'esempio per la <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> proprietà.  
  
 Per rendere permanenti le modifiche, è necessario `Commit` la transazione prima di eliminarlo. Se si verifica un'eccezione non rilevata all'interno della transazione, l'archivio verrà reimpostato sullo stato precedente le modifiche.  
  
## <a name="rolling-back-a-transaction"></a>Esecuzione del rollback di una transazione  
 Per garantire che l'archivio resta in oppure viene ripristinato lo stato della transazione, è possibile utilizzare una di queste strategie:  
  
1.  Generare un'eccezione non rilevata all'interno dell'ambito della transazione.  
  
2.  In modo esplicito il rollback della transazione:  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## <a name="transactions-do-not-affect-non-store-objects"></a>Operazioni non modificano gli oggetti Non Store  
 Le transazioni che disciplinano solo lo stato dell'archivio. È possibile annullare le modifiche parziali che sono state apportate a elementi esterni, ad esempio file, database o oggetti dichiarati con i tipi comuni all'esterno della definizione DSL.  
  
 Se un'eccezione potrebbe lasciare tale modifica non coerente con l'archivio, deve affrontare il possibilità nel gestore di eccezioni. Un modo per assicurarsi che le risorse esterne rimangano sincronizzate con gli oggetti dell'archivio è possibile unire ogni oggetto esterno a un elemento nell'archivio utilizzando i gestori di eventi. Per ulteriori informazioni, vedere [gestori propagare le modifiche di fuori di modello di eventi](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
## <a name="rules-fire-at-the-end-of-a-transaction"></a>Attivare le regole alla fine di una transazione  
 Alla fine di una transazione, prima dell'eliminazione della transazione, le regole associate agli elementi nell'archivio vengono attivate. Ogni regola è un metodo che viene applicato a un elemento del modello che è stato modificato. Ad esempio, esistono regole "Correggi" che aggiorna lo stato di una forma quando viene modificato il relativo elemento del modello e che creano una forma quando viene creato un elemento del modello. Non vi è alcun ordine di attivazione specificato. Una modifica eseguita da una regola possono essere attivati da un'altra regola.  
  
 È possibile definire regole personalizzate. Per ulteriori informazioni sulle regole, vedere [propagazione delle modifiche e risposta agli](../modeling/responding-to-and-propagating-changes.md).  
  
 Le regole non vengono attivati dopo un'operazione di annullamento, un ripristino o un comando di rollback.  
  
## <a name="transaction-context"></a>Contesto di transazione  
 Ogni transazione ha un dizionario in cui è possibile archiviare le informazioni desiderate:  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 Ciò è particolarmente utile per il trasferimento di informazioni tra le regole.  
  
## <a name="transaction-state"></a>Stato delle transazioni  
 In alcuni casi che è necessario per evitare la propagazione di una modifica se la modifica è causata dall'operazione di annullamento o ripetizione di una transazione. Ciò può verificarsi, ad esempio, se si scrive un gestore di valore di proprietà che è possibile aggiornare un altro valore nell'archivio. Poiché l'operazione di annullamento reimposta tutti i valori nell'archivio e ripristinarne lo stato precedente, non è necessario calcolare i valori aggiornati. Utilizzare questo codice:  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 Regole possono essere generato quando l'archivio inizialmente viene caricato da un file. Per evitare di rispondere a queste modifiche, utilizzare:  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```