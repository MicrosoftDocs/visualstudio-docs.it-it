---
title: Personalizzazione di strumenti e la casella degli strumenti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 160c1c27ab9d01dc76d6a5c76feb07179f7966b9
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="customizing-tools-and-the-toolbox"></a>Personalizzazione di strumenti e della casella degli strumenti
È necessario definire le voci della casella degli strumenti per gli elementi che gli utenti potranno aggiungere ai propri modelli. Esistono due tipi di strumenti: strumenti elemento e strumenti di connessione. Nella finestra di progettazione generata, un utente può selezionare uno strumento elemento per trascinare forme nel diagramma e uno strumento di connessione per tracciare i collegamenti tra le forme. In generale, gli strumenti elemento consentono agli utenti di aggiungere istanze di classi di dominio ai modelli e gli strumenti di connessione consentono di aggiungere istanze di relazioni di dominio.  
  
 In questo argomento  
  
-   [Modalità di definizione della casella degli strumenti](#ToolboxDef)  
  
-   [Personalizzazione di strumenti elemento](#customizing)  
  
-   [Creazione di gruppi di elementi da uno strumento](#groups)  
  
-   [Personalizzazione di strumenti di connessione](#connections)  
  
##  <a name="ToolboxDef"></a>Modalità di definizione della casella degli strumenti  
 In DSL Explorer espandere il nodo Editor e tutti i sottonodi. Verrà visualizzata una gerarchia simile alla seguente:  
  
```  
  
Editor  
     Toobox Tabs  
        MyDsl          //a tab  
           Tools  
               ExampleElement      // an element tool  
               ExampleRelationship // a connection tool  
  
```  
  
 In questa sezione di DSL Explorer è possibile:  
  
-   Creare nuove schede. Le schede definiscono le intestazioni di sezione nella casella degli strumenti.  
  
-   Creare nuovi strumenti.  
  
-   Copiare e incollare strumenti.  
  
-   Spostare gli strumenti verso l'alto o verso il basso nell'elenco.  
  
-   Eliminare schede e strumenti.  
  
> [!IMPORTANT]
>  Per aggiungere o incollare elementi in DSL Explorer, fare clic con il pulsante destro del mouse sul nodo padre del padre del nuovo nodo. Ad esempio, per aggiungere uno strumento, fare clic e non il **strumenti** nodo. Per aggiungere una scheda, fare doppio clic su di **Editor** nodo.  
  
 Il **icona casella degli strumenti** proprietà di ogni strumento fa riferimento a un file bitmap di 16x16. Questi file vengono in genere mantenuti **Dsl\Resources** cartella.  
  
 Il **classe** proprietà di uno strumento dell'elemento fa riferimento a una classe concreta dominio. Per impostazione predefinita, lo strumento creerà istanze di questa classe. È tuttavia possibile scrivere codice per fare in modo che lo strumento crei gruppi di elementi o elementi di tipi diversi.  
  
 Il **connessione generatore** proprietà di uno strumento di connessione fa riferimento a un generatore di connessione, che definisce i tipi di elementi lo strumento è possibile connettersi e le relazioni tra crea tra di essi. I generatori di connessioni sono definiti come nodi in DSL Explorer. I generatori di connessioni vengono creati automaticamente al momento della definizione delle relazioni di dominio, ma è possibile scrivere codice per personalizzarli.  
  
#### <a name="to-add-a-tool-to-the-toolbox"></a>Per aggiungere uno strumento alla casella degli strumenti  
  
1.  In genere si crea uno strumento elemento dopo avere creato una classe di forma e averla mappata a una classe di dominio.  
  
     Si crea invece uno strumento di connessione dopo avere creato una classe connettore e averla mappata a una relazione di riferimento.  
  
2.  In Esplora DSL, espandere il **Editor** nodo e **schede della casella degli strumenti** nodo.  
  
     Fare doppio clic su un nodo della scheda della casella degli strumenti e quindi fare clic su **Aggiungi nuovo elemento strumento** o **aggiungere di nuovo strumento di connessione**.  
  
3.  Impostare il **icona casella degli strumenti** proprietà per fare riferimento a una bitmap di 16x16.  
  
     Se si desidera definire una nuova icona, creare un file bitmap in Esplora soluzioni nel **Dsl\Resources** cartella. Il file deve avere i valori delle proprietà seguenti: **azione di compilazione** = **contenuto**; **Copia nella Directory di Output di** = **non copiare**.  
  
4.  **Per uno strumento di elemento:** impostare il **classe** proprietà dello strumento per fare riferimento a una classe concreta dominio che viene eseguito il mapping a una forma.  
  
     **Per uno strumento connettore:** impostare il **connessione generatore** proprietà dello strumento per uno degli elementi che sono disponibili nell'elenco a discesa. I generatori di connessione vengono creati automaticamente quando si mappa un connettore a una relazione di dominio. Se di recente si è creato un connettore, normalmente si selezionerà il generatore di connessioni associato.  
  
5.  Per testare il linguaggio specifico di dominio (DSL), premere F5 o CTRL+F5 e nell'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aprire un file di modello di esempio. Il nuovo strumento verrà visualizzato nella casella degli strumenti. Trascinarlo sul diagramma per verificare che crei un nuovo elemento.  
  
     Se lo strumento non viene visualizzato, arrestare l'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In Windows **avviare** menu, eseguire **ripristinare Microsoft Visual Studio 2010 istanza sperimentale**. Nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **compilare** menu, fare clic su **Ricompila soluzione**. Testare di nuovo il DSL.  
  
##  <a name="customizing"></a>Personalizzazione di strumenti dell'elemento  
 Per impostazione predefinita, lo strumento creerà una singola istanza della classe specificata, ma è possibile scegliere tra due alternative:  
  
-   Definire le direttive di merge degli elementi su altre classi, per consentire loro di accettare nuove istanze di questa classe e di creare collegamenti aggiuntivi quando viene creato il nuovo elemento. Ad esempio, è possibile consentire all'utente di rilasciare un commento su un altro elemento e quindi creare un collegamento di riferimento tra i due.  
  
     Queste personalizzazioni influiscono anche su ciò che succede quando l'utente incolla o trascina un elemento.  
  
     Per ulteriori informazioni, vedere [la creazione degli elementi di personalizzazione e spostamento](../modeling/customizing-element-creation-and-movement.md).  
  
-   Scrivere codice per personalizzare lo strumento in modo che possa creare gruppi di elementi. Lo strumento è inizializzato dai metodi in ToolboxHelper.cs che possono essere sostituiti. Per ulteriori informazioni, vedere [creazione di gruppi di elementi da uno strumento](#groups).  
  
##  <a name="groups"></a>Creazione di gruppi di elementi da uno strumento  
 Ogni strumento elemento contiene un prototipo degli elementi che deve creare. Per impostazione predefinita, ogni strumento elemento crea un singolo elemento, ma è anche possibile creare un gruppi di oggetti correlati con un solo strumento. A questo scopo, è necessario inizializzare lo strumento con un prototipo <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> che contiene gli elementi correlati.  
  
 L'esempio seguente è estratto da un DSL in cui è presente un tipo Transistor. Ogni transistor dispone di tre terminali denominati. Nello strumento elemento per i transistor è archiviato un prototipo contenente quattro elementi modello e tre collegamenti di relazione. Quando l'utente trascina lo strumento nel diagramma, viene creata un'istanza del prototipo che viene quindi collegato alla radice del modello.  
  
 Questo codice esegue l'override di un metodo che è definito in **Dsl\GeneratedCode\ToolboxHelper.cs**.  
  
 Per ulteriori informazioni sulla personalizzazione del modello utilizzando il codice programma, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
  public partial class CircuitsToolboxHelper  
  {  
    /// <summary>  
    /// Toolbox initialization, called for each element tool on the toolbox.  
    /// This version deals with each Component subtype separately.  
    /// </summary>  
    /// <param name="store"></param>  
    /// <param name="domainClassId">Identifies the domain class this tool should instantiate.</param>  
    /// <returns>prototype of the object or group of objects to be created by tool</returns>  
    protected override ElementGroupPrototype CreateElementToolPrototype(Store store, Guid domainClassId)  
    {  
        if (domainClassId == Transistor.DomainClassId)  
        {  
            Transistor transistor = new Transistor(store);  
  
            transistor.Base = new ComponentTerminal(store);  
            transistor.Collector = new ComponentTerminal(store);  
            transistor.Emitter = new ComponentTerminal(store);  
  
            transistor.Base.Name = "base";  
            transistor.Collector.Name = "collector";  
            transistor.Emitter.Name = "emitter";  
  
            // Create an ElementGroup for the Toolbox.  
            ElementGroup elementGroup = new ElementGroup(store.DefaultPartition);  
            elementGroup.AddGraph(transistor, true);  
            // AddGraph includes the embedded parts  
  
            return elementGroup.CreatePrototype();  
        }  
        else  
        {  
            return base.CreateElementToolPrototype(store, domainClassId);  
}  }    }  
  
```  
  
##  <a name="connections"></a>Personalizzazione di strumenti di connessione  
 Generalmente uno strumento elemento viene creato quando si crea una nuova classe connettore. In alternativa, è possibile sottoporre uno strumento a overload consentendo ai tipi delle due entità finali di determinare il tipo di relazione. È ad esempio possibile definire uno strumento di connessione che può creare sia relazioni Persona-Persona sia relazioni Persona-Città.  
  
 Gli strumenti di connessione richiamano i generatori di connessioni. Usare i generatori di connessioni per specificare il modo in cui gli utenti possono collegare gli elementi nella finestra di progettazione generata. I generatori di connessioni consentono di specificare gli elementi che si possono collegare e il tipo di collegamento che viene creato tra essi.  
  
 Quando si crea una relazione di riferimento tra classi di dominio, viene automaticamente creato un generatore di connessioni. È possibile usare questo generatore di connessioni per mappare uno strumento di connessione. Per ulteriori informazioni sulla creazione di strumenti di connessione, vedere [della casella degli strumenti di configurazione](../modeling/customizing-tools-and-the-toolbox.md).  
  
 È possibile modificare il generatore di connessioni predefinito in modo che possa gestire un intervallo di tipi di origine e destinazioni diverso e creare tipi di relazioni diversi.  
  
 È anche possibile scrivere codice personalizzato affinché i generatori di connessioni possano specificare le classi di origine e di destinazione per la connessione, definire il tipo di connessione da effettuare ed eseguire altre azioni associate alla creazione di una connessione.  
  
### <a name="the-structure-of-connection-builders"></a>Struttura dei generatori di connessioni  
 I generatori di connessioni contengono una o più direttive di collegamento connessione che specificano la relazione di dominio e gli elementi di origine e di destinazione. Nel modello di soluzione del flusso di attività, ad esempio, è possibile visualizzare il **CommentReferencesSubjectsBuilder** nel **Esplora DSL**. Questo generatore di connessione contiene un collegamento connettersi direttiva denominata **CommentReferencesSubjects**, che viene eseguito il mapping alla relazione dominio **CommentReferencesSubjects**. Questa direttiva di connessione di collegamento contiene una direttiva del ruolo di origine che fa riferimento alla classe di dominio `Comment` e una direttiva del ruolo di destinazione che fa riferimento alla classe di dominio `FlowElement`.  
  
### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Uso dei generatori di connessioni per limitare i ruoli di origine e di destinazione  
 È possibile usare i generatori di connessioni per limitare l'occorrenza di determinate classi sia nel ruolo di origine che nel ruolo di destinazione di una determinata relazione di dominio. Ad esempio, una classe di dominio di base potrebbe avere una relazione di dominio con un'altra classe di dominio, ma non si vuole che tutte le classi derivate della classe di base abbiano gli stessi ruoli in quella relazione. Nella soluzione del flusso di attività, sono presenti quattro classi concrete dominio (**StartPoint**, **EndPoint**, **MergeBranch**, e **sincronizzazione**) che ereditano direttamente dalla classe astratta dominio **FlowElement**, e due classi di dominio di concrete (**attività** e **ObjectInState**) che ereditare indirettamente da esso. È inoltre disponibile un **flusso** riferimento relazione che accetta **FlowElement** classi di dominio in cui sia il ruolo di origine e il ruolo di destinazione. Tuttavia, un'istanza di un **EndPoint** classe di dominio non deve essere l'origine di un'istanza di un **flusso** relazione, né deve un'istanza di un **StartPoint** classe il destinazione di un'istanza di un **flusso** relazione. Il **FlowBuilder** generatore di connessione dispone di un collegamento connettersi direttiva denominata **flusso** che specifica le classi di dominio che è possono riprodurre il ruolo di origine (**attività**,  **MergeBranch**, **StartPoint**, e **sincronizzazione**) e che può riprodurre il ruolo di destinazione (**MergeBranch**,  **Endpoint**, e **sincronizzazione**).  
  
### <a name="connection-builders-with-multiple-link-connect-directives"></a>Generatori di connessione con più direttive di connessione collegamento  
 È possibile aggiungere più di una direttiva di connessione di collegamento a un generatore di connessioni. Ciò consente di nascondere alcune delle complessità del modello di dominio da utenti e mantenere la **della casella degli strumenti** troppo rimangano. È possibile aggiungere direttive di connessione collegamento per diverse relazioni di dominio a un singolo generatore di connessioni. È tuttavia consigliabile combinare le relazioni di dominio quando svolgono approssimativamente la stessa funzione.  
  
 Nella soluzione del flusso di attività, il **flusso** dello strumento di connessione viene utilizzato per creare istanze di entrambi il **flusso** e **ObjectFlow** relazioni di dominio. Il **FlowBuilder** generatore di connessione deve, inoltre il **flusso** collegamento direttiva descritta in precedenza, collegamento due direttive denominate **ObjectFlow**. Queste direttive specificano che un'istanza di un **ObjectFlow** può tracciare una relazione tra le istanze del **ObjectInState** classe di dominio o da un'istanza di un **ObjectInState**  a un'istanza di un **attività**, ma non tra due istanze di un **attività**, o da un'istanza di un **attività** a un'istanza di un **ObjectInState**. Tuttavia, un'istanza di un **flusso** può tracciare una relazione tra due istanze di un **attività**. Se si compila e si esegue la soluzione del flusso di attività, è possibile visualizzare il disegno un **flusso** da un'istanza di un **ObjectInState** a un'istanza di un **attività** crea un'istanza di un **ObjectFlow**, ma disegno un **flusso** tra due istanze di un **attività** crea un'istanza di un **flusso**.  
  
### <a name="custom-code-for-connection-builders"></a>Codice personalizzato per i generatori di connessioni  
 Nell'interfaccia utente sono disponibili quattro caselle di controllo che definiscono i vari tipi di personalizzazione dei generatori di connessioni:  
  
-   il **personalizzato accettare** casella di controllo in una direttiva di ruolo di origine o di destinazione  
  
-   il **di connessione personalizzate** casella di controllo in una direttiva di ruolo di origine o di destinazione  
  
-   il **Usa Connetti personalizzato** casella di controllo in una direttiva di connect  
  
-   il **personalizzato è** proprietà del generatore di connessione  
  
 Per implementare queste personalizzazioni, è necessario fornire codice. Per informazioni sul codice da fornire, selezionare una delle caselle di controllo, fare clic su Trasforma tutti i modelli e quindi compilare la soluzione. Verrà visualizzato un report degli errori. Fare doppio clic sul report degli errori per visualizzare un commento che indica il codice da aggiungere.  
  
> [!NOTE]
>  Per aggiungere il codice personalizzato, creare una definizione di classe parziale in un file di codice separato dai file di codice nelle cartelle GeneratedCode. Per non perdere il lavoro svolto, non modificare i file di codice generati. Per ulteriori informazioni, vedere [si esegue l'override ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md).  
  
#### <a name="creating-custom-connection-code"></a>Creazione di codice di connessione personalizzato  
 In ogni collegamento connettersi direttiva, il **origine direttive ruolo** scheda definisce da quali tipi, è possibile trascinare. Analogamente, il **direttive ruolo di destinazione** scheda definisce per quali tipi, è possibile trascinare. Per ogni tipo, è inoltre possibile specificare se consentire la connessione (per tale collegamento direttiva) impostando il **personalizzato accettare** flag e quindi fornendo il codice aggiuntivo.  
  
 È anche possibile personalizzare ciò che accade una volta stabilita la connessione. Ad esempio, è possibile personalizzare solo il caso in cui il trascinamento si verifica da o a una classe specifica, tutti i casi regolamentati da una direttiva di connessione di collegamento o l'intero generatore di connessioni FlowBuilder. Per ognuna di queste opzioni, è possibile impostare flag personalizzati al livello appropriato. Quando si trasformano tutti i modelli e si tenta di compilare la soluzione, i messaggi di errore indirizzano l'utente ai commenti presenti nel codice generato. I commenti indicano ciò che è necessario fornire.  
  
 Nell'esempio relativo al diagramma dei componenti, il generatore di connessioni per la relazione di dominio Connessione è personalizzato per limitare le connessioni che possono essere stabilite tra le porte. Nell'illustrazione seguente viene mostrato che è possibile stabilire connessioni solo da elementi `OutPort` a elementi `InPort`, ma è possibile annidare i componenti l'uno all'interno dell'altro.  
  
 **Connessione a un OutPort provenienti da un componente annidato**  
  
 ![Generatore di connessione](../modeling/media/connectionbuilder_3.png "ConnectionBuilder_3")  
  
 È possibile specificare che una connessione può provenire da un componente annidato a un elemento OutPort. Per specificare una connessione, impostare **utilizza accettare personalizzato** sul **InPort** tipo come ruolo di origine e **OutPort** tipo come ruolo di destinazione nel **dettagli DSL**  finestra, come illustrato nelle figure seguenti:  
  
 **Collegamento di direttiva in Esplora DSL**  
  
 ![Immagine del generatore di connessione](../modeling/media/connectionbuilder_4a.png "ConnectionBuilder_4a")  
  
 **Collegamento di direttiva nella finestra Dettagli DSL**  
  
 ![](../modeling/media/connectionbuilder_4b.png "ConnectionBuilder_4b")  
  
 È quindi necessario fornire i metodi nella classe ConnectionBuilder:  
  
```  
  public partial class ConnectionBuilder  
  {  
    /// <summary>  
    /// OK if this component has children  
    /// </summary>  
    private static bool CanAcceptInPortAsSource(InPort candidate)  
    {  
       return candidate.Component.Children.Count > 0;  
    }  
  
    /// <summary>  
    /// Only if source is on parent of target.  
    /// </summary>  
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)  
    {  
      return sourceInPort.Component == targetInPort.Component.Parent;  
    }  
// And similar for OutPorts...  
```  
  
 Per ulteriori informazioni sulla personalizzazione del modello utilizzando il codice programma, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 È possibile usare un codice simile, ad esempio, per impedire agli utenti di creare cicli con collegamenti padre-figlio. Queste restrizioni vengono considerate i vincoli 'hard' perché gli utenti non possono violare in qualsiasi momento. È inoltre possibile creare i controlli di convalida 'soft' che gli utenti possono ignorare temporaneamente per la creazione di configurazioni non valide che non possono essere salvate.  
  
### <a name="good-practice-in-defining-connection-builders"></a>Procedure consigliate per la definizione dei generatori di connessioni  
 È consigliabile definire un generatore di connessioni per creare diversi tipi di relazioni solo se queste sono correlate a livello concettuale. Nell'esempio relativo al flusso attività, si usa lo stesso generatore per creare flussi tra attività e tra attività e oggetti. Tuttavia, usare lo stesso generatore per creare relazioni tra commenti e attività potrebbe creare confusione.  
  
 Se si definisce un generatore di connessioni per più tipi di relazioni, è necessario assicurarsi che non possa corrispondere a più di un tipi dalla stessa coppia di oggetti di origine e di destinazione. In caso contrario, i risultati non saranno prevedibili.  
  
 Utilizzare codice personalizzato per applicare vincoli 'hard', ma è necessario considerare se gli utenti devono essere in grado di rendere temporaneamente le connessioni non valide. Se si vuole concedere questa possibilità, è possibile modificare i vincoli in modo che le connessioni non vengano convalidate fino a quando gli utenti non tentano di salvare le modifiche.  
  
## <a name="see-also"></a>Vedere anche  
 [Lo spostamento e la creazione degli elementi di personalizzazione](../modeling/customizing-element-creation-and-movement.md)   
 [Personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md)   
 [Procedura: aggiungere un gestore di trascinamento e rilascio](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Esempio di diagrammi circuito DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)