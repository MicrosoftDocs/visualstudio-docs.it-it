---
title: Creazione di un linguaggio specifico di dominio di Windows basata su form | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7eb6bc6542350439250ace3dbaa7f2ba920e93ed
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>Creazione di un linguaggio specifico di dominio basato su Windows Form
È possibile utilizzare Windows Form per visualizzare lo stato di un modello di linguaggio specifico di dominio (DSL), anziché utilizzare un diagramma DSL. Questo argomento viene illustrata l'associazione di un Windows Form a un linguaggio DSL, usando il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK.  
  
 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  
Un'istanza DSL, che visualizza un'interfaccia utente di Windows Form ed Esplora modelli.  
  
## <a name="creating-a-windows-forms-dsl"></a>Creazione di un Windows Form DSL  
 Il **minima progettazione Windows Form** modello DSL consente di creare un linguaggio DSL minimo che è possibile modificare per adattarli ai propri requisiti.  
  
#### <a name="to-create-a-minimal-winforms-dsl"></a>Per creare un minimo di WinForms DSL  
  
1.  Creare un linguaggio DSL dal **minima progettazione Windows Form** modello.  
  
     In questa procedura dettagliata, si presuppone che i nomi seguenti:  
  
    |||  
    |-|-|  
    |Nome di soluzione e di DSL|FarmApp|  
    |Spazio dei nomi|Company.FarmApp|  
  
2.  Provare con l'esempio iniziale forniti dal modello:  
  
    1.  Trasforma tutti i modelli.  
  
    2.  Compilare ed eseguire l'esempio (**CTRL + F5**).  
  
    3.  Nell'istanza sperimentale di Visual Studio, aprire il `Sample` file nel progetto di debug.  
  
         Si noti che viene visualizzato in un controllo Windows Form.  
  
         È inoltre possibile visualizzare gli elementi del modello visualizzato in Esplora risorse.  
  
         Aggiungere alcuni elementi nel form o Esplora risorse e notare che vengono visualizzati nella visualizzazione altri.  
  
 Nell'istanza principale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], notare i punti seguenti circa la soluzione DSL:  
  
-   `DslDefinition.dsl`non contiene alcun elemento diagramma. Infatti, non si utilizzerà diagrammi DSL per visualizzare i modelli di istanza di questo linguaggio DSL. In alternativa, associare un Windows Form al modello e gli elementi nel form verranno visualizzato il modello.  
  
-   Oltre al `Dsl` e `DslPackage` progetti, la soluzione contiene un terzo progetto denominato `UI.` **dell'interfaccia utente** progetto contiene la definizione di un controllo Windows Form. `DslPackage`dipende `UI`, e `UI` dipende `Dsl`.  
  
-   Nel `DslPackage` progetto `UI\DocView.cs` contiene il codice che visualizza il controllo Windows Form che è definito nel `UI` progetto.  
  
-   Il `UI` progetto contiene un esempio reale di un controllo di modulo associato a del linguaggio DSL. Tuttavia, non funzionerà dopo avere modificato la definizione DSL. Il `UI` progetto contiene:  
  
    -   Una classe di Windows Form denominata `ModelViewControl`.  
  
    -   Un file denominato `DataBinding.cs` che contiene una definizione parziale aggiuntiva di `ModelViewControl`. Per visualizzare il contenuto, in **Esplora**, aprire il menu di scelta rapida per il file e scegliere **Visualizza codice**.  
  
### <a name="about-the-ui-project"></a>Sul progetto dell'interfaccia utente  
 Quando si aggiorna il file di definizione DSL per definire il proprio modello DSL, sarà necessario aggiornare il controllo di `UI` progetto per visualizzare il modello DSL. A differenza di `Dsl` e `DslPackage` progetti, il codice di esempio `UI` progetto non è stato generato da `DslDefinitionl.dsl`. È possibile aggiungere i file con estensione tt per generare il codice se si desidera, sebbene non compresi in questa procedura dettagliata.  
  
