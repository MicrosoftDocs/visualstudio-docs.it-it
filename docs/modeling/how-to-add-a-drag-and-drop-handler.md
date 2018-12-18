---
title: 'Procedura: aggiungere un gestore di trascinamento della selezione'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8b8d77f973ef58f7273ff5390828707f1d05c46c
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="how-to-add-a-drag-and-drop-handler"></a>Procedura: aggiungere un gestore di trascinamento della selezione
È possibile aggiungere al linguaggio DSL gestori per gli eventi di trascinamento della selezione, in modo che gli utenti possano trascinare gli elementi sul diagramma da altri diagrammi o da altre parti di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È possibile aggiungere gestori anche per eventi come il doppio clic. Insieme, i gestori di trascinamento e rilascio e fare doppio clic sono note come *gestori di movimento*.

 Questo argomento illustra i movimenti di trascinamento della selezione originati in altri diagrammi. Per gli eventi di spostamento e copia in uno stesso diagramma, considerare come alternativa la possibilità di definire una sottoclasse di `ElementOperations`. Per ulteriori informazioni, vedere [personalizzazione copia comportamento](../modeling/customizing-copy-behavior.md). È anche possibile personalizzare la definizione DSL.

## <a name="in-this-topic"></a>In questo argomento

-   Le prime due sezioni descrivono i metodi alternativi per definire un gestore movimenti:

    -   [Definire i gestori di movimento dai metodi di override ShapeElement](#overrideShapeElement). È possibile eseguire l'override di `OnDragDrop`, `OnDoubleClick`, `OnDragOver` e di altri metodi.

    -   [Definire i gestori di movimento tramite MEF](#MEF). Usare questo metodo se si vuole che gli sviluppatori di terze parti possano definire i propri gestori per il linguaggio DSL. Gli utenti possono scegliere di installare le estensioni di terze parti dopo aver installato il linguaggio DSL.

-   [Come decodificare l'elemento trascinato](#extracting). Gli elementi possono essere trascinati da una finestra o dal desktop, oltre che da un linguaggio DSL.

-   [Come ottenere originale trascinata l'elemento](#getOriginal). Se l'elemento trascinato è un elemento DSL, è possibile aprire il modello di origine e accedere all'elemento.

-   [Utilizzo di azioni del Mouse: Il trascinamento degli elementi di raggruppamento](#mouseActions). Questo esempio viene illustrato un gestore di livello inferiore che intercetta le azioni del mouse sui campi di una forma. L'esempio consente all'utente di riordinare gli elementi in un raggruppamento trascinando con il mouse.

##  <a name="overrideShapeElement"></a> Definire i gestori di movimento eseguendo l'override di metodi ShapeElement
 Aggiungere un nuovo file di codice al progetto DSL. Per un gestore movimenti, in genere è necessario avere almeno le istruzioni `using` seguenti:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Linq;
```

 Nel nuovo file definire una classe parziale per la forma o la classe del diagramma che deve rispondere all'operazione di trascinamento. Eseguire l'override dei metodi seguenti:

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragOver%2A> - Questo metodo viene chiamato quando il puntatore del mouse viene immesso nella forma durante un'operazione di trascinamento. Il metodo deve esaminare l'elemento che l'utente sta trascinando e impostare la proprietà Effect per indicare se l'utente può rilasciare l'elemento su questa forma. La proprietà Effect determina l'aspetto del cursore mentre è sopra la forma e determina anche se verrà chiamato `OnDragDrop()` quando l'utente rilascerà il pulsante del mouse.

    ```csharp
    partial class MyShape // MyShape generated from DSL Definition.
    {
        public override void OnDragOver(DiagramDragEventArgs e)
        {
          base.OnDragOver(e);
          if (e.Effect == System.Windows.Forms.DragDropEffects.None
               && IsAcceptableDropItem(e)) // To be defined
          {
            e.Effect = System.Windows.Forms.DragDropEffects.Copy;
          }
        }

    ```

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragDrop%2A> -Questo metodo viene chiamato se l'utente rilascia il pulsante del mouse mentre il puntatore del mouse si sofferma su questa forma o diagramma, se `OnDragOver(DiagramDragEventArgs e)` precedentemente impostato `e.Effect` su un valore diverso da `None`.

    ```csharp
    public override void OnDragDrop(DiagramDragEventArgs e)
        {
          if (!IsAcceptableDropItem(e))
          {
            base.OnDragDrop(e);
          }
          else
          { // Process the dragged item, for example merging a copy into the diagram
            ProcessDragDropItem(e); // To be defined
          }
        }

    ```

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDoubleClick%2A> -Questo metodo viene chiamato quando l'utente fa doppio clic forma o diagramma.

     Per ulteriori informazioni, vedere [procedura: intercettare un clic su una forma o un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

 Definire `IsAcceptableDropItem(e)` per determinare se l'elemento trascinato sia accettabile e ProcessDragDropItem(e) per aggiornare il modello quando l'elemento viene rilasciato. Questi metodi devono prima estrarre l'elemento dagli argomenti dell'evento. Per informazioni su come eseguire questa operazione, vedere [come ottenere un riferimento all'elemento trascinato](#extracting).

##  <a name="MEF"></a> Definire i gestori di movimento tramite MEF
 MEF (Managed Extensibility Framework) consente di definire i componenti che possono essere installati con la configurazione minima. Per altre informazioni, vedere [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

#### <a name="to-define-a-mef-gesture-handler"></a>Per definire un gestore movimenti MEF

1.  Aggiungere il **Dsl** e **DslPackage** progetti il **MefExtension** file descritti in [estendere il modello DSL tramite MEF](../modeling/extend-your-dsl-by-using-mef.md).

2.  Ora è possibile definire un gestore movimenti come componente MEF:

    ```

    // This attribute is defined in the generated file
    // DslPackage\MefExtension\DesignerExtensionMetaDataAttribute.cs:
    [MyDslGestureExtension]
    public class MyGestureHandlerClassName : IGestureExtension
    {
      /// <summary>
      /// Called to determine whether a drag onto the diagram can be accepted.
      /// </summary>
      /// <param name="diagramDragEventArgs">Contains a link to the item that is being dragged</param>
      /// <param name="targetMergeElement">The shape or connector that the mouse is over</param>
      /// <returns>True if the item can be accepted on the targetMergeElement.</returns>
      public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null) return false;
        if (target.IsAcceptableDropItem(diagramDragEventArgs)) return true;
        return false;
      }
      public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null || ! target.IsAcceptableDropItem(diagramDragEventArgs)) return;
        // Process the dragged item, for example merging a copy into the diagram:
        target.ProcessDragDropItem(diagramDragEventArgs);
     }

    ```

     È possibile creare più di un componente gestore movimenti, ad esempio quando si hanno tipi diversi di oggetti trascinati.

3.  Aggiungere le definizioni di classe parziale per le classi forma, connettore o diagramma di destinazione e definire i metodi `IsAcceptableDropItem()` e `ProcessDragDropItem()`. Questi metodi devono iniziare estraendo gli elementi trascinati dagli argomenti dell'evento. Per ulteriori informazioni, vedere [come ottenere un riferimento all'elemento trascinato](#extracting).

##  <a name="extracting"></a> Come decodificare l'elemento trascinato
 Quando l'utente trascina un elemento sul diagramma o da una parte del diagramma a un'altra, le informazioni sull'elemento trascinato sono disponibili in `DiagramDragEventArgs`. I dati possono essere disponibili in svariati formati, perché l'operazione di trascinamento potrebbe essere stata iniziata da qualsiasi oggetto. Il codice deve riconoscere i formati che riesce a gestire.

 Per individuare i formati in cui sono disponibili le informazioni sull'origine del trascinamento, eseguire il codice in modalità di debug, impostando un punto di interruzione all'inizio su `OnDragOver()` o `CanDragDrop()`. Esaminare i valori del parametro `DiagramDragEventArgs`. Le informazioni sono disponibili in due formati:

-   <xref:System.Windows.Forms.IDataObject>  `Data` -Questa proprietà esegue serializzatore versioni degli oggetti di origine, in genere in più formati. Le funzioni più utili sono:

    -   diagramEventArgs.Data.GetDataFormats() - Elenca i formati in cui è possibile decodificare l'oggetto trascinato. Se, ad esempio, l'utente trascina un file dal desktop, i formati disponibili includono il nome file ("`FileNameW`").

    -   `diagramEventArgs.Data.GetData(format)` -Decodifica l'oggetto trascinato nel formato specificato. Eseguire il cast dell'oggetto al tipo appropriato. Ad esempio:

         `string fileName = diagramEventArgs.Data.GetData("FileNameW") as string;`

         È anche possibile trasmettere oggetti, quali i riferimenti ModelBus, dall'origine nel formato personalizzato. Per ulteriori informazioni, vedere [come inviare modello Bus riferimenti in un'operazione di trascinamento](#mbr).

-   <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> `Prototype` -Utilizzare questa proprietà se si desidera che gli utenti di trascinare elementi da un modello UML o un linguaggio DSL. Un prototipo di gruppo di elementi contiene uno o più oggetti, collegamenti e i valori delle proprietà. Viene usato anche nelle operazioni Incolla e quando si aggiunge un elemento dalla casella degli strumenti. In un prototipo, gli oggetti e i tipi vengono identificati dal GUID. Ad esempio, questo codice consente all'utente di trascinare gli elementi della classe da un diagramma UML o da Esplora modelli UML:

    ```csharp
    private bool IsAcceptableDropItem(DiagramDragEventArgs e)
    {
      return e.Prototype != null && e.Prototype.RootProtoElements.Any(element =>
            element.DomainClassId.ToString()
            == "3866d10c-cc4e-438b-b46f-bb24380e1678"); // Accept UML class shapes.
     // Or, from another DSL: SourceNamespace.SourceShapeClass.DomainClassId
    }

    ```

     Per accettare le forme UML, determinare i GUID delle classi di forme UML facendo delle prove. Tenere presente che in genere in ogni diagramma ci sono più tipi di elemento. Tenere anche presente che un oggetto trascinato da un diagramma DSL o UML è la forma, non l'elemento del modello.

 `DiagramDragEventArgs` ha anche proprietà che indicano la posizione corrente del puntatore del mouse e se l'utente sta premendo CTRL, ALT o MAIUSC.

##  <a name="getOriginal"></a> Come ottenere originale di un elemento trascinato
 Le proprietà `Data` e `Prototype` degli argomenti dell'evento contengono solo un riferimento alla forma trascinata. In genere, se si vuole creare nel linguaggio DSL di destinazione un oggetto derivato in qualche modo dal prototipo, è necessario ottenere l'accesso all'originale, ad esempio, leggendo i contenuti del file o passando all'elemento del modello rappresentato da una forma.  A questo scopo è possibile usare ModelBus di Visual Studio.

### <a name="to-prepare-a-dsl-project-for-model-bus"></a>Per preparare un progetto DSL per ModelBus

1.  Rendere il linguaggio DSL di origine accessibile da ModelBus di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:

    1.  Scaricare e installare l'estensione di ModelBus di Visual Studio, se non è già installata. Per ulteriori informazioni, vedere [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).

    2.  Aprire il file di definizione DSL del linguaggio DSL di origine in Progettazione DSL. Fare doppio clic nell'area di progettazione e quindi fare clic su **abilitare Modelbus**. Nella finestra di dialogo scegliere una o entrambe le opzioni.  Fare clic su **OK**. Un nuovo progetto "ModelBus" viene aggiunto alla soluzione DSL.

    3.  Fare clic su **Trasforma tutti i modelli** e ricompilare la soluzione.

###  <a name="mbr"></a> Per inviare un oggetto da un'origine DSL

1.  Nella sottoclasse ElementOperations eseguire l'override di `Copy()` in modo che codifichi un riferimento ModelBus (MBR, Model Bus Reference) in IDataObject. Questo metodo verrà chiamato quando l'utente inizierà a trascinare dal diagramma di origine. Il riferimento MBR codificato sarà quindi disponibile in IDataObject quando l'utente rilascerà nel diagramma di destinazione.

    ```

    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Shell;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Integration;
    using Microsoft.VisualStudio.Modeling.Integration.Shell;
    using System.Drawing; // PointF
    using  System.Collections.Generic; // ICollection
    using System.Windows.Forms; // for IDataObject
    ...
    public class MyElementOperations : DesignSurfaceElementOperations
    {
        public override void Copy(System.Windows.Forms.IDataObject data, System.Collections.Generic.ICollection<ModelElement> elements, ClosureType closureType, System.Drawing.PointF sourcePosition)
        {
          base.Copy(data, elements, closureType, sourcePosition);

          // Get the ModelBus service:
          IModelBus modelBus =
              this.Store.GetService(typeof(SModelBus)) as IModelBus;
          DocData docData = ((VSDiagramView)this.Diagram.ActiveDiagramView).DocData;
          string modelFile = docData.FileName;
          // Get an adapterManager for the target DSL:
          ModelBusAdapterManager manager =
              (modelBus.FindAdapterManagers(modelFile).First());
          ModelBusReference modelReference = manager.CreateReference(modelFile);
          ModelBusReference elementReference = null;
          using (ModelBusAdapter adapter = modelBus.CreateAdapter(modelReference))
          {
            elementReference = adapter.GetElementReference(elements.First());
          }

          data.SetData("ModelBusReference", elementReference);
        }
    ...}

    ```

### <a name="to-receive-a-model-bus-reference-from-a-dsl-in-a-target-dsl-or-uml-project"></a>Per ricevere un riferimento ModelBus da un linguaggio DSL in un progetto DSL o UML di destinazione

1.  Nel progetto DSL di destinazione aggiungere i riferimenti al progetto a:

    -   Progetto Dsl di origine.

    -   Progetto ModelBus di origine.

2.  Nel file di codice del gestore movimenti aggiungere i riferimenti allo spazio dei nomi seguenti:

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Integration;
    using SourceDslNamespace;
    using SourceDslNamespace.ModelBusAdapters;

    ```

3.  L'esempio seguente illustra come ottenere l'accesso all'elemento del modello di origine:

    ```
    partial class MyTargetShape // or diagram or connector
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
        // Verify that we're being passed an Object Shape.
        ElementGroupPrototype prototype = diagramDragEventArgs.Prototype;
        if (prototype == null) return;
        if (Company.InstanceDiagrams.ObjectShape.DomainClassId
          != prototype.RootProtoElements.First().DomainClassId)
          return;
        // - This is an ObjectShape.
        // - We need to access the originating Store, find the shape, and get its object.

        IModelBus modelBus = targetDropElement.Store.GetService(typeof(SModelBus)) as IModelBus;

        // Unpack the MBR that was packed in Copy:
        ModelBusReference reference = diagramDragEventArgs.Data.GetData("ModelBusReference") as ModelBusReference;
        using (SourceDslAdapter adapter = modelBus.CreateAdapter(reference) as SourceDslAdapter)
        {
          using (ILinkedUndoTransaction t = LinkedUndoContext.BeginTransaction("doing things"))
          {
            // Quickest way to get the shape from the MBR:
            ObjectShape firstShape = adapter.ResolveElementReference<ObjectShape>(reference);

            // But actually there might be several shapes - so get them from the prototype instead:
            IElementDirectory remoteDirectory = adapter.Store.ElementDirectory;
            foreach (Guid shapeGuid in prototype.SourceRootElementIds)
            {
              PresentationElement pe = remoteDirectory.FindElement(shapeGuid) as PresentationElement;
              if (pe == null) continue;
              SourceElement instance = pe.ModelElement as SourceElement;
              if (instance == null) continue;

              // Do something with the object:
          instance...
            }
            t.Commit();
          }
        }
    }

    ```

### <a name="to-accept-an-element-sourced-from-a-uml-model"></a>Per accettare un elemento originato da un modello UML

-   L'esempio di codice seguente accetta un oggetto rilasciato da un diagramma UML.

    ```csharp

      using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
      using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
      using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
      using Microsoft.VisualStudio.Modeling;
      using Microsoft.VisualStudio.Modeling.Diagrams;
      using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
      using Microsoft.VisualStudio.Uml.Classes;
      using System;
      using System.ComponentModel.Composition;
      using System.Linq;
    ...
    partial class TargetShape
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
            EnvDTE.DTE dte = this.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
            // Find the UML project
            foreach (EnvDTE.Project project in dte.Solution.Projects)
            {
              IModelingProject modelingProject = project as IModelingProject;
              if (modelingProject == null) continue; // not a modeling project
              IModelStore store = modelingProject.Store;
              if (store == null) return;

              foreach (IDiagram dd in store.Diagrams())
              {
                  // Get Modeling.Diagram that implements UML.IDiagram:
                  Diagram diagram = dd.GetObject<Diagram>();

                  foreach (Guid elementId in e.Prototype.SourceRootElementIds)
                  {
                    ShapeElement shape = diagram.Partition.ElementDirectory.FindElement(elementId) as ShapeElement;
                    if (shape == null) continue;
                    // This example assumes the shape is a UML class:
                    IClass classElement = shape.ModelElement as IClass;
                    if (classElement == null) continue;

                    // Now do something with the UML class element ...
                  }
            }
          break; // don't try any more projects
    }  }  }

    ```

##  <a name="mouseActions"></a> Utilizzo di azioni del Mouse: Il trascinamento degli elementi di raggruppamento
 È possibile scrivere un gestore che intercetta le azioni del mouse sui campi di una forma. L'esempio seguente consente all'utente di riordinare gli elementi in un raggruppamento trascinando con il mouse.

 Per compilare questo esempio, creare una soluzione utilizzando la **diagrammi classi** modello di soluzione. Aggiungere un file di codice e aggiungere il codice seguente. Modificare lo spazio dei nomi in modo che sia uguale al proprio.

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
// This code assumes that the embedding relationships displayed in the compartments
// don't use inheritance (don't have base or derived domain relationships).

namespace Company.CompartmentDrag  // EDIT.
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
  /// click somewhere else in the source shape. Yuk.
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
   dragStartElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item, but still inside the compartment,
  /// create an Action to supervise the cursor and handle subsequent mouse events.
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

- [Personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md)
- [Distribuzione di soluzioni per un linguaggio specifico di dominio](../modeling/deploying-domain-specific-language-solutions.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]