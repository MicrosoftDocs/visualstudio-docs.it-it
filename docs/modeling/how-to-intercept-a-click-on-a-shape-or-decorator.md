---
title: 'Procedura: intercettare un clic su una forma o un elemento Decorator | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a4e096209c462452a7956f89560edaa74d8678cc
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-intercept-a-click-on-a-shape-or-decorator"></a>Procedura: intercettare un clic su una forma o su un elemento Decorator
Le procedure seguenti viene illustrato come intercettare un clic su una forma o un elemento decorator icona. È possibile intercettare fa clic su, fa doppio clic, trascina, e altre azioni e rendere l'elemento di rispondere.  
  
## <a name="to-intercept-clicks-on-shapes"></a>Per intercettare fa clic su forme  
 Nel progetto Dsl, in un file di codice separato dal file del codice generato, scrivere una definizione di classe parziale per la classe della forma. Eseguire l'override `OnDoubleClick()` o uno degli altri metodi il cui nome inizia con `On...`. Ad esempio:  
  
```  
public partial class MyShape // change  
  {  
    public override void OnDoubleClick(DiagramPointEventArgs e)  
    {  
      base.OnDoubleClick(e);  
      System.Windows.Forms.MessageBox.Show("Click");  
      e.Handled = true;  
  }  }  
```  
  
> [!NOTE]
>  Impostare `e.Handled` a `true`, a meno che non si desidera che l'evento da passare al contenitore forma o diagramma.  
  
## <a name="to-intercept-clicks-on-decorators"></a>Per intercettare i clic sugli elementi Decorator  
 Gli elementi Decorator immagine vengono eseguite in un'istanza della classe ImageField, che dispone di un metodo OnDoubleClick. Se si scrive una sottoclasse ImageField, è possibile intercettare i clic. I campi vengono impostati nel metodo InitializeShapeFields. Pertanto, è necessario modificare tale metodo per creare un'istanza di una sottoclasse anziché il ImageField regolare. Il metodo InitializeShapeFields è nel codice generato della classe shape. È possibile eseguire l'override della classe forma se si imposta il relativo `Generates Double Derived` proprietà come descritto nella procedura seguente.  
  
 Anche se InitializeShapeFields è un metodo di istanza, viene chiamato una sola volta per ogni classe. Di conseguenza, solo un'istanza di ClickableImageField esiste per ogni campo in ogni classe, non un'istanza per ciascuna forma nel diagramma. Quando l'utente fa doppio clic su un'istanza, è necessario identificare l'istanza è stato raggiunto, come illustrato nel codice dell'esempio.  
  
#### <a name="to-intercept-a-click-on-an-icon-decorator"></a>Per intercettare un clic su un elemento decorator icona  
  
1.  Aprire o creare una soluzione DSL.  
  
2.  Scegliere o creare una forma che dispone di un elemento decorator icona ed eseguirne il mapping a una classe di dominio.  
  
3.  In un file di codice separato dai file di `GeneratedCode` cartella, creare una nuova sottoclasse di ImageField:  
  
    ```  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Design;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
    using System.Collections.Generic;  
    using System.Linq;  
  
    namespace Fabrikam.MyDsl { // Change to your namespace  
    internal class ClickableImageField : ImageField  
    {  
      // You can also override OnClick and so on.  
      public override void OnDoubleClick(DiagramPointEventArgs e)  
      {  
        base.OnDoubleClick(e);  
        // Work out which instance was hit.  
        MyShape shapeHit = e.HitDiagramItem.Shape as MyShape;  
        if (shapeHit != null)  
        {  
          MyDomainClass element =   
              shapeHit.ModelElement as MyDomainClass;  
          System.Windows.Forms.MessageBox.Show(  
             "Double click on shape for " + element.Name);  
          // If we do not set Handled, the event will  
          // be passed to the containing shape:  
          e.Handled = true;  
        }  
      }  
  
       public ClickableImageField(string fieldName)  
         : base(fieldName)  
       { }  
    }  
    ```  
  
     È consigliabile impostare Handled su true se non si desidera l'evento deve essere passato alla forma che lo contiene.  
  
