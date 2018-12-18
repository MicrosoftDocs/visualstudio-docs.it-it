---
title: Definizione di criteri di blocco per creare segmenti di sola lettura | Documenti Microsoft
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
ms.openlocfilehash: dc7e620c04e31a063bbe8fada68527d391f0a903
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definizione di un criterio di blocco per creare segmenti di sola lettura
L'API immutabilità del [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK consente a un programma di blocco o parte di un modello di linguaggio specifico di dominio (DSL) in modo che può essere letto ma non è stato modificato. Questa opzione di sola lettura, ad esempio, può essere utilizzata in modo che un utente è possibile chiedere ai colleghi di aggiungere annotazioni e verificare un modello DSL ma può impedire il Modifica originale.  
  
 Inoltre, come l'autore di un linguaggio DSL, è possibile definire un *criteri blocco.* Un criterio di blocco definisce quali blocchi sono consentite, non è consentito o bloccato. Ad esempio, quando si pubblica un linguaggio DSL, è possibile incoraggiare gli sviluppatori di terze parti per estenderlo con i nuovi comandi. Ma è anche possibile usare un criterio di blocco per impedire che modifica lo stato di sola lettura di parti specificate del modello.  
  
> [!NOTE]
>  Un criterio di blocco può essere aggirato tramite reflection. Fornisce un limite di deseleziona per gli sviluppatori di terze parti, ma non fornisce una protezione avanzata.  
  
 Ulteriori informazioni ed esempi sono disponibili in Visual Studio [Visualization and Modeling SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) sito Web.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
## <a name="setting-and-getting-locks"></a>Impostazione e recupero di blocchi  
 È possibile impostare blocchi nell'archivio, in una partizione o in un singolo elemento. Ad esempio, questa istruzione sarà impediscono l'eliminazione di un elemento del modello e anche impedirà le relative proprietà da modificare:  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 Possono essere utilizzati altri valori di blocco per impedire la modifica di relazioni, la creazione degli elementi, lo spostamento tra le partizioni e i collegamenti di ordinamento nuovamente in un ruolo.  
  
 I blocchi si applicano alle azioni dell'utente e al codice programma. Se il codice programma tenta di apportare una modifica, un `InvalidOperationException` verrà generata. I blocchi vengono ignorati in un'operazione di annullamento o ripetizione.  
  
 È possibile individuare se un elemento è un qualsiasi tipo di blocco in un determinato set tramite `IsLocked(Locks)` ed è possibile ottenere il set corrente di blocchi su un elemento utilizzando `GetLocks()`.  
  
 È possibile impostare un blocco senza utilizzare una transazione. Il database di blocco non è parte dell'archivio. Se si imposta un blocco in risposta a una modifica di un valore nell'archivio, ad esempio in OnValueChanged, si devono consentire le modifiche che fanno parte di un'operazione di annullamento.  
  
 Questi metodi sono metodi di estensione che sono definiti nel <xref:Microsoft.VisualStudio.Modeling.Immutability> dello spazio dei nomi.  
  
### <a name="locks-on-partitions-and-stores"></a>Blocca sulle partizioni e archivia  
 Blocchi possono inoltre essere applicati a partizioni e l'archivio. Un blocco che è impostato su una partizione si applica a tutti gli elementi nella partizione. Pertanto, ad esempio, l'istruzione seguente impedirà tutti gli elementi in una partizione in corso l'eliminazione, indipendentemente dagli Stati dei propri blocchi. Tuttavia, altri blocchi, ad esempio `Locks.Property` potrebbe comunque essere impostati su singoli elementi:  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 Un blocco che è impostato sull'archivio si applica a tutti i relativi elementi, indipendentemente dalle impostazioni di tale blocco su partizioni e gli elementi.  
  
### <a name="using-locks"></a>L'utilizzo dei blocchi  
 È possibile utilizzare i blocchi di implementare gli schemi, come negli esempi seguenti:  
  
-   Impedire modifiche a tutti gli elementi e relazioni, ad eccezione di quelli che rappresentano i commenti. Ciò consente agli utenti di aggiungere annotazioni di un modello senza modificarlo.  
  
-   Impedire modifiche nella partizione predefinito, ma consentire le modifiche nella partizione di diagramma. L'utente è possibile riorganizzare il diagramma, ma non è possibile modificare il modello sottostante.  
  
-   Non consentire modifiche all'archivio, ad eccezione di un gruppo di utenti che sono registrati in un database separato. Per altri utenti, il diagramma e il modello sono di sola lettura.  
  
-   Non consentire modifiche al modello se una proprietà booleana del diagramma è impostata su true. Specificare un comando di menu per modificare tale proprietà. In questo modo gli utenti che non apportano modifiche accidentalmente.  
  
-   Impedire l'aggiunta e l'eliminazione di elementi e relazioni di particolari classi, ma consentire le modifiche alle proprietà. Ciò consente agli utenti con un modulo predefinito in cui è possibile inserire le proprietà.  
  
## <a name="lock-values"></a>Valori di blocco  
 Blocchi possono essere impostati su un archivio, partizioni o singoli ModelElement. Blocchi è un `Flags` enumerazione: è possibile combinare i valori utilizzando ' &#124;'.  
  
-   Blocchi di un oggetto ModelElement includono sempre i blocchi delle relative partizioni.  
  
