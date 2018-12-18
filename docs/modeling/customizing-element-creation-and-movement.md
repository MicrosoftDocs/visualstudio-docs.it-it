---
title: Personalizzazione della creazione e dello spostamento di elementi
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4747d41377d3f7cccce9142d0659251d3199714a
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="customizing-element-creation-and-movement"></a>Personalizzazione della creazione e dello spostamento di elementi
È possibile consentire a un elemento essere trascinato su un altro, dalla casella degli strumenti o in un'Incolla o dell'operazione di spostamento. È possibile disporre gli elementi spostati collegati a elementi di destinazione, utilizzando le relazioni che specificano.

 Una direttiva di tipo merge di elemento (Taiwanese) specifica che cosa avviene quando un elemento del modello è *unito* in un altro elemento del modello. Questo errore si verifica quando:

-   L'utente trascina dalla casella degli strumenti nel diagramma o una forma.

-   L'utente crea un elemento con un menu Aggiungi in Esplora risorse o una forma di raggruppamento.

-   L'utente sposta un elemento da una corsia a un altro.

-   L'utente incolla un elemento.

-   Il codice del programma chiama la direttiva di tipo merge di elemento.

 Anche se le operazioni di creazione possono sembrare può essere diverso dalle operazioni di copia, effettivamente funzionano nello stesso modo. Quando si aggiunge un elemento, ad esempio dalla casella degli strumenti, un prototipo di esso viene replicato. Il prototipo viene unito nel modello nello stesso modo come elementi che sono stati copiati da un'altra parte del modello.

 La responsabilità di un Taiwanese consiste nel decidere come un oggetto o un gruppo di oggetti deve essere unita in una determinata posizione nel modello. In particolare, decide le relazioni tra devono essere creata un'istanza per creare un collegamento nel modello del gruppo. È anche possibile personalizzare per impostare le proprietà e per creare oggetti aggiuntivi.

 ![DSL&#45;EMD&#95;di tipo Merge](../modeling/media/dsl-emd_merge.png "DSL EMD_Merge") il ruolo di una direttiva di elemento di tipo Merge

 Quando si definisce una relazione di incorporamento, viene generato automaticamente un Taiwanese. Questa impostazione predefinita Taiwanese crea un'istanza della relazione, quando gli utenti di aggiungere nuove istanze figlio al padre. È possibile modificare questi EMDs predefinito, ad esempio aggiungendo codice personalizzato.

 È inoltre possibile aggiungere la propria EMDs nella definizione del linguaggio DSL, per consentire agli utenti di trascinare o incollare diverse combinazioni delle classi sottoposto a merge e la ricezione.

## <a name="defining-an-element-merge-directive"></a>Definizione di una direttiva di tipo Merge di elemento
 È possibile aggiungere le direttive di tipo merge di elemento per le classi di dominio, relazioni di dominio, forme, i connettori e diagrammi. È possibile aggiungere o trovarle in Esplora DSL sotto la classe di dominio di destinazione. La classe ricevente è la classe di dominio dell'elemento che è già nel modello e in cui verrà unito l'elemento nuovo o copiato.

 ![DSL&#45;EMD&#95;Details](../modeling/media/dsl-emd_details.png "DSL-EMD_Details")

 Il **indicizzazione classe** è la classe di dominio di elementi che possono essere unite nei membri della classe ricevente. Le istanze delle sottoclassi della classe di indicizzazione verranno unite anche da questo Taiwanese, a meno che non si imposta **si applica alle sottoclassi** su False.

 Esistono due tipi di direttiva di tipo merge:

-   Oggetto **processo Merge** direttiva specifica le relazioni mediante il quale il nuovo elemento deve essere collegato all'albero.

-   Oggetto **rollforward Merge** direttiva reindirizza il nuovo elemento a un altro elemento ricevente, in genere un elemento padre.

 È possibile aggiungere codice personalizzato per unire le direttive:

-   Impostare **personalizzato utilizza accettare** per aggiungere codice personalizzato per determinare se una particolare istanza dell'elemento indicizzazione deve essere unita nell'elemento di destinazione. Quando l'utente trascina dalla casella degli strumenti, il puntatore "non valido" Mostra se il codice non consente l'unione.

     Ad esempio, è possibile consentire l'unione solo quando l'elemento di destinazione è in un determinato stato.

-   Impostare **unione personalizzata utilizza** aggiungere fornire codice personalizzato per definire le modifiche apportate al modello quando viene eseguito il merge.

     Ad esempio, è possibile impostare proprietà nell'elemento unito utilizzando i dati dalla nuova posizione nel modello.

> [!NOTE]
>  Se si scrive codice personalizzato di tipo merge, influisce soli operazioni di unione che vengono eseguite utilizzando questa Taiwanese. Se sono presenti altri EMDs che lo stesso tipo di oggetto di tipo merge, o se è presente altro codice personalizzato che crea questi oggetti senza utilizzare il Taiwanese, quindi non verrà influenzato dal codice personalizzato di tipo merge.
>
>  Se si desidera assicurarsi che un nuovo elemento o una nuova relazione viene sempre elaborato il codice personalizzato, si consiglia di definire un `AddRule` nella relazione di incorporamento e `DeleteRule` nella classe di dominio dell'elemento. Per ulteriori informazioni, vedere [propagare le modifiche all'interno di modello di regole](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="example-defining-an-emd-without-custom-code"></a>Esempio: Definizione di un Taiwanese senza codice personalizzato
 Nell'esempio seguente consente di creare un elemento e un connettore nello stesso momento mediante il trascinamento dalla casella degli strumenti in una forma esistente. L'esempio aggiunge un Taiwanese alla definizione DSL. Prima di questa modifica, gli utenti possono trascinare strumenti nel diagramma, ma non sulle forme esistenti.

 Gli utenti è inoltre possono incollare gli elementi su altri elementi.

#### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Per consentire agli utenti di creare un elemento e un connettore nello stesso momento

1.  Creare un nuovo DSL utilizzando il **Language minimo** modello di soluzione.

     Quando si esegue questo DSL, è possibile creare forme e connettori tra le forme. Non è possibile trascinare un nuovo **ExampleElement** forma dalla casella degli strumenti in una forma esistente.

2.  Per consentire agli utenti di unire gli elementi sul `ExampleElement` forme, creare un nuovo Taiwanese nel `ExampleElement` classe di dominio:

    1.  In **Esplora DSL**, espandere **classi di dominio**. Fare doppio clic su `ExampleElement` e quindi fare clic su **Aggiungi nuovo elemento di tipo Merge direttiva**.

    2.  Assicurarsi che il **dettagli DSL** finestra è aperta, in modo che è possibile visualizzare i dettagli del nuovo Taiwanese. (Menu: **vista**, **altre finestre**, **dettagli DSL**.)

3.  Impostare il **indicizzazione classe** nella finestra Dettagli DSL, per definire la classe di elementi può essere unita in `ExampleElement` oggetti.

     Per questo esempio, selezionare `ExampleElements`, in modo che l'utente può trascinare nuovi elementi in elementi esistenti.

     Si noti che la classe di indicizzazione diventa il nome del Taiwanese in Esplora DSL.

4.  In **merge processo tramite la creazione di collegamenti**, aggiungere due percorsi:

    1.  Un percorso collega il nuovo elemento di modello padre. L'espressione di percorso che è necessario immettere consente di passare dall'elemento esistente, backup tramite la relazione di incorporamento per il modello padre. Infine, specifica il ruolo nel nuovo collegamento a cui verrà assegnato il nuovo elemento. Il percorso è come segue:

         `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`

    2.  L'altro percorso collega il nuovo elemento all'elemento esistente. L'espressione di percorso Specifica la relazione di riferimento e il ruolo a cui verrà assegnato il nuovo elemento. Questo percorso è la seguente:

         `ExampleElementReferencesTargets.Sources`

     È possibile utilizzare lo strumento di navigazione del tracciato per creare ogni percorso:

    1.  In **merge processo tramite la creazione di collegamenti in percorsi**, fare clic su  **\<aggiungere percorso >**.

    2.  Fare clic sulla freccia a discesa a destra dell'elemento di elenco. Verrà visualizzata una visualizzazione albero.

    3.  Espandere i nodi dell'albero per formare il percorso che si desidera specificare.

5.  Test del linguaggio DSL:

    1.  Premere F5 per ricompilare ed eseguire la soluzione.

         La ricompilazione richiede più tempo del solito perché verrà aggiornato il codice generato dai modelli di testo per conformità alla nuova definizione DSL.

    2.  Quando l'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è avviato, aprire un file di modello di tale linguaggio DSL. Creare alcuni elementi di esempio.

    3.  Trascinare il **elemento esempio** strumento in una forma esistente.

         Verrà visualizzata una nuova forma e collegarla alla forma con un connettore esistente.

    4.  Copiare una forma esistente. Selezionare un'altra forma e incollare.

         Viene creata una copia della prima forma.  Ha un nuovo nome e la seconda forma con un connettore è collegato.

 Si noti quanto segue da questa procedura:

-   Tramite la creazione di direttive di elemento di tipo Merge, è possibile consentire a qualsiasi classe di elemento per accettare un altro. Il Taiwanese viene creato nella classe di dominio di destinazione e il dominio accettato è specificato nella **classe Index** campo.

-   Definendo i percorsi, è possibile specificare i collegamenti che devono essere utilizzata per connettere il nuovo elemento al modello esistente.

     I collegamenti desiderati devono includere una relazione di incorporamento.

-   Il Taiwanese influisce sia creazione dalla casella degli strumenti e anche le operazioni Incolla.

     Se si scrive codice personalizzato che consente di creare nuovi elementi, è possibile richiamare in modo esplicito il Taiwanese utilizzando il `ElementOperations.Merge` metodo. Ciò assicura che il codice collega nuovi elementi del modello nello stesso modo di altre operazioni. Per ulteriori informazioni, vedere [personalizzazione copia comportamento](../modeling/customizing-copy-behavior.md).

## <a name="example-adding-custom-accept-code-to-an-emd"></a>Esempio: Aggiunta di codice personalizzato accetta un Taiwanese
 Aggiungendo codice personalizzato per un Taiwanese, è possibile definire il comportamento di unione più complesso. Questo semplice esempio impedisce all'utente di aggiungere più di un numero fisso di elementi nel diagramma. Nell'esempio viene modificato il valore predefinito EMD associato a una relazione di incorporamento.

#### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Per scrivere codice personalizzato accettare per limitare gli elementi che è possibile aggiungere l'utente

1.  Creare un linguaggio DSL utilizzando il **Language minimo** modello di soluzione. Aprire il diagramma della definizione DSL.

2.  In Esplora DSL espandere **classi di dominio**, `ExampleModel`, **elemento Merge direttive**. Selezionare la direttiva di tipo merge elemento denominato `ExampleElement`.

     Questo Taiwanese controlla la modalità con cui l'utente può creare nuovi `ExampleElement` gli oggetti del modello, ad esempio mediante il trascinamento dalla casella degli strumenti.

3.  Nel **dettagli DSL** selezionare **personalizzato utilizza accettare**.

4.  Ricompilare la soluzione. Questa operazione richiederà più tempo del solito perché il codice generato verrà aggiornato dal modello.

     Un errore di compilazione saranno segnalati, simile a: "Company.ElementMergeSample.ExampleElement non contiene una definizione per CanMergeExampleElement..."

     È necessario implementare il metodo `CanMergeExampleElement`.

5.  Creare un nuovo file di codice nel **Dsl** progetto. Sostituire il contenuto con il codice riportato di seguito e modificare lo spazio dei nomi per lo spazio dei nomi del progetto.

    ```csharp
    using Microsoft.VisualStudio.Modeling;

    namespace Company.ElementMergeSample // EDIT.
    {
      partial class ExampleModel
      {
        /// <summary>
        /// Called whenever an ExampleElement is to be merged into this ExampleModel.
        /// This happens when the user pastes an ExampleElement
        /// or drags from the toolbox.
        /// Determines whether the merge is allowed.
        /// </summary>
        /// <param name="rootElement">The root element in the merging EGP.</param>
        /// <param name="elementGroupPrototype">The EGP that the user wants to merge.</param>
        /// <returns>True if the merge is allowed</returns>
        private bool CanMergeExampleElement(ProtoElementBase rootElement, ElementGroupPrototype elementGroupPrototype)
        {
          // Allow no more than 4 elements to be added:
          return this.Elements.Count < 4;
        }
      }
    }

    ```

     Questo semplice esempio limita il numero di elementi che possono essere uniti in del modello padre. Per le condizioni più interessante, il metodo è possibile esaminare le proprietà e i collegamenti dell'oggetto di destinazione. Anche possibile esaminare le proprietà degli elementi unione, che vengono eseguiti in un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Per ulteriori informazioni su `ElementGroupPrototypes`, vedere [personalizzazione copia comportamento](../modeling/customizing-copy-behavior.md). Per ulteriori informazioni su come scrivere codice che legge un modello, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

6.  Test del linguaggio DSL:

    1.  Premere F5 per compilare la soluzione. Quando l'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene aperto, aprire un'istanza di tale linguaggio DSL.

    2.  Creare nuovi elementi in diversi modi:

        1.  Trascinare il **elemento esempio** strumento nel diagramma.

        2.  Nel **Esplora modelli di esempio**, il pulsante destro del nodo radice e quindi fare clic su **Aggiungi nuovo elemento di esempio**.

        3.  Copiare e incollare un elemento nel diagramma.

    3.  Verificare che non è possibile utilizzare uno dei seguenti modi per aggiungere più di quattro elementi nel modello. Questo avviene perché tutte utilizzano la direttiva di elemento di tipo Merge.

## <a name="example-adding-custom-merge-code-to-an-emd"></a>Esempio: Aggiunta di codice personalizzato di tipo Merge per un Taiwanese
 Nel codice personalizzato di tipo merge, è possibile definire cosa accade quando l'utente trascina uno strumento o Incolla su un elemento. Esistono due modi per definire un'unione personalizzata:

1.  Impostare **utilizza Merge personalizzata** e fornire il codice necessario. Il codice sostituisce il codice generato di tipo merge. Utilizzare questa opzione se si desidera ridefinire completamente cosa il merge.

2.  Eseguire l'override di `MergeRelate` (metodo) e facoltativamente il `MergeDisconnect` (metodo). A tale scopo, è necessario impostare il **genera derivato doppie** proprietà della classe di dominio. Il codice può chiamare il codice di unione generato nella classe base. Utilizzare questa opzione se si desidera eseguire ulteriori operazioni dopo aver eseguito il merge.

 Questi approcci influiscono solo sui processi di merge che vengono eseguite utilizzando questa Taiwanese. Se si desidera influiscono su tutti i modi in cui è possibile creare l'elemento unito, in alternativa è possibile definire un `AddRule` nella relazione di incorporamento e `DeleteRule` nella classe di dominio sottoposto a merge. Per ulteriori informazioni, vedere [propagare le modifiche all'interno di modello di regole](../modeling/rules-propagate-changes-within-the-model.md).

#### <a name="to-override-mergerelate"></a>Per eseguire l'override MergeRelate

1.  Nella definizione del linguaggio DSL, assicurarsi che sia stata definita la Taiwanese a cui si desidera aggiungere il codice. Se si desidera, è possibile aggiungere i percorsi e definire personalizzato accetta codice, come descritto nelle sezioni precedenti.

2.  Nel diagramma DslDefinition, selezionare la classe di destinazione dell'unione. In genere si tratta della classe alla fine di origine di una relazione di incorporamento.

     Ad esempio, in un linguaggio DSL generato dalla soluzione minima lingua, selezionare `ExampleModel`.

3.  Nel **proprietà** finestra impostare **genera doppie derivato** per **true**.

4.  Ricompilare la soluzione.

5.  Controllare il contenuto di **Dsl\Generated Files\DomainClasses.cs**. Cerca i metodi denominati `MergeRelate` ed esaminare il relativo contenuto. Ciò consentirà di scrivere le versioni personalizzate.

6.  In un nuovo file di codice, scrivere una classe parziale per la classe di destinazione ed eseguire l'override di `MergeRelate` metodo. Ricordarsi di chiamare il metodo di base. Ad esempio:

    ```csharp
    partial class ExampleModel
    {
      /// <summary>
      /// Called when the user drags or pastes an ExampleElement onto the diagram.
      /// Sets the time of day as the name.
      /// </summary>
      /// <param name="sourceElement">Element to be added</param>
      /// <param name="elementGroup">Elements to be merged</param>
      protected override void MergeRelate(ModelElement sourceElement, ElementGroup elementGroup)
      {
        // Connect the element according to the EMD:
        base.MergeRelate(sourceElement, elementGroup);

        // Custom actions:
        ExampleElement mergingElement = sourceElement as ExampleElement;
        if (mergingElement != null)
        {
          mergingElement.Name = DateTime.Now.ToLongTimeString();
        }
      }
    }

    ```

#### <a name="to-write-custom-merge-code"></a>Per scrivere codice personalizzato di tipo Merge

1.  In **Dsl\Generated Code\DomainClasses.cs**, controllare i metodi denominati `MergeRelate`. Questi metodi creano collegamenti tra un nuovo elemento e il modello esistente.

     Controllare inoltre i metodi denominati `MergeDisconnect`. Questi metodi scollegare un elemento dal modello, in questo caso deve essere eliminato.

2.  In **Esplora DSL**, selezionare o creare la direttiva Element Merge che si desidera personalizzare. Nel **dettagli DSL** finestra impostare **utilizza Merge personalizzato**.

     Quando si imposta questa opzione, il **processo Merge** e **rollforward Merge** opzioni vengono ignorate. Viene invece utilizzato il codice.

3.  Ricompilare la soluzione. Richiederà più tempo del solito perché i file di codice generato verranno aggiornati dal modello.

     Verranno visualizzati messaggi di errore. Fare doppio clic sui messaggi di errore per vedere le istruzioni nel codice generato. Queste istruzioni chiesto di fornire due metodi, ovvero `MergeRelate` *YourDomainClass* e `MergeDisconnect` *YourDomainClass*

4.  Scrivere i metodi in una definizione di classe parziale in un file di codice separato. Negli esempi che è controllato in precedenza devono suggerire le informazioni necessarie.

 Codice personalizzato di tipo merge non influirà sul codice che crea oggetti e relazioni direttamente e non avrà alcun effetto altri EMDs. Per assicurarsi che le modifiche aggiuntive vengono implementate indipendentemente dalla modalità di creazione dell'elemento, prendere in considerazione la scrittura un `AddRule` e `DeleteRule` invece. Per ulteriori informazioni, vedere [propagare le modifiche all'interno di modello di regole](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="redirecting-a-merge-operation"></a>Reindirizzamento di un'operazione di unione
 Una direttiva di unione in avanti reindirizza la destinazione di un'operazione di unione. La nuova destinazione è in genere, l'incorporamento padre della destinazione iniziale.

 In un linguaggio DSL che è stato creato con il modello di diagramma componente, ad esempio, le porte sono incorporate nei componenti. Le porte vengono visualizzate come forme di piccole dimensioni per il bordo di una forma di componente. L'utente crea porte, trascinare lo strumento di porta in una forma di componente. In alcuni casi, l'utente trascina erroneamente lo strumento di porta su una porta esistente, anziché il componente, ma l'operazione non riesce. Questo è un semplice errore quando sono presenti diverse porte esistenti. Per consentire all'utente per evitare questo fastidiosi, è possibile consentire le porte per è possibile trascinare una porta esistente, ma l'azione reindirizzato al componente padre. L'operazione viene eseguita come se l'elemento di destinazione sono stati il componente.

 È possibile creare una direttiva di unione in avanti nella soluzione del modello di componente. Se viene compilato ed eseguito la soluzione originale, si noterà che gli utenti possono trascinare un numero qualsiasi di **porta di Input** o **porta di Output** gli elementi dal **della casella degli strumenti** per un **Componente** elemento. Tuttavia, è possibile trascinare una porta a una porta esistente. Gli avvisi di puntatore disponibile che questo spostamento non è abilitati. Tuttavia, è possibile creare una direttiva di inoltro di tipo merge in modo che una porta che viene accidentalmente eliminato su un oggetto esistente **porta di Input** viene inoltrato al **componente** elemento.

#### <a name="to-create-a-forward-merge-directive"></a>Per creare una direttiva di inoltro di tipo merge

1.  Creare un [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] soluzione usando il modello di componente.

2.  Visualizzazione di **Esplora DSL** aprendo DslDefinition.dsl.

3.  Nel **Esplora DSL**, espandere **classi di dominio**.

4.  Il **ComponentPort** classe astratta di dominio è la classe di base di entrambi **InPort** e **OutPort**. Fare doppio clic su **ComponentPort** e quindi fare clic su **Aggiungi nuovo elemento di tipo Merge direttiva**.

     Un nuovo **direttiva Merge Element** nodo viene visualizzato sotto il **elemento Merge direttive** nodo.

5.  Selezionare il **elemento Merge direttiva** nodo e aprire il **dettagli DSL** finestra.

6.  Nell'elenco di classi di indicizzazione, selezionare **ComponentPort**.

7.  Selezionare **inoltrare merge in una classe di dominio diverso**.

8.  Nell'elenco di selezione dei percorsi, espandere **ComponentPort**, espandere **ComponentHasPorts**, quindi selezionare **componente**.

     Il nuovo percorso dovrebbe essere simile a questo:

     **ComponentHasPorts.Component/!Component**

9. Salvare la soluzione e trasformare i modelli facendo clic sul pulsante più a destra il **Esplora** barra degli strumenti.

10. Compilare ed eseguire la soluzione. Una nuova istanza della [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene visualizzato.

11. In **Esplora**, aprire Sample.mydsl. Il diagramma e **ComponentLanguage della casella degli strumenti** vengono visualizzati.

12. Trascinare un **porta di Input** dal **casella degli strumenti** a un altro **porta di Input.** Successivamente, trascinare un **OutputPort** per un **InputPort** e quindi in un altro **OutputPort**.

     Non verrà visualizzato il puntatore non disponibile e dovrebbe essere in grado di rilasciare il nuovo **porta di Input** in uno esistente. Selezionare la nuova **porta di Input** e trascinarlo a un altro punto di **componente**.

## <a name="see-also"></a>Vedere anche

- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Personalizzazione di strumenti e della casella degli strumenti](../modeling/customizing-tools-and-the-toolbox.md)
- [Esempio di diagrammi circuito DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)