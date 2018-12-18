---
title: Personalizzazione di strumenti elemento
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 566558390e29f9198b2328463dfce26327f76565
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="customizing-element-tools"></a>Personalizzazione di strumenti elemento
In alcune definizioni DSL, un singolo concetto è rappresentare come un gruppo di elementi. Ad esempio, se si crea un modello in cui un componente dispone di un set fisso di porte, è necessario sempre le porte da creare contemporaneamente il proprio componente padre. Pertanto, è necessario personalizzare lo strumento di creazione di elemento in modo che crei un gruppo di elementi invece di uno solo. A tale scopo, è possibile personalizzare il tipo di inizializzazione lo strumento di creazione di elemento.

 È inoltre possibile sostituire cosa accade quando lo strumento viene trascinato il diagramma o un elemento.

## <a name="customizing-the-content-of-an-element-tool"></a>La personalizzazione del contenuto di uno strumento dell'elemento
 Ogni strumento elemento archivia un'istanza di un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> EGP (), che contiene una versione serializzata di uno o più elementi del modello e i collegamenti. Per impostazione predefinita, EGP di uno strumento dell'elemento contiene un'istanza della classe specificato per lo strumento. È possibile modificare questa impostazione viene sottoposto a override *YourLanguage*`ToolboxHelper.CreateElementToolPrototype`. Questo metodo viene chiamato quando viene caricato il pacchetto DSL.

 Un parametro del metodo è l'ID della classe specificata nella definizione del linguaggio DSL. Quando viene chiamato il metodo con la classe che si è interessati, è possibile aggiungere elementi aggiuntivi nel EGP.

 Deve includere il EGP incorporamento collegamenti da un elemento principale per gli elementi di filiale. È inoltre possibile utilizzare i collegamenti di riferimento.

 L'esempio seguente crea un elemento principale e due elementi incorporati. La classe principale viene chiamata resistenza e dispone di due relazioni di incorporamento per gli elementi denominati Terminal. Proprietà del ruolo di incorporamento sono denominate Terminal1 e Terminal2 e prevedono una molteplicità di 1..1.

```
using Microsoft.VisualStudio.Modeling; ...
public partial class CircuitDiagramToolboxHelper
{
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)
  {
    // A case for each tool to customize:
    if (domainClassId == Resistor.DomainClassId)
    {
      // Set up the prototype elements and links:
      Resistor resistor = new Resistor(store);
      resistor.Terminal1 = new Terminal(store);
      resistor.Terminal2 = new Terminal(store);
      resistor.Terminal1.Name = "T1"; // embedding
      resistor.Terminal2.Name = "T2"; // embedding
      // We could also set up reference links.

      // Create an element group prototype for the toolbox:
      ElementGroup egp = new ElementGroup(store.DefaultPartition);
      egp.AddGraph(resistor, true);
      // We do not have to explicitly include embedded children.
      return egp.CreatePrototype();
    }
    // Element tools for other classes:
    else
      return base.CreateElementToolPrototype(store, domainClassId);
  }
}
```

## <a name="see-also"></a>Vedere anche

- [Personalizzazione della creazione e dello spostamento di elementi](../modeling/customizing-element-creation-and-movement.md)