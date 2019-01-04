---
title: 'Procedura: Accedere e vincolare la selezione corrente'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 799e6fdc50cad91ebd5ee5081b1d80fa296f5a7c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947947"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Procedura: Accedere e vincolare la selezione corrente

Quando si scrive un gestore comandi o movimenti per il linguaggio specifico di dominio, è possibile determinare l'elemento che l'utente selezionata. È possibile anche impedire alcune forme o i campi selezionati. Ad esempio, è possibile disporre che, quando l'utente fa clic su un elemento decorator di icona, viene selezionata invece la forma che lo contiene. Vincolare la selezione in questo modo riduce il numero dei gestori che è necessario scrivere. Inoltre rende più semplice per l'utente, che è possibile fare clic su un punto qualsiasi nella forma senza la necessità di evitare l'elemento decorator.

## <a name="access-the-current-selection-from-a-command-handler"></a>Accedere alla selezione corrente da un gestore comando

La classe di set di comandi per un linguaggio specifico di dominio contiene i gestori di comando per i comandi personalizzati. Il <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> (classe), da cui deriva la classe di set di comandi per un linguaggio specifico di dominio, fornisce alcuni membri per l'accesso alla selezione corrente.

A seconda del comando, il gestore del comando potrebbe essere necessario la selezione in Progettazione modelli, Esplora modelli o la finestra attiva.

### <a name="to-access-selection-information"></a>Per accedere alle informazioni di selezione

1.  Il <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe definisce i membri seguenti che possono essere utilizzati per accedere alla selezione corrente.

    |Member|Descrizione|
    |-|-|
    |Metodo <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Restituisce `true` se uno degli elementi selezionati nella finestra di progettazione del modello è una forma di raggruppamento; in caso contrario, `false`.|
    |Metodo <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Restituisce `true` se il diagramma è selezionato nella finestra di progettazione del modello; in caso contrario, `false`.|
    |Metodo <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Restituisce `true` se esattamente un elemento è selezionato nella finestra di progettazione del modello; in caso contrario, `false`.|
    |Metodo <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Restituisce `true` se esattamente un elemento è selezionato nella finestra attiva; in caso contrario, `false`.|
    |Proprietà <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A>|Ottiene una raccolta di sola lettura degli elementi selezionati in Progettazione modelli.|
    |Proprietà <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A>|Ottiene una raccolta di sola lettura degli elementi selezionati nella finestra attiva.|
    |Proprietà <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A>|Ottiene l'elemento principale della selezione in Progettazione modelli.|
    |Proprietà <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A>|Ottiene l'elemento principale della selezione nella finestra attiva.|

2.  Il <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> proprietà del <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe fornisce l'accesso per il <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> oggetto che rappresenta la finestra di progettazione modelli e fornisce accesso aggiuntivo gli elementi selezionati in Progettazione modelli.

3.  Inoltre, il codice generato definisce una proprietà della finestra degli strumenti Esplora e una proprietà di selezione di Esplora risorse nel comando set (classe) per il linguaggio specifico di dominio.

    -   La proprietà della finestra degli strumenti Esplora restituisce un'istanza della classe della finestra dello strumento explorer per il linguaggio specifico di dominio. La classe della finestra degli strumenti Esplora deriva dal <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> classe e rappresenta Esplora modelli per il linguaggio specifico di dominio.

    -   Il `ExplorerSelection` proprietà restituisce l'elemento selezionato nella finestra Esplora modelli per il linguaggio specifico di dominio.

## <a name="determine-which-window-is-active"></a>Determinare quale finestra è attiva

Il <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> contiene interfaccia definisce i membri che forniscono l'accesso allo stato di selezione corrente nella shell. È possibile ottenere un' <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> oggetto di classe del pacchetto o la classe di set di comandi per il linguaggio specifico di dominio tramite il `MonitorSelection` definita nella classe di base di ogni proprietà. La classe del pacchetto deriva dal <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> classe e la classe di set di comandi deriva dal <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe.

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Per determinare da un gestore del comando il tipo di finestra è attivo

1.  Il <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> proprietà del <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe restituisce un <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> oggetto che fornisce accesso allo stato di selezione corrente nella shell.

2.  Il <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> proprietà del <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> interface Ottiene il contenitore di selezione attiva, che può essere diverso dalla finestra attiva.

3.  Aggiungere che le proprietà seguenti al comando impostato classe automaticamente linguaggio specifico di dominio per determinare il tipo di finestra è attivo.

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constrain-the-selection"></a>Vincolare la selezione

Quando si aggiungono regole di selezione, è possibile controllare quali elementi sono selezionati quando l'utente seleziona un elemento del modello. Ad esempio, per consentire all'utente di considerare un numero di elementi come una singola unità, è possibile usare una regola di selezione.

### <a name="to-create-a-selection-rule"></a>Per creare una regola di selezione

1.  Creare un file di codice personalizzato nel progetto DSL

2.  Definire una classe di regola di selezione che è derivata dal <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> classe.

3.  Eseguire l'override di <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> metodo della classe di regola di selezione per applicare i criteri di selezione.

4.  Aggiungere una definizione di classe parziale per la classe ClassDiagram al file di codice personalizzato.

     Il `ClassDiagram` deriva dalla classe di <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> classe e viene definito nel file di codice generato, Diagram.cs, nel progetto DSL.

5.  Eseguire l'override di <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> proprietà del `ClassDiagram` classe per restituire la regola di selezione personalizzata.

     L'implementazione predefinita del <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> proprietà ottiene un oggetto regola di selezione che non modificano la selezione.

### <a name="example"></a>Esempio

Il file di codice seguente crea una regola di selezione che si espande la selezione per includere tutte le istanze di ogni forma dominio che è stato inizialmente selezionato.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>