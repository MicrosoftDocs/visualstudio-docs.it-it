---
title: Aggiungere proprietà personalizzate ai diagrammi di dipendenza
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 368d1a794f51d827aa62cc913039edda59ae7ae6
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Aggiungere proprietà personalizzate ai diagrammi di dipendenza

Quando si scrive codice di estensione per i diagrammi di dipendenza, è possibile archiviare i valori con qualsiasi elemento in un diagramma di dipendenza. I valori saranno permanenti quando il diagramma viene salvato e riaperto. È inoltre possibile impostare queste proprietà vengono visualizzate nel **proprietà** finestra in modo che gli utenti possono vedere e modificarli. Ad esempio, è possibile consentire agli utenti di specificare un'espressione regolare per ogni livello e scrivere il codice di convalida per verificare che i nomi delle classi in ogni livello siano conformi al modello specificato dall'utente.

## <a name="non-visible-properties"></a>Proprietà non visibili

Se si desidera solo il codice associ i valori a qualsiasi elemento in un diagramma di dipendenze, è necessario definire un componente MEF. Esiste un dizionario denominato `Properties` in <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>. Aggiungere semplicemente i valori marshalable al dizionario di qualsiasi elemento del livello. Verranno salvate come parte del diagramma di dipendenza. Per ulteriori informazioni, vedere [Naviga e aggiornare i modelli nel codice programma dei livelli](../modeling/navigate-and-update-layer-models-in-program-code.md).

## <a name="editable-properties"></a>Proprietà modificabili

**Preparazione iniziale**

> [!IMPORTANT]
> Per visualizzare le proprietà, apportare la modifica seguente in ogni computer in cui si desidera essere visibili le proprietà del livello:
>
> 1. Eseguire il blocco note con **Esegui come amministratore**. Aprire *%ProgramFiles%\Microsoft Visual Studio [versione] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest*.
> 2. All'interno di **contenuto** elemento, aggiungere:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
> 3. Sotto il **Visual Studio Tools** sezione del menu start applicazione di Visual Studio, aprire **prompt dei comandi per sviluppatori**. Immettere:
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Riavviare Visual Studio.

**Assicurarsi che il codice sia in un progetto VSIX**

Se la proprietà fa parte di un progetto di convalida, un movimento o un comando, è necessario aggiungere alcun valore. Il codice per la proprietà personalizzata deve essere specificato in un progetto Extensibility di Visual Studio definito come componente MEF. Per ulteriori informazioni, vedere [aggiungere comandi e movimenti a diagrammi di dipendenza](../modeling/add-commands-and-gestures-to-layer-diagrams.md) o [aggiunta di convalida dell'architettura personalizzati a diagrammi dipendenza](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

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
