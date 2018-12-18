---
title: Utilizzo di ModelBus di Visual Studio in un modello di testo | Documenti Microsoft
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
ms.openlocfilehash: 0184e3b543e509d0e523504c0ea07f6fcc36775f
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Utilizzo di ModelBus di Visual Studio in un modello di testo
Se si scrivono modelli di testo che leggono un modello contenente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus fa riferimento, si consiglia di risolvere i riferimenti per accedere ai modelli di destinazione. In tal caso, è necessario adattare i modelli di testo e i riferimento linguaggi specifici di dominio (DSL):  
  
-   DSL che rappresenta la destinazione dei riferimenti deve essere una scheda di ModelBus configurato per l'accesso da modelli di testo. Se si accede anche del linguaggio DSL da altro codice, la scheda riconfigurata è richiesto insieme a della scheda ModelBus standard.  
  
     Il gestore di adattatori deve ereditare da <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> e deve avere l'attributo `[HostSpecific(HostName)]`.  
  
-   Il modello deve ereditare da <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
> [!NOTE]
>  Se si desidera leggere modelli DSL che non contengono riferimenti ModelBus, è possibile utilizzare i processori di direttive generate nei progetti DSL. Per ulteriori informazioni, vedere [l'accesso a modelli da modelli di testo](../modeling/accessing-models-from-text-templates.md).  
  
 Per ulteriori informazioni sui modelli di testo, vedere [generazione codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>Creazione di una scheda Bus modello per l'accesso da modelli di testo  
 Per risolvere un riferimento di ModelBus in un modello di testo, la destinazione DSL deve avere una scheda compatibile. Modelli di testo eseguite in un AppDomain separato dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor di documenti e pertanto l'adapter deve caricare il modello anziché accedervi tramite DTE.  
  
#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>Per creare un adattatore ModelBus compatibile con i modelli di testo  
  
1.  Se la soluzione DSL di destinazione non dispone di un **ModelBusAdapter** del progetto, crearne uno utilizzando la procedura guidata Modelbus estensione:  
  
    1.  Scaricare e installare il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus di estensione, se non è stato già fatto. Per ulteriori informazioni, vedere [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
    2.  Aprire il file di definizione del linguaggio specifico di dominio. Fare doppio clic nell'area di progettazione e quindi fare clic su **abilitare Modelbus**.  
  
    3.  Nella finestra di dialogo, selezionare **si desidera esporre questo DSL per il ModelBus**. È possibile selezionare entrambe le opzioni se si desidera che questa DSL per esporre i modelli e utilizzare i riferimenti agli altri DSL.  
  
    4.  Fare clic su **OK**. Un nuovo progetto "ModelBusAdapter" verrà aggiunto alla soluzione relativa al linguaggio specifico di dominio.  
  
    5.  Fare clic su **Trasforma tutti i modelli**.  
  
    6.  Ricompilare la soluzione.  
  
2.  Se si desidera accedere del linguaggio DSL, da un modello di testo e da altro codice, ad esempio di comando, Duplica la **ModelBusAdapter** progetto:  
  
    1.  In Esplora risorse, copiare e incollare la cartella che contiene **ModelBusAdapter.csproj**.  
  
    2.  Rinominare il file di progetto (ad esempio, per **T4ModelBusAdapter.csproj**).  
  
    3.  In **Esplora**, fare doppio clic sul nodo della soluzione, scegliere **Aggiungi**, quindi fare clic su **progetto esistente**. Individuare il nuovo progetto di adapter, **T4ModelBusAdapter.csproj**.  
  
    4.  In ogni `*.tt` file del nuovo progetto, modificare lo spazio dei nomi.  
  
    5.  Fare clic sul nuovo progetto in Esplora soluzioni e quindi fare clic su proprietà. Nell'editor delle proprietà, modificare i nomi di assembly generato e lo spazio dei nomi predefinito.  
  
    6.  Nel progetto DslPackage, aggiungere un riferimento al nuovo progetto di adapter in modo che include riferimenti a entrambe le schede.  
  
    7.  In DslPackage\source.extension.tt, aggiungere una linea che fa riferimento il nuovo progetto di adapter.  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **Trasforma tutti i modelli** e ricompilare la soluzione. Non devono essere eseguito errori di compilazione.  
  
3.  Nel nuovo progetto di adapter, aggiungere riferimenti agli assembly riportati di seguito:  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  In AdapterManager.tt:  
  
    -   Modificare la dichiarazione di AdapterManagerBase in modo che erediti da <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   Verso la fine del file, sostituire l'attributo HostSpecific prima della classe del gestore adattatori. Rimuovere la riga seguente:  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         Inserire la riga seguente:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Questo attributo consente di filtrare il set di schede che è disponibile quando un consumer di modelbus Cerca un adapter.  
  
5.  **Trasforma tutti i modelli** e ricompilare la soluzione. Non devono essere eseguito errori di compilazione.  
  
## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>Scrittura di un modello di testo che può risolvere i riferimenti di ModelBus  
 In genere, iniziare con un modello che legge e genera i file da un linguaggio DSL "source". Questo modello utilizza la direttiva che viene generata nel progetto DSL di origine per leggere i file di modello di origine nel modo descritto in [l'accesso a modelli da modelli di testo](../modeling/accessing-models-from-text-templates.md). Tuttavia, l'origine DSL contiene riferimenti ModelBus a un linguaggio DSL "target". Pertanto necessario abilitare il codice del modello risolvere i riferimenti e accedere al linguaggio specifico di dominio di destinazione. È pertanto necessario adattare il modello seguendo questi passaggi:  
  
-   Modificare la classe di base del modello da <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
-   Includere `hostspecific="true"` nella direttiva del modello.  
  
-   Aggiungere riferimenti ad assembly per la destinazione DSL e adattatore e abilitare ModelBus.  
  
-   Non è necessaria la direttiva che viene generata come parte della destinazione del linguaggio DSL.  
  
```  
<#@ template debug="true" hostspecific="true" language="C#"  
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
<#@ output extension=".txt" #>  
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>  
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>  
<#@ assembly name = "System.Core" #>  
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
<#@ import namespace="Company.TargetDsl" #>  
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>  
<#@ import namespace="System.Linq" #>  
<#  
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.  
  // In the source DSL Definition, the root element has a model reference:  
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)   
  {if (adapter != null)  
   {  
      // Get the root of the target model:  
      TargetRoot target = adapter.ModelRoot;  
    // The source DSL Definition has a class "SourceElement" embedded under the root.  
    // (Let's assume they're all in the same model file):  
    foreach (SourceElement sourceElement in source.Elements)  
    {  
      // In the source DSL Definition, each SourceElement has a MBR property:  
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;  
      // Resolve the target model element:   
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);   
#>  
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.  
<#  
    }  
  }}  
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename   
  // from a path that is relative to the text template.  
#>  
  
```  
  
 Quando viene eseguito questo modello di testo, il `SourceDsl` direttiva carica il file `Sample.source`. Il modello può accedere agli elementi del modello, a partire da `this.ModelRoot`. Il codice è possibile utilizzare le classi di dominio e proprietà di tale linguaggio DSL.  
  
 Inoltre, il modello può risolvere i riferimenti di ModelBus. Se i riferimenti puntano al modello di destinazione, le direttive assembly lasciare che il codice utilizzare le classi di dominio e le proprietà di DSL tale modello.  
  
-   Se non si utilizza una direttiva generato da un progetto DSL, è necessario includere anche le operazioni seguenti.  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   Utilizzare `this.ModelBus` per ottenere l'accesso a di ModelBus.  
  
## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Procedura dettagliata: Verifica di un modello di testo che utilizza ModelBus  
 In questa procedura dettagliata, si eseguire la procedura seguente:  
  
1.  Creare due DSL. Un linguaggio DSL, il *Consumer*, ha un `ModelBusReference` proprietà che è possibile fare riferimento a DSL, il *Provider*.  
  
2.  Creare due schede di ModelBus nel Provider: uno per l'accesso da modelli di testo, l'altro per il codice normale.  
  
3.  Creare modelli di istanza del DSL in un unico progetto sperimentale.  
  
4.  Impostare una proprietà di dominio in un modello in modo che punti al modello di altri.  
  
5.  Scrivere un gestore di doppio clic che apre il modello a cui punta.  
  
6.  Scrivere un modello di testo che è possibile caricare il primo modello, il riferimento al modello di altri e leggere il modello di altri.  
  
#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Creare un linguaggio DSL che sia accessibile a ModelBus  
  
1.  Creare una nuova soluzione DSL. Per questo esempio, selezionare il modello di soluzione del flusso attività. Impostare il nome della lingua `MBProvider` e l'estensione del nome file ".provide".  
  
2.  Il diagramma della definizione DSL, fare doppio clic su una parte vuota del diagramma che non è presente nella parte superiore e quindi fare clic su **abilitare Modelbus**.  
  
    -   Se non viene visualizzato **abilitare Modelbus**, è necessario scaricare e installare l'estensione VMSDK ModelBus. Si trova nel sito VMSDK: [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
3.  Nel **abilitare Modelbus** nella finestra di dialogo **esporre questo DSL per il ModelBus**e quindi fare clic su **OK**.  
  
     Un nuovo progetto, `ModelBusAdapter`, viene aggiunto alla soluzione.  
  
 È ora disponibile un linguaggio DSL che è possibile accedere tramite modelli di testo tramite ModelBus. I riferimenti a esso possono essere risolti nel codice di comandi, i gestori eventi o regole, che operano nel dominio applicazione dell'editor del file modello. Tuttavia, i modelli di testo eseguiti in un AppDomain separato e non possono accedere a un modello quando viene modificato. Se si desidera accedere ModelBus riferimenti a questo DSL da un modello di testo, è necessario disporre di un oggetto ModelBusAdapter separato.  
  
#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Per creare un adattatore ModelBus configurato per i modelli di testo  
  
1.  In Esplora risorse, copiare e incollare la cartella che contiene ModelBusAdapter.csproj.  
  
     Nome della cartella T4ModelBusAdapter.  
  
     Rinominare il file di progetto T4ModelBusAdapter.csproj.  
  
2.  In Esplora soluzioni, aggiungere la soluzione MBProvider T4ModelBusAdapter. Pulsante destro del mouse sul nodo della soluzione, scegliere **Aggiungi**, quindi fare clic su **progetto esistente**.  
  
3.  Pulsante destro del mouse sul nodo del progetto T4ModelBusAdapter e quindi fare clic su proprietà. Nella finestra delle proprietà del progetto, modificare il **nome Assembly** e **Default Namespace** a `Company.MBProvider.T4ModelBusAdapters`.  
  
4.  In ogni file *.tt T4ModelBusAdapter, inserire "T4" l'ultima parte dello spazio dei nomi, in modo che la riga è simile al seguente.  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  Nel `DslPackage` del progetto, aggiungere un riferimento al progetto `T4ModelBusAdapter`.  
  
6.  In DslPackage\source.extension.tt, aggiungere la riga seguente sotto `<Content>`.  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  Nel `T4ModelBusAdapter` del progetto, aggiungere un riferimento a: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  Open T4ModelBusAdapter\AdapterManager.tt:  
  
    1.  Modificare la classe di base di AdapterManagerBase e impostarla su <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>. Questa parte del file è ora simile al seguente.  
  
        ```  
        namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters  
        {  
            /// <summary>  
            /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer  
            /// </summary>  
            public partial class <#= dslName #>AdapterManagerBase   
            : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager  
            {  
  
        ```  
  
    2.  Verso la fine del file, inserire il seguente attributo supplementare davanti classe AdapterManager.  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Il risultato è simile al seguente.  
  
        ```  
        /// <summary>  
        /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter  
        /// </summary>  
        [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]  
        [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]  
        [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]  
        [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]  
        public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase  
        {  
        }  
  
        ```  
  
9. Fare clic su **Trasforma tutti i modelli** nella barra del titolo della soluzione Esplora.  
  
10. Ricompilare la soluzione. Premere F5.  
  
11. Verificare che funzioni DSL premendo F5. Nel progetto sperimentale aprire `Sample.provider`. Chiudere l'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 I riferimenti di ModelBus a questo DSL ora possono essere risolti nei modelli di testo e anche nel codice.  
  
#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Creare un linguaggio DSL con una proprietà di dominio di riferimento ModelBus  
  
1.  Creare un linguaggio DSL di nuovo usando il modello di soluzione Language minimo. Denominare la lingua MBConsumer e impostare l'estensione del nome file ".consume".  
  
2.  Nel progetto DSL, aggiungere un riferimento all'assembly MBProvider DSL. Fare doppio clic su `MBConsumer\Dsl\References` e quindi fare clic su **Aggiungi riferimento**. Nel **Sfoglia** , individuare`MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     In questo modo è possibile creare codice che usa il linguaggio specifico di dominio. Se si desidera creare riferimenti a diversi DSL, aggiungerli anche.  
  
3.  Nel diagramma definizione DSL, il pulsante destro del diagramma e quindi fare clic su **abilitare ModelBus**. Nella finestra di dialogo, selezionare **abilitare questo DSL utilizzare il ModelBus**.  
  
4.  Nella classe `ExampleElement`, aggiungere una nuova proprietà dominio `MBR`e nella finestra Proprietà impostare il tipo `ModelBusReference`.  
  
5.  Il pulsante destro la proprietà di dominio nel diagramma e quindi fare clic su **oggetto ModelBusReference modifica specifiche proprietà**. Nella finestra di dialogo, selezionare **un elemento del modello**.  
  
     Impostare il filtro della finestra di dialogo file per le operazioni seguenti.  
  
     `Provider File|*.provide`  
  
     La sottostringa dopo "&#124;" è un filtro per la finestra di dialogo di selezione file. È possibile impostarlo per consentire tutti i file utilizzando *.\*  
  
     Nel **il tipo di elemento del modello** elenco, immettere i nomi di uno o più dominio classi nel provider DSL (ad esempio, Company.MBProvider.Task). Possono essere classi astratte. Se si lascia vuoto l'elenco, l'utente può impostare il riferimento a qualsiasi elemento.  
  
6.  Chiudere la finestra di dialogo e **Trasforma tutti i modelli**.  
  
 È stato creato un linguaggio DSL che può contenere riferimenti agli elementi in un altro linguaggio DSL.  
  
#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Creare un riferimento ModelBus a un altro file nella soluzione  
  
1.  Nella soluzione MBConsumer, premere CTRL + F5. Un'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene aperto nel **MBConsumer\Debugging** progetto.  
  
2.  Aggiungere una copia di Sample.provide per il **MBConsumer\Debugging** progetto. Ciò è necessario perché un riferimento ModelBus deve fare riferimento a un file nella stessa soluzione.  
  
    1.  Fare clic sul progetto debug, scegliere **Aggiungi**, quindi fare clic su **elemento esistente**.  
  
    2.  Nel **Aggiungi elemento** finestra di dialogo, impostare il filtro su **tutti i file (\*.\*)** .  
  
    3.  Passare a `MBProvider\Debugging\Sample.provide` e quindi fare clic su **Aggiungi**.  
  
3.  Aprire `Sample.consume`.  
  
4.  Fare clic su una forma di esempio e nella finestra Proprietà fare clic su **[…]**  nella proprietà MBR. Nella finestra di dialogo, fare clic su **Sfoglia** e selezionare `Sample.provide`. Nella finestra di elementi, espandere il tipo di attività e selezionare uno degli elementi.  
  
5.  Salvare il file.  
  
     (Non chiudere ancora l'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].)  
  
 È stato creato un modello che contiene un riferimento ModelBus a un elemento in un altro modello.  
  
#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Risolvere un riferimento di ModelBus in un modello di testo  
  
1.  Nell'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], aprire un file di modello di testo di esempio. Impostare il relativo contenuto, come indicato di seguito.  
  
    ```  
    <#@ template debug="true" hostspecific="true" language="C#"  
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="Company.MBProvider" #>  
    <#  
      // Property provided by the Consumer directive processor:  
      ExampleModel consumerModel = this.ExampleModel;   
      // Iterate through Consumer model, listing the elements:  
      foreach (ExampleElement element in consumerModel.Elements)  
      {  
    #>  
       <#= element.Name #>   
    <#  
        if (element.MBR != null)  
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))  
      {   
              // If we allowed multiple types or DSLs in the MBR, discover type here.  
        Task task = adapter.ResolveElementReference<Task>(element.MBR);  
    #>  
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>  
    <#  
          }  
      }  
    #>  
  
    ```  
  
     È importante tenere presente i punti seguenti:  
  
    1.  Il `hostSpecific` e `inherits` gli attributi del `template` direttiva deve essere impostata.  
  
    2.  Il modello consumer avviene nel modo consueto tramite il processore di direttiva che è stato generato in tale linguaggio DSL.  
  
    3.  Le direttive di importazione e di assembly devono essere in grado di accedere a ModelBus e i tipi di provider DSL.  
  
    4.  Se si conosce MBR molti sono collegate allo stesso modello, è preferibile chiamare CreateAdapter solo una volta.  
  
2.  Salvare il modello. Verificare che il file di testo risultante è simile al seguente.  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Risolvere un riferimento di ModelBus in un gestore movimenti  
  
1.  Chiudere l'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], se è in esecuzione.  
  
2.  Aggiungere un file denominato MBConsumer\Dsl\Custom.cs e impostarne il contenuto per le operazioni seguenti.  
  
    ```  
  
    namespace Company.MB2Consume  
    {  
      using Microsoft.VisualStudio.Modeling.Integration;  
      using Company.MB3Provider;  
  
      public partial class ExampleShape  
      {  
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)  
        {  
          base.OnDoubleClick(e);  
          ExampleElement element = this.ModelElement as ExampleElement;  
          if (element.MBR != null)  
          {  
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;  
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))  
            {  
              Task task = adapter.ResolveElementReference<Task>(element.MBR);  
              // Open a window on this model:  
              ModelBusView view = adapter.GetDefaultView();  
              view.Show();  
              view.SetSelection(element.MBR);  
            }  
          }  
        }  
      }  
    }  
  
    ```  
  
3.  Premere CTRL+F5.  
  
4.  Nell'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]aprire `Debugging\Sample.consume`.  
  
5.  Fare doppio clic su una forma.  
  
     Se è stata impostata la MBR in quell'elemento, il modello di cui viene fatto riferimento viene aperto e si seleziona l'elemento a cui fa riferimento.  
  
## <a name="see-also"></a>Vedere anche  
 [Integrazione di modelli tramite Modelbus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
