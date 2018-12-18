---
title: Aggiornamento forme e connettori in modo da riflettere il modello | Documenti Microsoft
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
ms.openlocfilehash: 6d50d0258a44553451deed68a8ccf17c60d88965
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>Aggiornamento di forme e di connettori per riflettere il modello
In un linguaggio specifico di dominio in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è possibile apportare l'aspetto di una forma riflettono lo stato del modello sottostante.  
  
 Gli esempi di codice in questo argomento devono essere aggiunto a un `.cs` file nel `Dsl` progetto. È necessario che queste istruzioni in ogni file:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Impostare le proprietà di mappa di forme per controllare la visibilità di un elemento decorator  
 È possibile controllare la visibilità di un elemento decorator senza scrivere codice programma, configurando il mapping tra la forma e la classe di dominio nella definizione del linguaggio DSL. Per ulteriori informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md).
  
## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Esporre il colore e lo stile di una forma come proprietà  
 Nella definizione del linguaggio DSL, fare doppio clic su classe shape, scegliere **aggiungere esposti**, quindi fare clic su uno degli elementi, ad esempio **colore riempimento**.  
  
 A questo punto, la forma ha una proprietà che è possibile impostare nel codice programma o come un utente di dominio. Per impostare il codice del programma di un comando o una regola, ad esempio, è possibile scrivere:  
  
 `shape.FillColor = System.Drawing.Color.Red;`  
  
 Se si desidera rendere la variabile di proprietà solo nel controllo del programma e non dall'utente, selezionare la nuova proprietà di dominio, ad esempio **colore riempimento** nel diagramma definizione DSL. Quindi, nella finestra Proprietà impostare **è esplorabile** a `false` o impostare **è Readonly dell'interfaccia utente** a `true`.  
  
## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Definire le regole di modifica per colore, stile o il percorso dipende dalle proprietà di elemento di modello  
 È possibile definire regole che aggiornano l'aspetto della forma dipende da altre parti del modello. Ad esempio, è possibile definire una regola di modifica su un elemento del modello che aggiorna il colore della relativa forma dipende dalla proprietà dell'elemento del modello. Per ulteriori informazioni sulle regole di modifica, vedere [propagare le modifiche all'interno di modello di regole](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Utilizzare le regole solo per aggiornare le proprietà che vengono gestite all'interno dell'archivio, poiché le regole non vengono richiamate quando viene eseguito il comando Annulla. Non include alcune funzionalità grafiche, ad esempio le dimensioni e la visibilità di una forma. Per aggiornare le funzionalità di una forma, vedere [le funzionalità di aggiornamento dell'archivio Non grafica](#OnAssociatedProperty).  
  
 Nell'esempio seguente si presuppone che sia stata esposta `FillColor` come una proprietà di dominio come descritto nella sezione precedente.  
  
```csharp  
[RuleOn(typeof(ExampleElement))]  
  class ExampleElementPropertyRule : ChangeRule  
  {  
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)  
    {  
      base.ElementPropertyChanged(e);  
      ExampleElement element = e.ModelElement as ExampleElement;  
      // The rule is called for every property that is updated.  
      // Therefore, verify which property changed:  
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)  
      {  
        // There is usually only one shape:  
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))  
        {  
          ExampleShape shape = pel as ExampleShape;  
          // Replace this with a useful condition:  
          shape.FillColor = element.Name.EndsWith("3")   
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;  
        }  
      }  
    }  
  }  
  // The rule must be registered:  
  public partial class OnAssociatedPropertyExptDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(ExampleElementPropertyRule));  
      // If you add more rules, list them here.   
      return types.ToArray();  
    }  
  }  
  
```  
  
## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Utilizzare OnChildConfigured per inizializzare le proprietà di una forma  
 Per impostare le proprietà di una forma quando viene inizialmente creato, la sostituzione `OnChildConfigured()` in una definizione parziale della classe del diagramma. La classe diagramma è specificata nella definizione del linguaggio DSL e il codice generato è in **Dsl\Generated Code\Diagram.cs**. Ad esempio:  
  
```csharp  
partial class MyLanguageDiagram  
{  
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)  
  {  
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);  
    ExampleShape shape = child as ExampleShape;  
    if (shape != null)   
    {  
      if (!createdDuringViewFixup) return; // Ignore load from file.  
      ExampleElement element = shape.ModelElement as ExampleElement;  
      // Replace with a useful condition:  
      shape.FillColor = element.Name.EndsWith("3")   
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;  
    }  
    // else deal with other types of shapes and connectors.  
  }  
}  
  
```  
  
 Questo metodo può essere utilizzato sia per le proprietà di dominio e non dell'archivio di funzionalità, ad esempio la dimensione della forma.  
  
##  <a name="OnAssociatedProperty"></a>Utilizzare AssociateValueWith per aggiornare altre funzionalità di una forma  
 Per alcune funzionalità di una forma, ad esempio se dispone di un'ombreggiatura o lo stile della freccia di un connettore, non è presente alcun metodo incorporato di esporre la funzionalità come una proprietà di dominio.  Le modifiche apportate a tali funzionalità non sono sotto il controllo del sistema delle transazioni. Pertanto, non è appropriato per aggiornarli utilizzando le regole, poiché le regole non viene richiamate quando l'utente esegue il comando Annulla.  
  
 In alternativa, è possibile aggiornare tali funzionalità tramite <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>. Nell'esempio seguente, è possibile controllare lo stile della freccia di un connettore da un valore di una proprietà di dominio nella relazione che consente di visualizzare il connettore:  
  
```  
public partial class ArrowConnector // My connector class.   
{  
   /// <summary>  
    /// Called whenever a registered property changes in the associated model element.  
    /// </summary>  
    /// <param name="e"></param>  
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)  
    {  
      base.OnAssociatedPropertyChanged(e);  
      // Can be called for any property change. Therefore,  
      // Verify that this is the property we're interested in:  
      if ("IsDirected".Equals(e.PropertyName))  
      {  
        if (e.NewValue.Equals(true))  
        { // Update the shape's built-in Decorator feature:  
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;  
        }  
        else  
        {  
          this.DecoratorTo = null; // No arrowhead.  
        }  
      }  
    }  
    // OnAssociatedPropertyChanged is called only for properties  
    // that have been registered using AssociateValueWith().  
    // InitializeResources is a convenient place to call this.  
    // This method is invoked only once per class, even though  
    // it is an instance method.   
    protected override void InitializeResources(StyleSet classStyleSet)  
    {  
      base.InitializeResources(classStyleSet);  
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);  
      // Add other properties here.  
    }  
}  
  
```  
  
 `AssociateValueWith()`deve essere chiamato una volta per ogni proprietà del dominio che si desidera registrare. Dopo che è stato chiamato, tutte le modifiche alla proprietà specificata chiamerà `OnAssociatedPropertyChanged()` in tutte le forme che presentano l'elemento del modello della proprietà.  
  
 Non è necessario chiamare `AssociateValueWith()` per ogni istanza. Anche se InitializeResources è un metodo di istanza, viene richiamato solo una volta per ogni classe della forma.