4.  Eseguire l'override del metodo InitializeShapeFields in classs la forma aggiungendo la seguente definizione di classe parziale.  
  
    ```  
    public partial class MyShape // change  
    {  
     protected override void InitializeShapeFields  
          (IList<ShapeField> shapeFields)  
     {  
      base.InitializeShapeFields(shapeFields);  
      // You can see the above method in MyShapeBase   
      // in the generated Shapes.cs  
      // It has already added fields for the Icons.  
      // So you will have to retrieve them and replace with your own.  
      ShapeField unwantedField = shapeFields.First  
          (field => field.Name == "IconDecorator1");  
      shapeFields.Remove(unwantedField);  
  
      // Now replicate the generated code from the base class   
      // in Shape.cs, but with your own image constructor.  
      ImageField field2 = new ClickableImageField("IconDecorator1");        
      field2.DefaultImage = ImageHelper.GetImage(  
        MyDslDomainModel.SingletonResourceManager  
        .GetObject("MyShapeIconDecorator1DefaultImage"));  
          shapeFields.Add(field2);  
    }  
    ```  
  
1.  Compilare ed eseguire la soluzione.  
  
2.  Fare doppio clic sull'icona in un'istanza della forma. Dovrebbe essere visualizzato il messaggio di test.  
  
## <a name="intercepting-clicks-and-drags-on-compartmentshape-lists"></a>Intercettazione fa clic e trascina sugli elenchi CompartmentShape  
 L'esempio seguente consente di riordinare gli elementi in una forma raggruppamento trascinandoli. Per eseguire questo codice:  
  
1.  Creare una nuova soluzione DSL utilizzando il **diagrammi classi** modello di soluzione.  
  
     È inoltre possibile utilizzare con una soluzione personalizzata che contiene le forme di raggruppamento. Questo codice si presuppone che esista una relazione di incorporamento tra gli elementi del modello rappresentati dalla forma e di elementi rappresentati in elementi dell'elenco di raggruppamento.  
  
2.  Impostare il **genera derivato doppie** proprietà della forma raggruppamento.  
  
3.  Aggiungere il codice in un file di **Dsl** progetto.  
  
4.  Modificare i nomi di classe e la forma di dominio in questo codice in modo che corrisponda il proprio modello DSL.  
  
 In breve, il codice funziona nel modo seguente. In questo esempio, `ClassShape` è il nome della forma raggruppamento.  
  
-   Quando viene creato, un set di gestori eventi del mouse è collegato a ogni istanza di raggruppamento.  
  
-   Il `ClassShape.MouseDown` evento archivia l'elemento corrente.  
  
-   Quando il puntatore del mouse si sposta all'esterno dell'elemento corrente, viene creata un'istanza di MouseAction, che imposta il cursore e acquisisce il mouse fino a quando non viene rilasciato.  
  
     Per evitare interferenze tra le altre azioni del mouse, ad esempio si seleziona il testo di un elemento, il MouseAction non viene creato fino a quando il mouse ha lasciato l'elemento originale.  
  
     Un'alternativa alla creazione di un MouseAction sarebbe sufficiente per ascoltare MouseUp. Tuttavia, questo metodo non funziona correttamente se l'utente rilascia il puntatore del mouse dopo averla trascinata all'esterno del contesto. Il MouseAction è in grado di eseguire l'azione appropriata, indipendentemente da dove viene rilasciato.  
  
-   Quando il mouse viene rilasciato, MouseAction.MouseUp riorganizzare l'ordine dei collegamenti tra gli elementi del modello.  
  
-   La modifica dell'ordine di ruolo viene attivata una regola che aggiorna la visualizzazione. Questo comportamento è già definito ed è richiesto alcun codice aggiuntivo.  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Design;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using System.Collections.Generic;  
using System.Linq;  
  
// This sample allows users to re-order items in a compartment shape by dragging.  
  
// This example is built on the "Class Diagrams" solution template of VMSDK (DSL Tools).  
// You will need to change the following domain class names to your own:  
// ClassShape = a compartment shape  
// ClassModelElement = the domain class displayed using a ClassShape  
// This code assumes that the embedding relationships   
// displayed in the compartments don't use inheritance   
// (don't have base or derived domain relationships).  
  
namespace Company.CompartmentDrag  
{  
 /// <summary>  
 /// Manage the mouse while dragging a compartment item.  
 /// </summary>  
 public class CompartmentDragMouseAction : MouseAction  
 {  
  private ModelElement sourceChild;  
  private ClassShape sourceShape;  
  private RectangleD sourceCompartmentBounds;  
  
