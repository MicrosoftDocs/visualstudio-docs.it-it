---
title: Le regole di propagano le modifiche all'interno del modello | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: af086275f641e3237f8d22308c960ad30240b647
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="rules-propagate-changes-within-the-model"></a>Le regole propagano le modifiche all'interno del modello
È possibile creare una regola di archivio per propagare una modifica da un elemento a un altro in Visualization and Modeling SDK (VMSDK). Quando si verifica una modifica a qualsiasi elemento nell'archivio, le regole vengono pianificate da eseguire, in genere quando viene eseguito il commit della transazione più esterna. Esistono diversi tipi di regole per diversi tipi di eventi, ad esempio l'aggiunta di un elemento o l'eliminazione. È possibile collegare regole a tipi specifici di elementi, forme o diagrammi. Molte funzioni incorporate sono definiti da regole: ad esempio, le regole di garantire che un diagramma viene aggiornato quando viene modificato il modello. È possibile personalizzare il linguaggio specifico di dominio tramite l'aggiunta di regole personalizzate.  
  
 Archivio regole sono particolarmente utili per la propagazione delle modifiche all'interno dell'archivio, vale a dire le modifiche a elementi del modello, relazioni, forme o connettori e dominio di proprietà. Le regole non vengono eseguiti quando l'utente richiama i comandi di annullamento o ripetizione. Al contrario, il gestore delle transazioni assicura che il contenuto dell'archivio viene ripristinato allo stato corretto. Se si desidera propagare le modifiche apportate alle risorse all'esterno dell'archivio, utilizzare gli eventi di archiviazione. Per ulteriori informazioni, vedere [gestori propagare le modifiche di fuori di modello di eventi](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
 Si supponga, ad esempio, che si desidera specificare che ogni volta che l'utente (o il codice) crea un nuovo elemento di tipo ExampleDomainClass, viene creato un ulteriore elemento di un altro tipo in un'altra parte del modello. È possibile scrivere un AddRule e associarlo a ExampleDomainClass. Scrivere il codice nella regola per creare l'elemento aggiuntiva.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
  
namespace ExampleNamespace  
{  
 // Attribute associates the rule with a domain class:  
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]  
 // The rule is a class derived from one of the abstract rules:  
 class MyAddRule : AddRule  
 {  
  // Override the abstract method:  
  public override void ElementAdded(ElementAddedEventArgs e)  
  {  
    base.ElementAdded(e);  
    ExampleDomainClass element = e.ModelElement;  
    Store store = element.Store;  
    // Ignore this call if we're currently loading a model:  
    if (store.TransactionManager.CurrentTransaction.IsSerializing)   
       return;  
  
    // Code here propagates change as required - for example:  
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);  
      echo.Name = element.Name;  
      echo.Parent = element.Parent;    
    }  
  }  
 // The rule must be registered:  
 public partial class ExampleDomainModel  
 {  
   protected override Type[] GetCustomDomainModelTypes()  
   {  
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
     types.Add(typeof(MyAddRule));  
     // If you add more rules, list them here.   
     return types.ToArray();  
   }  
 }  
}  
  
```  
  
> [!NOTE]
>  Il codice di una regola è necessario modificare lo stato solo degli elementi all'interno dell'archivio; ovvero, la regola deve modificare solo gli elementi del modello, le relazioni, forme, i connettori, diagrammi o le relative proprietà. Se si desidera propagare le modifiche apportate alle risorse all'esterno dell'archivio, definire gli eventi di archiviazione. Per ulteriori informazioni, vedere [gestori propagare le modifiche di fuori di modello di eventi](../modeling/event-handlers-propagate-changes-outside-the-model.md)  
  
### <a name="to-define-a-rule"></a>Per definire una regola  
  
1.  Definire la regola come prefisso di una classe con il `RuleOn` attributo. L'attributo la regola viene associata a uno di classi di dominio, relazioni o elementi del diagramma. La regola verrà applicata a ogni istanza di questa classe, che può essere astratta.  
  
2.  Registrare la regola aggiunta al set di restituito da `GetCustomDomainModelTypes()` nella classe di modello di dominio.  
  
3.  Derivare la classe di regola da una delle classi astratte regola e scrivere il codice del metodo di esecuzione.  
  
 Nelle sezioni seguenti vengono descritti questi passaggi in maggiore dettaglio.  
  
### <a name="to-define-a-rule-on-a-domain-class"></a>Per definire una regola in una classe di dominio  
  
-   In un file di codice personalizzato, definire una classe e prefisso di <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> attributo:  
  
    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value - but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  
  
    ```  
  