-   Blocchi di una partizione includono sempre i blocchi dell'archivio.  
  
 È possibile impostare un blocco su una partizione o archiviare e allo stesso tempo, disabilitare il blocco su un singolo elemento.  
  
|Valore|Vale a dire se `IsLocked(Value)` è true|  
|-----------|------------------------------------------|  
|nessuno|Nessuna restrizione.|  
|Proprietà|Impossibile modificare le proprietà di dominio degli elementi. Questa opzione non viene applicata alle proprietà che vengono generate dal ruolo di una classe di dominio in una relazione.|  
|Aggiunta|Impossibile creare nuovi elementi e i collegamenti in una partizione o l'archivio.<br /><br /> Non applicabile a `ModelElement`.|  
|Move|Elemento non può essere spostato tra partizioni se `element.IsLocked(Move)` è true, o se `targetPartition.IsLocked(Move)` è true.|  
|Eliminare|Un elemento non può essere eliminato se è impostato il blocco dell'elemento stesso o in uno qualsiasi degli elementi a cui verrebbe propagare l'eliminazione, come forme e gli elementi incorporati.<br /><br /> È possibile utilizzare `element.CanDelete()` per individuare se un elemento può essere eliminato.|  
|Riordinare|L'ordine dei collegamenti in un roleplayer non può essere modificato.|  
|RolePlayer|Il set di collegamenti che sono distribuiti in questo elemento non può essere modificato. Ad esempio, non è consentito inserire nuovi elementi in questo elemento. Questa operazione non influenza i collegamenti per il quale questo elemento è la destinazione.<br /><br /> Se questo elemento è un collegamento, l'origine e destinazione non sono interessate.|  
|Tutti|OR bit per bit degli altri valori.|  
  
## <a name="locking-policies"></a>Criteri di blocchi  
 L'autore di un linguaggio DSL, è possibile definire un *criteri blocco*. Un criterio di blocco Modera il funzionamento di SetLocks(), in modo che è possibile impedire blocchi specifici set o implica che è necessario impostare blocchi specifici. In genere, si utilizzerebbe un criterio di blocco per impedire agli utenti o agli sviluppatori di accidentalmente violare la destinazione di un linguaggio DSL, in modo che è possibile dichiarare una variabile `private`.  
  
 È inoltre possibile utilizzare un criterio di blocco impostare blocchi su tutti gli elementi dipende dal tipo dell'elemento. In questo modo `SetLocks(Locks.None)` viene sempre chiamato quando un elemento viene innanzitutto creato o deserializzato dal file.  
  
 Tuttavia, è possibile usare un criterio per variare i blocchi su un elemento durante il ciclo di vita. Per ottenere tale effetto, è consigliabile utilizzare chiamate a `SetLocks()`.  
  
 Per definire un criterio di blocco, è necessario:  
  
-   Creare una classe che implementi <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.  
  
-   Aggiungere questa classe per i servizi disponibili tramite DocData di tale linguaggio DSL.  
  
### <a name="to-define-a-locking-policy"></a>Per definire un criterio di blocco  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>presenta la seguente definizione:  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 Questi metodi vengono chiamati quando viene effettuata una chiamata a `SetLocks()` in un archivio, o partizioni ModelElement. Ogni metodo, viene fornito con un set di blocchi proposto. È possibile restituire il set di proposto oppure è possibile aggiungere o sottrarre blocchi.  
  
 Ad esempio:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{  
  public class MyLockingPolicy : ILockingPolicy  
  {  
    /// <summary>  
    /// Moderate SetLocks(this ModelElement target, Locks locks)  
    /// </summary>  
    /// <param name="element">target</param>  
    /// <param name="proposedLocks">locks</param>  
    /// <returns></returns>  
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)  
    {  
      // In my policy, users can never delete an element,  
      // and other developers cannot easily change that:  
      return proposedLocks | Locks.Delete);  
    }  
    public Locks RefineLocks(Store store, Locks proposedLocks)  
    {  
      // Only one user can change this model:  
      return Environment.UserName == "aUser"   
           ? proposedLocks : Locks.All;  
    }  
  
```  
  
 Per assicurarsi che gli utenti possono eliminare sempre elementi, anche se altre chiamate di codice`SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 Per impedire modifiche in tutte le proprietà di ogni elemento della MyClass:  
  
 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`  
  
### <a name="to-make-your-policy-available-as-a-service"></a>Per rendere i criteri disponibili come un servizio  
 Nel `DslPackage` del progetto, aggiungere un nuovo file che contiene codice analogo all'esempio seguente:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{   
  // Override the DocData GetService() for this DSL.  
  internal partial class YourDslDocData // Change  
  {  
    /// <summary>  
    /// Custom locking policy cache.  
    /// </summary>  
    private ILockingPolicy myLockingPolicy = null;  
  
    /// <summary>  
    /// Called when a service is requested.  
    /// </summary>  
    /// <param name="serviceType">Service requested</param>  
    /// <returns>Service implementation</returns>  
    public override object GetService(System.Type serviceType)  
    {  
      if (serviceType == typeof(SLockingPolicy)   
       || serviceType == typeof(ILockingPolicy))  
      {  
        if (myLockingPolicy == null)  
        {  
          myLockingPolicy = new MyLockingPolicy();  
        }  
        return myLockingPolicy;  
      }  
      // Request is for some other service.  
      return base.GetService(serviceType);  
    }  
}  
```