## <a name="updating-the-dsl-definition"></a>L'aggiornamento della definizione DSL  
 Le operazioni seguenti che in questa procedura dettagliata viene utilizzata la definizione di DSL.  
  
 ![DSL&#45;Wpf&#45;1](../modeling/media/dsl-wpf-1.png "DSL-Wpf-1")  
  
#### <a name="to-update-the-dsl-definition"></a>Per aggiornare la definizione DSL  
  
1.  Aprire DslDefinition.dsl nella finestra di progettazione DSL.  
  
2.  Eliminare **ExampleElement**  
  
3.  Rinominare il **ExampleModel** classe dominio `Farm`.  
  
     Assegnare le proprietà di dominio aggiuntivo denominate `Size` di tipo **Int32**, e `IsOrganic` di tipo **booleano**.  
  
    > [!NOTE]
    >  Se si elimina la classe di dominio radice e quindi creare una nuova radice, è necessario reimpostare la proprietà di classe principale dell'Editor. In **Esplora DSL**selezionare **Editor**. Nella finestra Proprietà impostare **classe radice** a `Farm`.  
  
4.  Utilizzare il **la classe di dominio denominato** strumento per creare le classi di dominio seguenti:  
  
    -   `Field`-Fornire questo una proprietà di dominio aggiuntivo denominata `Size`.  
  
    -   `Animal`-Nella finestra Proprietà impostare **modificatore di ereditarietà** a **astratta**.  
  
5.  Utilizzare il **classe dominio** strumento per creare le classi seguenti:  
  
    -   `Sheep`  
  
    -   `Goat`  
  
6.  Utilizzare il **ereditarietà** strumento per rendere `Goat` e `Sheep` ereditare `Animal`.  
  
7.  Utilizzare il **incorporamento** strumento per incorporare `Field` e `Animal` in `Farm`.  
  
8.  Si potrebbe voler ordinato nel diagramma. Per ridurre il numero di elementi duplicati, usare il **portare sottoalbero qui** comando nel menu di scelta rapida di elementi foglia.  
  
9. **Trasforma tutti i modelli** nella barra degli strumenti di Esplora soluzioni.  
  
10. Compilare il **Dsl** progetto.  
  
    > [!NOTE]
    >  In questa fase, gli altri progetti non verranno compilata senza errori. Tuttavia, si desidera compilare il progetto Dsl in modo che il relativo assembly sia disponibile per la creazione guidata origine dati.  
  
## <a name="updating-the-ui-project"></a>L'aggiornamento del progetto dell'interfaccia utente  
 È ora possibile creare un nuovo controllo utente che consente di visualizzare le informazioni archiviate nel modello DSL. Il modo più semplice per connettere il controllo utente per il modello è tramite le associazioni di dati. Il data binding di tipo di adattatore denominato **ModelingBindingSource** è progettato specificamente per la connessione DSL a interfacce non VMSDK.  
  
#### <a name="to-define-your-dsl-model-as-a-data-source"></a>Per definire il modello DSL come origine dati  
  
1.  Nel **dati** menu, scegliere **Mostra origini dati**.  
  
     Il **origini dati** verrà visualizzata la finestra.  
  
     Scegliere **Aggiungi nuova origine dati**. Il **configurazione guidata origine dati** apre.  
  
2.  Scegliere **oggetto**, **Avanti**.  
  
     Espandere **Dsl**, **Company.FarmApp**e selezionare **Farm**, che corrisponde alla classe radice del modello. Scegliere **Fine**.  
  
     In Esplora soluzioni, il **dell'interfaccia utente** progetto contiene ora **Properties\DataSources\Farm.datasource**  
  
     Le proprietà e relazioni della classe modello vengono visualizzati nella finestra Origini dati.  
  
     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png "DslWpf-3")  
  
#### <a name="to-connect-your-model-to-a-form"></a>Per connettere il modello a un form  
  
1.  Nel **dell'interfaccia utente** del progetto, eliminare tutti i file con estensione cs esistente.  
  
2.  Aggiungere un nuovo **controllo utente** file denominato `FarmControl` per il **dell'interfaccia utente** progetto.  
  
3.  Nel **origini dati** finestra, menu a discesa nel **Farm**, scegliere **dettagli**.  
  
     Lasciare le impostazioni predefinite per le altre proprietà.  
  
4.  Aprire FarmControl.cs nella visualizzazione progettazione.  
  
     Trascinare **Farm** dalla finestra Origini dati FarmControl.  
  
     Un set di controlli viene visualizzata, uno per ogni proprietà. I controlli non generano proprietà della relazione.  
  