-   Il tipo di oggetto nel primo parametro può essere una classe di dominio, relazione di dominio, forma, connettore o diagramma. In genere, applicare le regole per le relazioni e classi di dominio.  
  
     Il `FireTime` è in genere `TopLevelCommit`. In questo modo si garantisce che la regola viene eseguita solo dopo avere apportate tutte le modifiche principali della transazione. Le alternative sono in linea, a cui viene eseguita la regola dopo la modifica. e LocalCommit, che esegue la regola alla fine della transazione corrente (che potrebbe non essere più esterna). È inoltre possibile impostare la priorità di una regola per influire sul relativo ordine nella coda, ma si tratta di un metodo affidabile per ottenere il risultato desiderato.  
  
-   È possibile specificare una classe astratta come tipo di oggetto.  
  
-   La regola si applica a tutte le istanze della classe dell'oggetto.  
  
-   Il valore predefinito per `FireTime` è TimeToFire.TopLevelCommit. In questo modo la regola da eseguire quando viene eseguito il commit della transazione più esterna. In alternativa, è TimeToFire.Inline. In questo modo la regola deve essere eseguito subito dopo l'evento di attivazione.  
  
### <a name="to-register-the-rule"></a>Per registrare la regola  
  
-   Aggiungere all'elenco dei tipi restituita dalla classe di regola `GetCustomDomainModelTypes` nel modello di dominio:  
  
    ```  
    public partial class ExampleDomainModel  
     {  
       protected override Type[] GetCustomDomainModelTypes()  
       {  
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
         types.Add(typeof(MyAddRule));  
         // If you add more rules, list them here.   
         return types.ToArray();  
       }  
     }  
  
    ```  
  
-   Se non si certi del nome della classe di modello di dominio, ricerca all'interno del file **Dsl\GeneratedCode\DomainModel.cs**  
  
-   Scrivere il codice in un file di codice personalizzato nel progetto DSL.  
  
### <a name="to-write-the-code-of-the-rule"></a>Per scrivere il codice della regola  
  
-   Derivare la classe di regola da una delle classi base seguenti:  
  
    |Classe base|Trigger|  
    |----------------|-------------|  
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|Viene aggiunto un elemento, un collegamento o una forma.<br /><br /> Consente di rilevare le nuove relazioni, oltre ai nuovi elementi.|  
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|Il valore di una proprietà di dominio viene modificato. L'argomento del metodo fornisce i valori vecchi e nuovi.<br /><br /> Per le forme, questa regola viene attivata quando l'oggetto incorporato `AbsoluteBounds` modifiche delle proprietà, se la forma viene spostata.<br /><br /> In molti casi, è preferibile eseguire l'override `OnValueChanged` o `OnValueChanging` nel gestore di proprietà. Questi metodi vengono chiamati prima e dopo la modifica. Al contrario, la regola viene eseguita in genere alla fine della transazione. Per ulteriori informazioni, vedere [gestori di Modifica valore proprietà dominio](../modeling/domain-property-value-change-handlers.md). **Nota:** questa regola non viene generata quando un collegamento viene creato o eliminato. Invece di scrivere un `AddRule` e `DeleteRule` per la relazione di dominio.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|Generato quando sta per eliminare un elemento o un collegamento. La proprietà ModelElement.IsDeleting è true fino alla fine della transazione.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|Eseguito quando un elemento o un collegamento è stato eliminato. La regola viene eseguita dopo che sono state eseguite tutte le altre regole, tra cui DeletingRules. ModelElement.IsDeleting è false e ModelElement.IsDeleted è true. Per consentire un annullamento successive, l'elemento non viene effettivamente rimosso dalla memoria, ma viene rimosso da Store.ElementDirectory.|  
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|Un elemento viene spostato dalla partizione di un archivio a un altro.<br /><br /> Si noti che questo non è correlato alla posizione di una forma grafica.|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|Questa regola si applica solo alle relazioni di dominio. Se si assegna in modo esplicito un elemento del modello a delle estremità di un collegamento di attivazione.|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|Generato quando l'ordine dei collegamenti verso o da un elemento viene modificata utilizzando i metodi MoveBefore o MoveToIndex su un collegamento.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|Eseguito quando viene creata una transazione.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|Eseguito quando sta per essere eseguito il commit della transazione.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|Eseguito quando la transazione è possibile eseguire il rollback.|  
  