  public CompartmentDragMouseAction(ModelElement sourceChildElement, ClassShape sourceParentShape, RectangleD bounds)  
   : base (sourceParentShape.Diagram)  
  {  
   sourceChild = sourceChildElement;  
   sourceShape = sourceParentShape;  
   sourceCompartmentBounds = bounds; // For cursor.  
  }  
  
  /// <summary>  
  /// Call back to the source shape to drop the dragged item.  
  /// </summary>  
  /// <param name="e"></param>  
  protected override void OnMouseUp(DiagramMouseEventArgs e)  
  {  
   base.OnMouseUp(e);  
   sourceShape.DoMouseUp(sourceChild, e);  
   this.Cancel(e.DiagramClientView);  
   e.Handled = true;  
  }  
  
  /// <summary>  
  /// Ideally, this shouldn't happen. This action should only be active  
  /// while the mouse is still pressed. However, it can happen if you  
  /// move the mouse rapidly out of the source shape, let go, and then   
  /// click somewhere else in the source shape.  
  /// </summary>  
  /// <param name="e"></param>  
  protected override void OnMouseDown(DiagramMouseEventArgs e)  
  {  
   base.OnMouseDown(e);  
   this.Cancel(e.DiagramClientView);  
   e.Handled = false;  
  }  
  
  /// <summary>  
  /// Display an appropriate cursor while the drag is in progress:  
  /// Up-down arrow if we are inside the original compartment.  
  /// No entry if we are elsewhere.  
  /// </summary>  
  /// <param name="currentCursor"></param>  
  /// <param name="diagramClientView"></param>  
  /// <param name="mousePosition"></param>  
  /// <returns></returns>  
  public override System.Windows.Forms.Cursor GetCursor(System.Windows.Forms.Cursor currentCursor, DiagramClientView diagramClientView, PointD mousePosition)  
  {  
   // If the cursor is inside the original compartment, show up-down cursor.  
   return sourceCompartmentBounds.Contains(mousePosition)   
    ? System.Windows.Forms.Cursors.SizeNS // Up-down arrow.  
    : System.Windows.Forms.Cursors.No;  
  }  
 }  
  
 /// <summary>  
 /// Override some methods of the compartment shape.  
 /// *** GenerateDoubleDerived must be set for this shape in DslDefinition.dsl. ****  
 /// </summary>  
 public partial class ClassShape  
 {  
  /// <summary>  
  /// Model element that is being dragged.  
  /// </summary>  
  private static ClassModelElement dragStartElement = null;  
  /// <summary>  
  /// Absolute bounds of the compartment, used to set the cursor.  
  /// </summary>  
  private static RectangleD compartmentBounds;  
  
  /// <summary>  
  /// Attach mouse listeners to the compartments for the shape.  
  /// This is called once per compartment shape.  
  /// The base method creates the compartments for this shape.  
  /// </summary>  
  public override void EnsureCompartments()  
  {  
   base.EnsureCompartments();  
   foreach (Compartment compartment in this.NestedChildShapes.OfType<Compartment>())  
   {  
    compartment.MouseDown += new DiagramMouseEventHandler(compartment_MouseDown);  
    compartment.MouseUp += new DiagramMouseEventHandler(compartment_MouseUp);  
    compartment.MouseMove += new DiagramMouseEventHandler(compartment_MouseMove);  
   }  
  }  
  
  /// <summary>  
  /// Remember which item the mouse was dragged from.  
  /// We don't create an Action immediately, as this would inhibit the  
  /// inline text editing feature. Instead, we just remember the details  
  /// and will create an Action when/if the mouse moves off this list item.  
  /// </summary>  
  /// <param name="sender"></param>  
  /// <param name="e"></param>  
  void compartment_MouseDown(object sender, DiagramMouseEventArgs e)  
  {  
   dragStartElement = e.HitDiagramItem.RepresentedElements  
     .OfType<ClassModelElement>().FirstOrDefault();  
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;  
  }  
  
