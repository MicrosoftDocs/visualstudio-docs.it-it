---
title: Incorporamento di un diagramma in Windows Form
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 75e7c058d1cc852386e1df897127b96781b60c50
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Incorporamento di un diagramma in Windows Form
È possibile incorporare un diagramma DSL in un controllo Windows, che viene visualizzata nella [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] finestra.

## <a name="embedding-a-diagram"></a>Incorporamento di un diagramma

#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Per incorporare un diagramma DSL in un controllo di Windows

1.  Aggiungere un nuovo **controllo utente** file al progetto DslPackage.

2.  Aggiungere un controllo riquadro al controllo utente. Questo pannello conterrà il diagramma DSL.

     Aggiungere altri controlli necessari.

     Impostare le proprietà di ancoraggio dei controlli.

3.  In Esplora soluzioni fare doppio clic su file di controllo utente e fare clic su **Visualizza codice**. Aggiungere il codice di questo costruttore e una variabile:

    ```csharp

    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;

    ```

4.  Aggiungere un nuovo file al progetto DslPackage, con il seguente contenuto:

    ```
    using System.Windows.Forms;
    namespace Company.MyDSL
    {
      partial class MyDSLDocView
      {
        private UserControl1 container;
        public override IWin32Window Window
        {
          get
          {
            if (container == null)
            {
              // Put our own form inside the DSL window:
              container = new UserControl1(this,
                (Control)base.Window);
            }
            return container;
    } } } }

    ```

5.  Per eseguire il test del linguaggio DSL, premere F5 e aprire un file di modello di esempio. Il diagramma verrà visualizzato all'interno del controllo. Casella degli strumenti e altre funzionalità funzionano normalmente.

#### <a name="updating-the-form-using-store-events"></a>L'aggiornamento al Form utilizzando gli eventi di archiviazione

1.  Nella finestra di progettazione di form, aggiungere un **ListBox** denominato `listBox1`. Questo verrà visualizzato un elenco degli elementi nel modello. Rimarrà in synchronism con il modello utilizzando *archiviare eventi*. Per ulteriori informazioni, vedere [gestori propagare le modifiche di fuori di modello di eventi](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2.  Nel file di codice personalizzato, eseguire l'override ulteriori metodi alla classe DocView:

    ```

    partial class MyDSLDocView
    {
     /// <summary>
     /// Register store event listeners.
     /// This method is called when the model and diagram
     /// have completed loading.
     /// </summary>
     protected override bool LoadView()
      {
        bool result = base.LoadView();
        Store store = this.DocData.Store;
        EventManagerDirectory emd = store.EventManagerDirectory;
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));

        // Do the initial parts list:
        container.SetUpFormFromModel();
        return result;
      }
     /// <summary>
     /// Listener method called on creation of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void AddElement(object sender, ElementAddedEventArgs e)
     {
       container.Add(e.ModelElement as ExampleElement);
     }
     /// <summary>
     /// Listener method called after deletion of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void RemoveElement(object sender, ElementDeletedEventArgs e)
     {
       container.Remove(e.ModelElement as ExampleElement);
     }

    ```

3.  Nel code-behind del controllo utente, inserire i metodi per l'ascolto degli elementi aggiunti e rimossi:

    ```

          public partial class UserControl1 : UserControl { ...

    private ExampleModel modelRoot;

    internal void Add(ExampleElement e) { UpdatePartsList(); }
    internal void Remove(ExampleElement e) { UpdatePartsList(); }

    internal void SetUpFormFromModel()
    {
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      UpdatePartsList();
    }

    private void UpdatePartsList()
    {
      StringBuilder builder = new StringBuilder();
      listBox1.Items.Clear();
      foreach (ExampleElement c in modelRoot.Elements)
      {
        listBox1.Items.Add(c.Name);
      }
    }

    ```

4.  Per eseguire il test del linguaggio DSL, premere F5 e nell'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], aprire un file di modello di esempio.

     Si noti che la casella di riepilogo Mostra un elenco degli elementi nel modello e che sia corretto dopo qualsiasi aggiunta o eliminazione e dopo l'annullamento e ripristino.

## <a name="see-also"></a>Vedere anche

- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