-   Ogni classe dispone di un metodo che si esegue l'override. Tipo `override` nella classe per individuarlo. Il parametro di questo metodo identifica l'elemento che viene modificato.  
  
 Tenere presente i punti seguenti circa regole:  
  
1.  Il set di modifiche in una transazione potrebbe generare molte regole. In genere, le regole vengono eseguite quando viene eseguito il commit della transazione più esterna. Vengono eseguiti in un ordine non specificato.  
  
2.  Una regola viene sempre eseguita all'interno di una transazione. Pertanto, non si dispone di creare una nuova transazione per apportare modifiche.  
  
3.  Le regole non vengono eseguite quando viene eseguito il rollback di una transazione, o quando vengono eseguite le operazioni di annullamento o ripetizione. Queste operazioni Reimposta tutto il contenuto dell'archivio dello stato precedente. Pertanto, se la regola viene modificato lo stato di qualsiasi elemento all'esterno dell'archivio, potrebbe non tenere synchronism con l'archivio di contenuto. Per aggiornare lo stato di fuori dell'archivio, è preferibile utilizzare gli eventi. Per ulteriori informazioni, vedere [gestori propagare le modifiche di fuori di modello di eventi](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
4.  Alcune regole vengono eseguite quando un modello viene caricato dal file. Per determinare se è in corso il caricamento o il salvataggio, utilizzare `store.TransactionManager.CurrentTransaction.IsSerializing`.  
  
5.  Se il codice della regola crea più trigger di regola, verrà aggiunto alla fine dell'elenco di generazione dell'evento e verrà eseguiti prima del completamento della transazione. DeletedRules vengono eseguiti dopo tutte le altre regole. Una regola può eseguire più volte in una transazione, una volta per ogni modifica.  
  
6.  Per passare informazioni da e verso le regole, è possibile archiviare le informazioni di `TransactionContext`. Questo è solo un dizionario che viene mantenuto durante la transazione. Viene eliminato al termine della transazione. Gli argomenti dell'evento di ogni regola forniscono l'accesso a esso. Tenere presente che non vengono eseguite le regole in un ordine prestabilito.  
  
7.  Utilizzare le regole tenendo conto di altre alternative. Ad esempio, se si desidera aggiornare una proprietà quando viene modificato un valore, è consigliabile utilizzare una proprietà calcolata. Se si desidera vincolare le dimensioni o il percorso di una forma, utilizzare un `BoundsRule`. Se si desidera rispondere a una modifica nel valore della proprietà, aggiungere un `OnValueChanged` gestore per la proprietà. Per ulteriori informazioni, vedere [propagazione delle modifiche e risposta agli](../modeling/responding-to-and-propagating-changes.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente aggiorna una proprietà quando viene creata un'istanza di una relazione di dominio per collegare due elementi. Verrà attivata la regola non solo quando l'utente crea un collegamento in un diagramma, ma anche se il codice del programma crea un collegamento.  
  
 Per testare questo esempio, creare un linguaggio DSL utilizzando il modello di soluzione del flusso di attività, inserire il codice seguente in un file nel progetto Dsl. Compilare e quindi eseguire la soluzione, aprire il file di esempio nel progetto di debug. Creare un collegamento commento tra una forma di commento e un elemento del flusso. Il testo nel commento diventa report sull'elemento che si è connessi a più recente.  
  
 In pratica, è in genere necessario scrivere un DeleteRule per ogni AddRule.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.VisualStudio.Modeling;  
  
namespace Company.TaskRuleExample  
{  
  
  [RuleOn(typeof(CommentReferencesSubjects))]  
  public class RoleRule : AddRule  
  {  
  
    public override void ElementAdded(ElementAddedEventArgs e)  
    {  
      base.ElementAdded(e);  
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;  
      Comment comment = link.Comment;  
      FlowElement subject = link.Subject;  
      Transaction current = link.Store.TransactionManager.CurrentTransaction;  
      // Don't want to run when we're just loading from file:  
      if (current.IsSerializing) return;  
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";  
    }  
  
  }  
  
  public partial class TaskRuleExampleDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(RoleRule));  
      return types.ToArray();  
    }  
  }  
  
}  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [I gestori eventi propagano le modifiche apportate all'esterno del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [Le regole associate (BoundsRules) vincolano posizione e dimensione delle forme](../modeling/boundsrules-constrain-shape-location-and-size.md)