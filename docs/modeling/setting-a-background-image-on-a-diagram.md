---
title: Impostazione di un'immagine di sfondo in un diagramma
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: b133428162b0f07a70f30da80e36537a2242d744
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="setting-a-background-image-on-a-diagram"></a>Impostazione di un'immagine di sfondo in un diagramma
In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK è possibile impostare l'immagine di sfondo per una finestra di progettazione generata tramite codice personalizzato.

## <a name="setting-the-background-image"></a>Impostazione dell'immagine di sfondo

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Per impostare un'immagine di sfondo per una finestra di progettazione generata

1.  Copiare il file di immagine da usare come sfondo per il diagramma nella directory Dsl\Resources del progetto corrente.

2.  In **Esplora**, la cartella Dsl\Resources destro, scegliere **Aggiungi**, quindi fare clic su **elemento esistente**.

3.  Nel **Aggiungi elemento esistente** la finestra di dialogo, passare alla cartella Dsl\Resources.

4.  Nel **i file di tipo** elenco, fare clic su **i file di immagine**.

5.  Fare clic sul file di immagine che è stato copiato nella directory e quindi fare clic su **Aggiungi**.

6.  Fare doppio clic su Dsl e fare clic su **proprietà** per aprire le proprietà del progetto Dsl.

7.  Nel **risorse** scheda, fare clic su **questo progetto non contiene un file di risorse predefinito. Fare clic qui per crearne uno.**

8.  Aggiungere il file di immagine al file di risorse, trascinare l'immagine di **Esplora** nella finestra di risorse.

9. Aprire il menu File e fare clic sull'opzione per salvare le proprietà del progetto.

10. Verificare che il file Dsl\Properties\Resources.resx sia presente e contenga il file Resources.Designer.cs.

11. Se manca Resources.Designer.cs, fare clic sul file resx in **Esplora**.

12. Nel **proprietà** finestra, impostare il `Custom Tool` proprietà `ResXFileCodeGenerator`.

13. In **Esplora**, fare clic sul progetto Dsl, scegliere **Aggiungi**, fare clic su **nuova cartella**.

14. Denominare la cartella **personalizzato**.

15. Pulsante destro del mouse sulla cartella personalizzata, scegliere **Aggiungi**, fare clic su **nuovo elemento**.

16. Nel **Aggiungi nuovo elemento** della finestra di dialogo di **modelli** elenco, fare clic su **File di codice**.

17. Nel **nome** digitare `BackgroundImage.cs`, fare clic su **Aggiungi**.

18. Copiare il codice seguente nel file BackgroundImage.cs, usando lo spazio dei nomi, il nome della classe del diagramma e il nome della risorsa del file di immagine corretti.

     Sostituire "MyDiagramClass" con il nome della classe parziale del diagramma definita in Dsl\GeneratedCode\Diagrams.cs. È anche possibile recuperare lo spazio dei nomi corretto dal file Dsl\GeneratedCode\Diagrams.cs.

    ```
    using System;
    using Microsoft.VisualStudio.Modeling.Diagrams;

    // Fix the namespace:
    namespace Fabrikam.MyLanguage
    {
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs

      public partial class Language29Diagram
      {
        protected override void InitializeInstanceResources()
        {
          // Fix the Resources namespace and the Image resource name:
          ImageField backgroundField = new ImageField("background",
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);

          backgroundField.DefaultFocusable = false;
          backgroundField.DefaultSelectable = false;
          backgroundField.DefaultVisibility = true;
          backgroundField.DefaultUnscaled = false;

          shapeFields.Add(backgroundField);

          backgroundField.AnchoringBehavior
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);
          backgroundField.AnchoringBehavior
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);
          backgroundField.AnchoringBehavior
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);
          backgroundField.AnchoringBehavior
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);

          base.InitializeInstanceResources();
        }
      }
    }
    ```

     Per ulteriori informazioni sulla personalizzazione del modello con il codice del programma, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Vedere anche

- [Definizione di forme e connettori](../modeling/defining-shapes-and-connectors.md)
- [Personalizzazione dei campi testo e immagine](../modeling/customizing-text-and-image-fields.md)
- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
