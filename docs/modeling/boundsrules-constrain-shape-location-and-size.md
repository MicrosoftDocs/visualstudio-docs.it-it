---
title: Le regole associate (BoundsRules) vincolano posizione e dimensione delle forme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 69e189b8348b7c68c7a778f00975d5d1475223ab
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Le regole associate (BoundsRules) vincolano posizione e dimensione delle forme

Oggetto *limiti regola* è una classe che definisce i limiti alle dimensioni e posizione di una forma. Fornisce un metodo che viene chiamato ripetutamente quando un utente sta trascinando una forma o negli angoli o ai lati della forma.

Nell'esempio seguente viene vincola una forma rettangolare a una barra di dimensioni fisse, orizzontale o verticale. Quando l'utente trascina l'angoli o ai lati, la struttura consente di capovolgere tra le due configurazioni consentite dell'altezza e larghezza.

I limiti della regola è una classe derivata da <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Viene creata un'istanza della regola nella forma:

```csharp
using Microsoft.VisualStudio.Modeling.Diagrams; ...

public partial class BarShape
{
  /// <summary>
  /// Rule invoked when the user is resizing a shape.
  /// </summary>
  public override BoundsRules BoundsRules
  { get { return new BarBoundsRule(); } }
}

/// <summary>
/// Rule invoked when the user is changing a shape's outline.
/// Provides real-time mouse rubber-band feedback, so must work fast.
/// </summary>
public class BarBoundsRule: BoundsRules
{
  public override RectangleD GetCompliantBounds
     (ShapeElement shape, RectangleD proposedBounds)
  {
    double thickness = 0.1;
    if (proposedBounds.Height > proposedBounds.Width)
    {
      // There is a minimum width for a shape; the width
      // will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
            new SizeD(thickness, proposedBounds.Height));
    }
    else
    {
      // There is a minimum height for a shape; the
      // height will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
         new SizeD(proposedBounds.Width, thickness));
} } }
```

Si noti che può essere vincolati sia la posizione e dimensioni se si desidera.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>
- [Rispondere e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md)