5.  Eliminare **farmBindingNavigator**. Viene generato anche automaticamente nel `FarmControl` finestra di progettazione, ma non è utile per questa applicazione.  
  
6.  Utilizzando la casella degli strumenti, creare due istanze di **DataGridView**e assegnare loro un nome `AnimalGridView` e `FieldGridView`.  
  
    > [!NOTE]
    >  Un passaggio alternativo consiste nel trascinare gli elementi di animali e i campi dalla finestra Origini dati nel controllo. Questa azione crea automaticamente griglie dei dati e le associazioni tra la visualizzazione griglia e l'origine dati. Tuttavia, questa associazione non funziona correttamente per DSL. È pertanto consigliabile creare le griglie dei dati e le associazioni manualmente.  
  
7.  Se la casella degli strumenti non contiene il **ModelingBindingSource** strumento, aggiungerlo. Dal menu di scelta rapida del **dati** scegliere **Scegli elementi**. Nel **Scegli elementi della casella degli strumenti** finestra di dialogo Seleziona **ModelingBindingSource** dal **.NET Framework scheda**.  
  
8.  Utilizzando la casella degli strumenti, creare due istanze di **ModelingBindingSource**e assegnare loro un nome `AnimalBinding` e `FieldBinding`.  
  
9. Impostare il **DataSource** proprietà di ogni **ModelingBindingSource** a **farmBindingSource**.  
  
     Impostare il **DataMember** proprietà **animali** o **campi**.  
  
10. Impostare il **DataSource** le proprietà di `AnimalGridView` a `AnimalBinding`e di `FieldGridView` a `FieldBinding`.  
  
11. Modificare il layout del controllo Farm desiderato.  
  
 Il **ModelingBindingSource** un adattatore che esegue diverse funzioni che sono specifiche di DSL:  
  
-   Esegue il wrapping degli aggiornamenti in una transazione archivio VMSDK.  
  
     Ad esempio, quando l'utente elimina una riga dalla griglia di visualizzazione dei dati, un'associazione regolare comporta un'eccezione di transazione.  
  
-   Assicura che, quando l'utente seleziona una riga, la finestra proprietà vengono visualizzate le proprietà dell'elemento del modello corrispondente, anziché la riga della griglia di dati.  
  
 ![DslWpf4](../modeling/media/dslwpf4.png "DslWpf4")  
Schema dei collegamenti tra origini dati e viste.  
  
#### <a name="to-complete-the-bindings-to-the-dsl"></a>Per completare le associazioni del linguaggio DSL  
  
1.  Aggiungere il codice seguente in un file di codice separato nella **dell'interfaccia utente** progetto:  
  
    ```csharp  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Design;  
  
    namespace Company.FarmApp  
    {  
      partial class FarmControl  
      {  
        public IContainer Components { get { return components; } }  
  
        /// <summary>Binds the WinForms data source to the DSL model.  
        /// </summary>  
        /// <param name="nodelRoot">The root element of the model.</param>  
        public void DataBind(ModelElement modelRoot)  
        {  
          WinFormsDataBindingHelper.PreInitializeDataSources(this);  
          this.farmBindingSource.DataSource = modelRoot;  
          WinFormsDataBindingHelper.InitializeDataSources(this);  
        }  
      }  
    }  
    ```  
  
2.  Nel **DslPackage** progetto, modificare **DslPackage\DocView.tt** per aggiornare la definizione di variabile seguente:  
  
    ```csharp  
    string viewControlTypeName = "FarmControl";  
    ```  
  
## <a name="testing-the-dsl"></a>Test del linguaggio DSL  
 La soluzione DSL possibile compilare ed eseguire, sebbene potrebbe essere necessario aggiungere ulteriori miglioramenti in un secondo momento.  
  
#### <a name="to-test-the-dsl"></a>Per eseguire il test del linguaggio DSL  
  
1.  Compilare ed eseguire la soluzione.  
  
2.  Nell'istanza sperimentale di Visual Studio, aprire il **esempio** file.  
  
3.  Nel **FarmApp Explorer**, aprire il menu di scelta rapida nel **Farm** nodo radice, quindi scegliere **aggiungere nuovo Goat**.  
  
     `Goat1`è presente il **animali** visualizzazione.  
  
    > [!WARNING]
    >  È necessario utilizzare il menu di scelta rapida nel **Farm** nodo, non il **animali** nodo.  
  
