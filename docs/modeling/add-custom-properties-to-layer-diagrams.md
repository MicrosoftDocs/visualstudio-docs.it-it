---
title: Aggiungere proprietà personalizzate ai diagrammi delle dipendenze
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76bfa81f1285dce000f79c356a604bab1d53cc55
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2019
ms.locfileid: "58415824"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Aggiungere proprietà personalizzate ai diagrammi delle dipendenze

Quando si scrive codice delle estensioni per diagrammi delle dipendenze, è possibile archiviare i valori con qualsiasi elemento in un diagramma di dipendenza. I valori saranno permanenti quando il diagramma viene salvato e riaperto. È inoltre possibile impostare queste proprietà vengono visualizzate nel **proprietà** finestra in modo che gli utenti possono vedere e modificarli. Ad esempio, è possibile consentire agli utenti di specificare un'espressione regolare per ogni livello e scrivere il codice di convalida per verificare che i nomi delle classi in ogni livello siano conformi al modello specificato dall'utente.

## <a name="non-visible-properties"></a>Proprietà non visibili

Se si desidera semplicemente il codice associ i valori a qualsiasi elemento in un diagramma delle dipendenze, non devi definire un componente MEF. Esiste un dizionario denominato `Properties` in <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>. Aggiungere semplicemente i valori marshalable al dizionario di qualsiasi elemento del livello. Verranno salvate come parte del diagramma delle dipendenze.

## <a name="editable-properties"></a>Proprietà modificabili

**Preparazione iniziale**

> [!IMPORTANT]
> Per visualizzare le proprietà, apportare le modifiche seguenti in ogni computer in cui si desidera visualizzare le proprietà del livello:
>
> 1. Eseguire blocco note scegliendo **Esegui come amministratore**. Aprire *%ProgramFiles%\Microsoft Visual Studio [versione] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest*.
> 2. All'interno di **contenuto** elemento, aggiungere:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
> 3. Sotto il **strumenti di Visual Studio** sezione del menu start dell'applicazione di Visual Studio, aprire **prompt dei comandi sviluppatore**. Immettere:
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Riavviare Visual Studio.

**Assicurarsi che il codice è in un progetto VSIX**

Se la proprietà fa parte di un progetto di convalida, un movimento o un comando, non occorre aggiungere alcuna operazione. Il codice per la proprietà personalizzata deve essere specificato in un progetto Extensibility di Visual Studio definito come componente MEF. Per altre informazioni, vedere [aggiungere comandi e movimenti ai diagrammi delle dipendenze](../modeling/add-commands-and-gestures-to-layer-diagrams.md) oppure [aggiungere la convalida architettura personalizzati a diagrammi delle dipendenze](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

**Definire la proprietà personalizzata**

Per creare una proprietà personalizzata, definire una classe come quella seguente:

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

È possibile definire le proprietà in <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> o nelle relative classi derivate che includono:

-   `ILayerModel` - il modello

-   `ILayer` - ciascun livello

-   `ILayerDependencyLink` - i collegamenti tra i livelli

-   `ILayerComment`

-   `ILayerCommentLink`

## <a name="example"></a>Esempio

Il codice seguente è un descrittore di proprietà personalizzate tipico. Definisce una proprietà booleana nel modello di livello (`ILayerModel`) che consente all'utente di specificare i valori per un metodo di convalida personalizzata.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;

namespace MyNamespace
{
  /// <summary>
  /// Custom properties are added to the Layer Designer via a custom
  /// Property Descriptor. We have to export this Property Descriptor
  /// using MEF to make it available in the Layer Designer.
  /// </summary>
  [Export(typeof(IPropertyExtension))]
  public class AllTypesMustBeReferencedProperty
      : PropertyExtension<ILayerModel>
  {
    /// <summary>
    /// Each custom property must have a unique name.
    /// Usually we use the full name of this class.
    /// </summary>
    public static readonly string FullName =
      typeof(AllTypesMustBeReferencedProperty).FullName;

    /// <summary>
    /// Construct the property. Notice the use of FullName.
    /// </summary>
    public AllTypesMustBeReferencedProperty()
            : base(FullName)
    {  }

    /// <summary>
    /// The display name is shown in the Properties window.
    /// We therefore use a localizable resource.
    /// </summary>
    public override string DisplayName
    {
      get { return Strings.AllTypesMustBeReferencedDisplayName; }
    }

    /// <summary>
    /// Description shown at the bottom of the Properties window.
    /// We use a resource string for easier localization.
    /// </summary>
    public override string Description
    {
      get { return Strings.AllTypesMustBeReferencedDescription; }
    }

    /// <summary>
    /// This is called to set a new value for this property. We must
    /// throw an exception if the value is invalid.
    /// </summary>
    /// <param name="component">The target ILayerElement</param>
    /// <param name="value">The new value</param>
    public override void SetValue(object component, object value)
    {
      ValidateValue(value);
      base.SetValue(component, value);
    }
    /// <summary>
    /// Helper to validate the value.
    /// </summary>
    /// <param name="value">The value to validate</param>
    private static void ValidateValue(object value)
    {  }

    public override Type PropertyType
    { get { return typeof(bool); } }

    /// <summary>
    /// The segment label of the properties window.
    /// </summary>
    public override string Category
    {
      get
      {
        return Strings.AllTypesMustBeReferencedCategory;
      }
    }
  }
}
```

## <a name="see-also"></a>Vedere anche

- [Estendere i diagrammi delle dipendenze](../modeling/extend-layer-diagrams.md)
