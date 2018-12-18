---
title: Esplorare e aggiornare i modelli di livello nel codice del programma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 57ba3e2b2df938a41129fdf2d05bfa02690d2cce
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Esplorare e aggiornare i modelli di livello nel codice del programma

In questo articolo vengono descritti gli elementi e le relazioni nei modelli di livello, che è possibile esplorare e aggiornare utilizzando codice programma. Per ulteriori informazioni sui diagrammi dipendenza dal punto di vista dell'utente, vedere [diagrammi dipendenza: riferimento](../modeling/layer-diagrams-reference.md) e [diagrammi dipendenza: linee guida](../modeling/layer-diagrams-guidelines.md).

Il <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer> modello descritto in questo argomento è un aspetto di un più generale <xref:Microsoft.VisualStudio.GraphModel> modello. Se si sta scrivendo un [estensione comandi o movimenti menu](../modeling/add-commands-and-gestures-to-layer-diagrams.md), utilizzare il `Layer` modello. Se si sta scrivendo un [estensione di convalida dei livelli](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), risulta più semplice utilizzare il `GraphModel`.

## <a name="transactions"></a>Transazioni

Quando si aggiorna un modello, provare a includere le modifiche in un `ILinkedUndoTransaction`, che raggruppa le modifiche in un'unica transazione. Se le modifiche non riesce, viene eseguito il rollback dell'intera transazione. Se l'utente annulla una modifica, tutte le modifiche verranno annullate.

```
using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("a name"))
{
    // Make changes here ....
    t.Commit(); // Don't forget this!
}
```

## <a name="containment"></a>Contenuto

![ILayer e ILayerModel possono contenere entrambi oggetti ILayers.](../modeling/media/layerapi_containment.png)

I livelli (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) e il modello di livello (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) possono contenere commenti e livelli.

Un livello (`ILayer`) può essere contenuto in un modello di livello (`ILayerModel`) o annidato in un altro elemento `ILayer`.

Per creare un commento o un livello, usare i metodi di creazione sul contenitore appropriato.

## <a name="dependency-links"></a>Collegamenti di dipendenza

Un collegamento di dipendenza è rappresentato da un oggetto e può essere esplorato in entrambe le direzioni:

![Oggetto ILayerDependencyLink che connette due ILayers.](../modeling/media/layerapi_dependency.png)

Per creare un collegamento di dipendenza, chiamare `source.CreateDependencyLink(target)`.

## <a name="comments"></a>Commenti

I commenti possono essere contenuti in livelli o nel modello di livello e possono inoltre essere collegati a qualsiasi elemento livello:

![È possibile associare commenti a qualsiasi elemento del livello.](../modeling/media/layerapi_comments.png)

Un commento può essere collegato a qualsiasi numero di elementi o a nessun elemento.

Per ottenere i commenti collegati a un elemento livello, usare:

```csharp
ILayerModel model = diagram.GetLayerModel();
IEnumerable<ILayerComment> comments =
   model.Comments.Where(comment =>
      comment.Links.Any(link => link.Target == layerElement));
```

> [!CAUTION]
> La proprietà `Comments` di un elemento `ILayer` ottiene commenti contenuti nell'elemento `ILayer`. Non ottiene i commenti che sono collegati a esso.

Creare un commento chiamando `CreateComment()` sul contenitore appropriato.

Creare un collegamento usando `CreateLink()` sul commento.

## <a name="layer-elements"></a>Elementi di livello

Tutti i tipi di elemento che possono essere contenuti in un modello sono elementi di livello:

![i contenuti del diagramma dipendenza sono oggetti ILayerElements.](../modeling/media/layerapi_layerelements.png)

## <a name="properties"></a>Proprietà

Ogni `ILayerElement` ha un dizionario di stringhe denominato`Properties`. È possibile usare questo dizionario per collegare informazioni arbitrarie a qualsiasi elemento livello.

## <a name="artifact-references"></a>Riferimenti per elementi

Un riferimento per elementi (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) rappresenta il collegamento tra un livello e un elemento di progetto come un file, una classe o una cartella. L'utente crea gli elementi quando creare un livello o aggiungervi trascinando gli elementi da Esplora soluzioni, Visualizzazione classi o Visualizzatore oggetti in un diagramma di dipendenza. È possibile collegare qualsiasi numero di riferimenti per artefatti a un livello.

Ogni riga di Esplora livello visualizza un riferimento ad artefatti. Per ulteriori informazioni, vedere [creare diagrammi dipendenza dal codice](../modeling/create-layer-diagrams-from-your-code.md).

I tipi e i metodi principali interessati dai riferimenti ad artefatti sono i seguenti:

<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>. La proprietà Categorie indica il tipo di artefatto al quale viene fatto riferimento, ad esempio una classe, un file eseguibile o un assembly. La proprietà categorie determina la modalità di identificazione dell'elemento di destinazione da parte dell'identificatore.

<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> crea un riferimento a elementi da un <xref:EnvDTE.Project> o da un <xref:EnvDTE.ProjectItem>. Si tratta di un'operazione asincrona, Pertanto, in genere si fornisce un callback che viene chiamato quando viene completata la creazione.

I riferimenti a elementi di livello sono diverse per gli elementi in diagrammi caso d'uso.

## <a name="shapes-and-diagrams"></a>Forme e diagrammi

Per rappresentare ogni elemento di un modello di livello si usano due oggetti: un <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> e un <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>. L'oggetto `IShape` rappresenta la posizione e la dimensione della forma sul diagramma. Nei modelli di livello ogni `ILayerElement` presenta uno `IShape`e ogni `IShape` una dipendenza diagramma ha uno `ILayerElement`. `IShape` è usato anche per i modelli UML, quindi non tutti gli oggetti `IShape` hanno un elemento livello.

Analogamente, <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> è visualizzato in un <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>.

Nel codice di un gestore comandi o movimenti personalizzato, è possibile ottenere il diagramma corrente e la selezione corrente di forme dall'importazione `DiagramContext`:

```
public class ... {
[Import]
    public IDiagramContext DiagramContext { get; set; }
...
public void ... (...)
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;
  ILayerModel model = diagram.GetLayerModel();
  if (model != null)
  { foreach (ILayer layer in model.Layers) { ... }}
  foreach (IShape selected in diagram.SelectedShapes)
  { ILayerElement element = selected.GetLayerElement();
    if (element != null) ... }}
```

![Ogni oggetto ILayerElement è presentato da un oggetto IShape.](../modeling/media/layerapi_shapes.png)

<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> e <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> sono usati anche per visualizzare modelli UML.

## <a name="see-also"></a>Vedere anche

- [Aggiungere comandi e movimenti ai diagrammi delle dipendenze](../modeling/add-commands-and-gestures-to-layer-diagrams.md)
- [Aggiungere strumenti di convalida dell'architettura personalizzati ai diagrammi delle dipendenze](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
- [Aggiungere proprietà personalizzate ai diagrammi delle dipendenze](../modeling/add-custom-properties-to-layer-diagrams.md)
- [Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)
- [Diagrammi delle dipendenze: linee guida](../modeling/layer-diagrams-guidelines.md)