4.  Selezionare il **Farm** nodo radice e visualizzarne le proprietà.  
  
     Nella visualizzazione del modulo, modificare il **nome** o **dimensioni** della farm.  
  
     Quando si abbandona ogni campo nel modulo, le modifiche alle proprietà corrispondenti nella finestra Proprietà.  
  
## <a name="enhancing-the-dsl"></a>Miglioramento del linguaggio DSL  
  
#### <a name="to-make-the-properties-update-immediately"></a>Per impostare le proprietà di aggiornamento immediato  
  
1.  Nella visualizzazione progettazione di FarmControl.cs, selezionare un campo semplice, ad esempio nome, dimensioni o IsOrganic.  
  
2.  Nella finestra Proprietà espandere **DataBindings** e aprire **(avanzate)**.  
  
     Nel **formattazione e associazione avanzata** finestra di dialogo, in **modalità aggiornamento origine dati**, scegliere **OnPropertyChanged**.  
  
3.  Compilare ed eseguire la soluzione.  
  
     Verificare che quando si modifica il contenuto del campo, la proprietà corrispondente di immediatamente le modifiche del modello Farm.  
  
#### <a name="to-provide-add-buttons"></a>Per fornire pulsanti Aggiungi  
  
1.  Nella visualizzazione progettazione di FarmControl.cs, utilizzare la casella degli strumenti per creare un pulsante nel form.  
  
     Modificare il nome e il testo del pulsante, ad esempio per `New Sheep`.  
  
2.  Aprire il codice dietro il pulsante (ad esempio facendovi doppio clic).  
  
     Modificare come indicato di seguito:  
  
    ```csharp  
    private void NewSheepButton_Click(object sender, EventArgs e)  
    {  
      using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))  
      {  
        elementOperations.MergeElementGroup(farm,  
          new ElementGroup(new Sheep(farm.Partition)));  
        t.Commit();  
      }  
    }  
  
    // The following code is shared with other add buttons:  
    private ElementOperations operationsCache = null;  
    private ElementOperations elementOperations  
    {  
      get  
      {  
        if (operationsCache == null)  
        {  
          operationsCache = new ElementOperations(farm.Store, farm.Partition);  
        }  
        return operationsCache;  
      }  
    }  
    private Farm farm  
    {  
      get { return this.farmBindingSource.DataSource as Farm; }  
    }  
  
    ```  
  
     Inoltre, è necessario inserire la direttiva seguente:  
  
    ```csharp  
  
    using Microsoft.VisualStudio.Modeling;  
  
    ```  
  
3.  Aggiungere pulsanti simili per i campi e caprini.  
  
4.  Compilare ed eseguire la soluzione.  
  
5.  Verificare che il nuovo pulsante Aggiunge un elemento. L'elemento nuovo verrà visualizzato in Esplora FarmApp e nella visualizzazione griglia dati appropriato.  
  
     Dovrebbe essere possibile modificare il nome dell'elemento nella visualizzazione griglia dati. È anche possibile eliminare da qui.  
  
 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  
  
### <a name="about-the-code-to-add-an-element"></a>Informazioni sul codice per aggiungere un elemento  
 Per i pulsanti del nuovo elemento, il seguente codice alternativo è leggermente più semplice.  
  
```csharp  
private void NewSheepButton_Click(object sender, EventArgs e)  
{  
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))  
  {  
    farm.Animals.Add(new Sheep(farm.Partition)); ;  
    t.Commit();  
  }  
}  
  
```  
  
 Questo codice, tuttavia, non impostare un nome predefinito per il nuovo elemento. Non viene eseguito alcun merge personalizzato che è stata definita nel **elemento unione direttive** di DSL, e non può essere eseguito il codice personalizzato di tipo merge che è stato definito.  
  
 Si consiglia di utilizzare <xref:Microsoft.VisualStudio.Modeling.ElementOperations> per creare nuovi elementi. Per ulteriori informazioni, vedere [la creazione degli elementi di personalizzazione e spostamento](../modeling/customizing-element-creation-and-movement.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)   
 [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [SDK di modellazione per Visual Studio (linguaggi specifici di dominio)](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)