  /// <summary>  
  /// When the mouse moves away from the initial list item,  
  /// but still inside the compartment, create an Action   
  /// to supervise the cursor and handle subsequent mouse events.  
  /// Transfer the details of the initial mouse position to the Action.  
  /// </summary>  
  /// <param name="sender"></param>  
  /// <param name="e"></param>  
  void compartment_MouseMove(object sender, DiagramMouseEventArgs e)  
  {  
   if (dragStartElement != null)  
   {  
    if (dragStartElement != e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault())  
    {  
     e.DiagramClientView.ActiveMouseAction = new CompartmentDragMouseAction(dragStartElement, this, compartmentBounds);  
     dragStartElement = null;  
    }  
   }  
  }  
  
  /// <summary>  
  /// User has released the mouse button.   
  /// </summary>  
  /// <param name="sender"></param>  
  /// <param name="e"></param>  
  void compartment_MouseUp(object sender, DiagramMouseEventArgs e)  
  {  
    dragStartElement = null;  
  }  
  
  /// <summary>  
  /// Forget the source item if mouse up occurs outside the  
  /// compartment.  
  /// </summary>  
  /// <param name="e"></param>  
  public override void OnMouseUp(DiagramMouseEventArgs e)  
  {  
   base.OnMouseUp(e);  
   dragStartElement = null;  
  }  
  
  /// <summary>  
  /// Called by the Action when the user releases the mouse.  
  /// If we are still on the same compartment but in a different list item,  
  /// move the starting item to the position of the current one.  
  /// </summary>  
  /// <param name="dragFrom"></param>  
  /// <param name="e"></param>  
  public void DoMouseUp(ModelElement dragFrom, DiagramMouseEventArgs e)  
  {  
   // Original or "from" item:  
   ClassModelElement dragFromElement = dragFrom as ClassModelElement;  
   // Current or "to" item:  
   ClassModelElement dragToElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();  
   if (dragFromElement != null && dragToElement != null)  
   {  
    // Find the common parent model element, and the relationship links:  
    ElementLink parentToLink = GetEmbeddingLink(dragToElement);  
    ElementLink parentFromLink = GetEmbeddingLink(dragFromElement);  
    if (parentToLink != parentFromLink && parentFromLink != null && parentToLink != null)  
    {  
     // Get the static relationship and role (= end of relationship):  
     DomainRelationshipInfo relationshipFrom = parentFromLink.GetDomainRelationship();  
     DomainRoleInfo parentFromRole = relationshipFrom.DomainRoles[0];  
     // Get the node in which the element is embedded, usually the element displayed in the shape:  
     ModelElement parentFrom = parentFromLink.LinkedElements[0];  
  
     // Same again for the target:  
     DomainRelationshipInfo relationshipTo = parentToLink.GetDomainRelationship();  
     DomainRoleInfo parentToRole = relationshipTo.DomainRoles[0];  
     ModelElement parentTo = parentToLink.LinkedElements[0];  
  
     // Mouse went down and up in same parent and same compartment:  
     if (parentTo == parentFrom && relationshipTo == relationshipFrom)  
     {  
      // Find index of target position:  
      int newIndex = 0;  
      var elementLinks = parentToRole.GetElementLinks(parentTo);  
      foreach (ElementLink link in elementLinks)  
      {  
       if (link == parentToLink) { break; }  
       newIndex++;  
      }  
  
      if (newIndex < elementLinks.Count)  
      {  
       using (Transaction t = parentFrom.Store.TransactionManager.BeginTransaction("Move list item"))  
       {  
        parentFromLink.MoveToIndex(parentFromRole, newIndex);  
        t.Commit();  
       }  
      }  
     }  
    }  
   }  
  }  
  
  /// <summary>  
  /// Get the embedding link to this element.  
  /// Assumes there is no inheritance between embedding relationships.  
  /// (If there is, you need to make sure you've got the relationship  
  /// that is represented in the shape compartment.)  
  /// </summary>  
  /// <param name="child"></param>  
  /// <returns></returns>  
  ElementLink GetEmbeddingLink(ClassModelElement child)  
  {  
   foreach (DomainRoleInfo role in child.GetDomainClass().AllEmbeddedByDomainRoles)  
   {  
    foreach (ElementLink link in role.OppositeDomainRole.GetElementLinks(child))  
    {  
     // Just the assume the first embedding link is the only one.  
     // Not a valid assumption if one relationship is derived from another.  
     return link;  
    }  
   }  
   return null;  
  }  
 }  
}  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Risponde a e la propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md)   
 [Proprietà degli elementi Decorator](../modeling/properties-of-decorators.md)