---
title: Integrazione di modelli tramite Modelbus di Visual Studio | Documenti Microsoft
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
ms.openlocfilehash: 92be17ab117a1c76456180cbb40a9b1d77f9181c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="integrating-models-by-using-visual-studio-modelbus"></a>Integrazione di modelli tramite ModelBus di Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus fornisce un metodo per la creazione di collegamenti tra i modelli e da altri strumenti nei modelli. Ad esempio, è stato possibile collegare i modelli di linguaggio specifico di dominio (DSL) e i modelli UML. È anche possibile creare un set integrato di DSL.  
  
 ModelBus consente di creare un riferimento univoco a un modello o a un elemento specifico all'interno di un modello. Questo riferimento può essere archiviato all'esterno del modello, ad esempio in un elemento in un altro modello. Quando, ad esempio, in un momento successivo uno strumento vuole ottenere l'accesso all'elemento, l'infrastruttura ModelBus caricherà il modello appropriato e restituirà l'elemento. Se si vuole, è possibile mostrare il modello all'utente. Se non è possibile accedere al file nel percorso precedente, ModelBus chiederà all'utente di trovarlo. Se l'utente trova il file, ModelBus correggerà tutti i riferimenti al file in questione.  
  
> [!NOTE]
>  Nell'implementazione di ModelBus di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] corrente, i modelli collegati devono essere elementi collocati nella stessa soluzione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Per altre informazioni e per il codice di esempio, vedere:  
  
-   [Procedura: Aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md)  
  
-   [SDK di modellazione per Visual Studio](http://www.microsoft.com/download/details.aspx?id=40754)  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
##  <a name="provide"></a>Accesso a un linguaggio DSL  
 Prima di poter creare un riferimento ModelBus a un modello o ai relativi elementi, è necessario definire un ModelBusAdapter per il linguaggio specifico di dominio. Il modo più facile prevede l'uso dell'estensione ModelBus di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che aggiunge comandi alla finestra di progettazione del linguaggio specifico di dominio.  
  
###  <a name="expose"></a>Per esporre una definizione DSL al Bus di modelli  
  
1.  Scaricare e installare l'estensione ModelBus di Visual Studio, se non è già installata. Per ulteriori informazioni, vedere [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
2.  Aprire il file di definizione del linguaggio specifico di dominio. Fare doppio clic nell'area di progettazione e quindi fare clic su **abilitare Modelbus**.  
  
3.  Nella finestra di dialogo, scegliere **si desidera esporre questo DSL per il ModelBus**. È possibile scegliere entrambe le opzioni se si vuole che il linguaggio specifico di dominio esponga i propri modelli e usi riferimenti ad altri modelli.  
  
4.  Fare clic su **OK**. Un nuovo progetto "ModelBusAdapter" verrà aggiunto alla soluzione relativa al linguaggio specifico di dominio.  
  
5.  Se si vuole accedere al linguaggio specifico di dominio da un modello di testo, è necessario modificare il file AdapterManager.tt nel nuovo progetto. Ignorare questo passaggio se si vuole accedere al linguaggio specifico di dominio da altro codice, ad esempio comandi e gestori di eventi. Per ulteriori informazioni, vedere [utilizzando ModelBus di Visual Studio in un modello di testo](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
    1.  Modificare la classe di base di AdapterManagerBase e impostarla su <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
    2.  Verso la fine del file, inserire questo attributo aggiuntivo davanti alla classe AdapterManager:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
    3.  Nel progetto i riferimenti dell'oggetto ModelBusAdapter, aggiungere **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**.  
  
     Se si vuole accedere al linguaggio specifico di dominio sia da modelli di testo che da altro codice, sono necessari due adattatori, uno modificato e uno non modificato.  
  
6.  Fare clic su **Trasforma tutti i modelli**.  
  
7.  Ricompilare la soluzione.  
  
 Per ModelBus sarà ora possibile aprire istanze di questo linguaggio specifico di dominio.  
  
 Nella cartella `ModelBusAdapters\bin\*` sono contenuti gli assembly compilati dal progetto `Dsl` e dal progetto `ModelBusAdapters`. Per fare riferimento a questo linguaggio specifico di dominio da un altro linguaggio specifico di dominio, è necessario importare questi assembly.  
  
### <a name="making-sure-that-elements-can-be-referenced"></a>Verificare che sia possibile fare riferimento agli elementi  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Gli adapter di ModelBus utilizzano il guid di un elemento per identificarlo, per impostazione predefinita. Questi identificatori devono quindi essere persistenti nel file del modello.  
  
##### <a name="to-ensure-that-element-ids-are-persisted"></a>Per assicurarsi che gli ID degli elementi siano persistenti  
  
1.  Aprire il file DslDefinition.dsl.  
  
2.  In Esplora DSL espandere **il comportamento di serializzazione Xml**, quindi **dati della classe**.  
  
3.  Per ogni classe per la quale si vogliono creare riferimenti a ModelBus:  
  
     Fare clic sul nodo della classe e nella finestra Proprietà, accertarsi che **Id serializzare** è impostato su `true`.  
  
 In alternativa, se per identificare gli elementi si preferisce usare i nomi di elementi anziché i GUID, è possibile eseguire l'override di parti degli adattatori generati. Eseguire l'override dei metodi seguenti nella classe Adapter:  
  
-   Eseguire l'override di `GetElementId` affinché venga restituito l'identificatore che si vuole usare. Questo metodo viene chiamato quando vengono creati i riferimenti.  
  
-   Eseguire l'override di `ResolveElementReference` per individuare l'elemento corretto da un riferimento ModelBus  
  
##  <a name="editRef"></a>L'accesso a un linguaggio DSL da un altro linguaggio DSL  
 È possibile archiviare riferimenti ModelBus in una proprietà di dominio in un linguaggio specifico di dominio ed è possibile scrivere codice personalizzato per usarli. È anche possibile consentire all'utente di creare un riferimento ModelBus selezionando un file di modello e un elemento al suo interno.  
  
 Per abilitare un linguaggio DSL per l'utilizzo di riferimenti a un altro linguaggio DSL, è necessario innanzitutto renderlo un *consumer* di bus di modelli di riferimento.  
  
#### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>Per consentire a un linguaggio specifico di dominio di usare riferimenti a un linguaggio specifico di dominio esposto  
  
1.  Nel diagramma definizione DSL, fare doppio clic sulla parte principale del diagramma e quindi fare clic su **abilitare Modelbus**.  
  
2.  Nella finestra di dialogo, selezionare **si desidera abilitare questo modello utilizzare riferimenti di bus del modello**.  
  
3.  Nel progetto DSL del linguaggio specifico di dominio usato aggiungere gli assembly seguenti ai riferimenti del progetto. Sarà possibile trovare questi assembly (file con estensione dll) nel ModelBusAdapter\bin\\* directory della DSL esposto.  
  
    -   L'assembly DSL esposto, ad esempio **Fabrikam.FamilyTree.Dsl.dll**  
  
    -   Il modello esposto del bus di assembly dell'adattatore, ad esempio **Fabrikam.FamilyTree.ModelBusAdapter.dll**  
  
4.  Aggiungere gli assembly .NET seguenti ai riferimenti del progetto del progetto DSL usato.  
  
    1.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
    2.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**  
  
#### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>Per archiviare un riferimento ModelBus in una proprietà di dominio  
  
1.  Nella definizione DSL del linguaggio specifico di dominio usato, aggiungere una proprietà di dominio a una classe di dominio e impostarne il nome.  
  
2.  Nella proprietà finestra, con la proprietà del dominio selezionata, imposta **tipo** a `ModelBusReference`.  
  
 In questa fase, il codice programma può impostare il valore della proprietà, ma nella finestra Proprietà è di sola lettura.  
  
 È possibile consentire agli utenti di impostare la proprietà con un editor di riferimenti ModelBus specifico. Sono disponibili due versioni dell'editor o *selezione:* uno che consente agli utenti di scegliere un file di modello e l'altro consente agli utenti di scegliere un file di modello e un elemento all'interno del modello.  
  
#### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>Per consentire all'utente di impostare un riferimento ModelBus in una proprietà di dominio  
  
1.  Il pulsante destro la proprietà di dominio e quindi fare clic su **oggetto ModelBusReference modifica specifiche proprietà**. Verrà visualizzata una finestra di dialogo. Si tratta di *selezione Bus modello*.  
  
2.  Selezionare l'appropriata **tipo di oggetto ModelBusReference**: a un modello o a un elemento all'interno di un modello.  
  
3.  Nella stringa di filtro della finestra di dialogo File, immettere una stringa come `Family Tree files |*.ftree`. Sostituire l'estensione di file del linguaggio specifico di dominio esposto.  
  
4.  Se si sceglie di fare riferimento a un elemento in un modello, è possibile aggiungere un elenco di tipi che possono essere selezionati dall'utente, ad esempio Company.FamilyTree.Person.  
  
5.  Fare clic su **OK**, quindi fare clic su **Trasforma tutti i modelli** nella barra degli strumenti di Esplora soluzioni.  
  
    > [!WARNING]
    >  Se non è stato selezionata un'entità o un modello valido, il pulsante OK non avrà alcun effetto sebbene possa sembrare abilitato.  
  
6.  Se è stato specificato un elenco di tipi di destinazione, come Company.FamilyTree.Person, sarà necessario aggiungere un riferimento di assembly al progetto DSL, facendo riferimento alla DLL del DSL di destinazione, ad esempio Company.FamilyTree.Dsl.dll.  
  
#### <a name="to-test-a-model-bus-reference"></a>Per testare un riferimento ModelBus  
  
1.  Compilare entrambi i DSL esposto e utilizzato.  
  
2.  Eseguire uno dei DSL in modalità sperimentale premendo F5 o CTRL+F5.  
  
3.  Nel progetto di debug nell'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], aggiungere i file che sono istanze di ogni DSL.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus solo può risolvere i riferimenti per i modelli di elementi nello stesso [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione. Ad esempio, non è possibile creare un riferimento a un file di modello in un'altra parte del file system.  
  
4.  Creare alcuni elementi e collegamenti nell'istanza del DSL esposto e salvarlo.  
  
5.  Aprire un'istanza del DSL utilizzato e selezionare un elemento del modello contenente una proprietà di riferimento ModelBus.  
  
6.  Nella finestra Proprietà fare doppio clic sulla proprietà di riferimento ModelBus. Verrà visualizzata la finestra di dialogo del selettore.  
  
7.  Fare clic su **Sfoglia** e selezionare l'istanza di DSL esposto.  
  
     Il selettore consentirà inoltre di scegliere un elemento nel modello, se è stato specificato il tipo di riferimento ModelBus specifico dell'elemento.  
  
## <a name="creating-references-in-program-code"></a>Creare riferimenti nel codice programma  
 Per archiviare un riferimento a un modello o a un elemento all'interno di un modello, è necessario creare un `ModelBusReference`. Esistono due tipi di `ModelBusReference`: riferimenti a modelli e riferimenti a elementi.  
  
 Per creare un riferimento a un modello, occorre l'AdapterManager del DSL di cui il modello costituisce un'istanza e il nome file o elemento di progetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] del modello.  
  
 Per creare un riferimento a un elemento, occorre un adattatore per il file di modello e l'elemento a cui si vuole fare riferimento.  
  
> [!NOTE]
>  Con ModelBus di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è possibile creare riferimenti solo a elementi appartenenti alla stessa soluzione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="import-the-exposed-dsl-assemblies"></a>Importare gli assembly DSL esposti  
 Nel progetto utilizzato, aggiungere i riferimenti di progetto al DSL e agli assembly ModelBusAdapter del DSL esposto.  
  
 Si supponga ad esempio di voler archiviare i riferimenti ModelBus in elementi di un DSL MusicLibrary. I riferimenti ModelBus faranno riferimento agli elementi del DSL FamilyTree. Nel progetto `Dsl` della soluzione MusicLibrary, nel nodo Riferimenti aggiungere i riferimenti agli assembly seguenti:  
  
-   Fabrikam.FamilyTree.Dsl.dll: DSL esposto.  
  
-   Fabrikam.FamilyTree.ModelBusAdapters.dll: adattatore ModelBus del DSL esposto.  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0  
  
 Questi assembly sono disponibili nel progetto `ModelBusAdapters` del DSL esposto, in `bin\*`.  
  
 Nel file di codice in cui verranno creati i riferimenti, sarà necessario importare gli spazi dei nomi seguenti:  
  
```  
// The namespace of the DSL you want to reference:  
using Fabrikam.FamilyTree;  // Exposed DSL  
using Fabrikam.FamilyTree.ModelBusAdapters;  
using Microsoft.VisualStudio.Modeling.Integration;  
using System.Linq;  
...  
```  
  
### <a name="to-create-a-reference-to-a-model"></a>Per creare un riferimento a un modello  
 Per creare un riferimento a un modello, accedere all'AdapterManager per il DSL esposto e usarlo per creare un riferimento al modello. È possibile specificare un percorso di file o un elemento `EnvDTE.ProjectItem`.  
  
 Da AdapterManager è possibile ottenere un adattatore, che fornisce accesso ai singoli elementi nel modello.  
  
> [!NOTE]
>  È necessario eliminare l'adattatore dopo avere finito di usarlo. Il modo più pratico per eseguire questa operazione, è usare un'istruzione `using`. Questa condizione è illustrata nell'esempio seguente.  
  
```  
// The file path of a model instance of the FamilyTree DSL:  
string targetModelFile = "TudorFamilyTree.ftree";  
// Get the ModelBus service:  
IModelBus modelBus =   
    this.Store.GetService(typeof(SModelBus)) as IModelBus;  
// Get an adapterManager for the target DSL:  
FamilyTreeAdapterManager manager =   
    (modelbus.GetAdapterManager(FamilyTreeAdapter.AdapterId)   
     as FamilyTreeAdapterManager;  
// or: (modelBus.FindAdapterManagers(targetModelFile).First())  
// or could provide an EnvDTE.ProjectItem  
  
// Create a reference to the target model:  
// NOTE: the target model must be a file in this project.  
ModelBusReference modelReference =  
     manager.CreateReference(targetModelFile);  
// or can use an EnvDTE.ProjectItem instead of the filename  
  
// Get the root element of this model:  
using (FamilyTreeAdapter adapter =   
     modelBus.CreateAdapter(modelReference) as FamilyTreeAdapter)  
{  
  FamilyTree modelRoot = adapter.ModelRoot;  
  // Access elements under the root in the usual way:  
  foreach (Person p in modelRoot.Persons) {...}  
  // You can create adapters for individual elements:  
  ModelBusReference elementReference =  
     adapter.GetElementReference(person);  
  ...  
} // Dispose adapter  
  
```  
  
 Se si vuole poter riutilizzare `modelReference` in un secondo momento, è possibile archiviarlo in una proprietà di dominio con un `ModelBusReference` di tipo esterno.  
  
```  
using Transaction t = this.Store.TransactionManager  
    .BeginTransaction("keep reference"))  
{  
  artist.FamilyTreeReference = modelReference;  
  t.Commit();  
}  
```  
  
 Per consentire agli utenti di modificare questa proprietà di dominio, usare `ModelReferenceEditor` come parametro nell'attributo Editor. Per ulteriori informazioni, vedere [consentono all'utente di modificare un riferimento](#editRef).  
  
### <a name="to-create-a-reference-to-an-element"></a>Per creare un riferimento a un elemento  
 L'adattatore creato per il modello può essere usato anche per creare e risolvere riferimenti.  
  
```  
// person is an element in the FamilyTree model:  
ModelBusReference personReference =   
  adapter.GetElementReference(person);  
```  
  
 Se si vuole poter riutilizzare `elementReference` in un secondo momento, è possibile archiviarlo in una proprietà di dominio con un `ModelBusReference` di tipo esterno. Per consentire agli utenti di modificarla, usare `ModelElementReferenceEditor` come parametro nell'attributo Editor. Per ulteriori informazioni, vedere [consentono all'utente di modificare un riferimento](#editRef).  
  
### <a name="resolving-references"></a>Risolvere i riferimenti  
 Se è disponibile un `ModelBusReference` (MBR), è possibile ottenere il modello o l'elemento del modello a cui fa riferimento. Se l'elemento è presentato in un diagramma o in un'altra visualizzazione, è possibile aprire la visualizzazione e selezionare l'elemento.  
  
 È possibile creare un adattatore da un MBR. Dall'adattatore è quindi possibile ottenere la radice del modello. È anche possibile risolvere gli MBR che fanno riferimento a elementi specifici nel modello.  
  
```  
using Microsoft.VisualStudio.Modeling.Integration; ...  
ModelBusReference elementReference = ...;  
  
// Get the ModelBus service:  
IModelBus modelBus =   
    this.Store.GetService(typeof(SModelBus)) as IModelBus;  
// Use a model reference or an element reference  
// to obtain an adapter for the target model:  
using (FamilyTreeAdapter adapter =   
   modelBus.CreateAdapter(elementReference) as FamilyTreeAdapter)  
   // or CreateAdapter(modelReference)  
{  
  // Get the root of the model:  
  FamilyTree tree = adapter.ModelRoot;  
  
  // Get a model element:  
  MyDomainClass mel =  
    adapter.ResolveElementReference<MyDomainClass>(elementReference);  
  if (mel != null) {...}  
  
  // Get the diagram or other view, if there is one:  
  ModelBusView view = adapter.GetDefaultView();  
  if (view != null)   
  {  
   view.Open();  
   // Display the diagram:  
   view.Show();   
   // Attempt to select the shape that presents the element:  
   view.SetSelection(elementReference);  
  }  
} // Dispose the adapter.  
```  
  
##### <a name="to-resolve-modelbus-references-in-a-text-template"></a>Per risolvere riferimenti ModelBus in un modello di testo  
  
1.  Il DSL a cui si vuole accedere deve disporre di un adattatore ModelBus configurato per l'accesso dai modelli di testo. Per ulteriori informazioni, vedere [che fornisce accesso a un linguaggio DSL](#provide).  
  
2.  In genere, si accederà a un DSL di destinazione tramite un riferimento di ModelBus (MBR) archiviato in un DSL di origine. Il modello include pertanto la direttiva del DSL di origine, più il codice per risolvere l'MBR. Per ulteriori informazioni sui modelli di testo, vedere [la generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
    ```  
    <#@ template debug="true" hostspecific="true"   
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "System.Core" #>  
    <#@ assembly name = "Company.CompartmentDragDrop.Dsl.dll" #>  
    <#@ assembly name = "Company.CompartmentDragDrop.ModelBusAdapter.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="Company.CompartmentDragDrop" #>  
    <#@ import namespace="Company.CompartmentDragDrop.ModelBusAdapters" #>  
    <# // Get source root from directive processor:  
      ExampleModel source = this.ExampleModel;   
      // This DSL has a MBR in its root:  
    using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as ModelBusAdapter)   
      {  
      ModelBusAdapterManager manager = this.ModelBus.FindAdapterManagers(this.Host.ResolvePath("Sample.compDD1")).FirstOrDefault();  
      ModelBusReference modelReference =  
        manager.CreateReference(this.Host.ResolvePath("Sample.compDD1"));  
  
      // Get the root element of this model:  
      using (CompartmentDragDropAdapter adapter =   
         this.ModelBus.CreateAdapter(modelReference) as CompartmentDragDropAdapter)  
      {  
        ModelRoot root = adapter.ModelRoot;  
    #>  
    [[<#= root.Name #>]]  
    <#  
      }  
    #>  
  
    ```  
  
 Per ulteriori informazioni e una procedura dettagliata, vedere [utilizzando ModelBus di Visual Studio in un modello di testo](../modeling/using-visual-studio-modelbus-in-a-text-template.md)  
  
## <a name="serializing-a-modelbusreference"></a>Eseguire la serializzazione di un ModelBusReference  
 Se si vuole archiviare un `ModelBusReference` (MBR) sotto forma di stringa, è possibile serializzarlo:  
  
```  
string serialized = modelBus.SerializeReference(elementReference);  
// Store it anywhere, then get it back again:  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, null);  
```  
  
 Un MBR serializzato in questo modo è indipendente dal contesto. Se si usa un semplice adattatore ModelBus basato su file, l'MBR contiene un percorso di file assoluto. Questo è sufficiente se i file di modello dell'istanza non verranno spostati. Tuttavia, in genere i file di modello costituiscono elementi di un progetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È quindi probabile che gli utenti abbiano l'esigenza di spostare l'intero progetto in altre parti del file system e di poter eseguire il controllo del codice sorgente del progetto e aprirlo in computer diversi. I nomi dei percorsi devono quindi essere serializzati in relazione al percorso del progetto contenente i file.  
  
### <a name="serializing-relative-to-a-specified-file-path"></a>Eseguire la serializzazione in relazione a un percorso di file specificato  
 Un `ModelBusReference` contiene un `ReferenceContext`, ovvero un dizionario in cui è possibile archiviare informazioni, ad esempio il percorso del file in relazione al quale deve essere serializzato.  
  
 Per eseguire la serializzazione in relazione a un percorso:  
  
```  
elementReference.ReferenceContext.Add(  
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,   
   currentProjectFilePath);  
string serialized = modelBus.SerializeReference(elementReference);  
```  
  
 Per recuperare il riferimento dalla stringa:  
  
```  
ReferenceContext context = new ReferenceContext();  
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,  
    currentProjectFilePath);  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, context);  
```  
  
### <a name="modelbusreferences-created-by-other-adapters"></a>Riferimenti ModelBus creati da altri adattatori  
 Le informazioni seguenti risultano utili per la creazione di un adattatore personalizzato.  
  
 Un `ModelBusReference` (MBR) è costituito da due parti: l'intestazione dell'MBR, che è deserializzata da ModelBus e una parte specifica dell'adattatore gestita dal gestore dell'adattatore specifico. In questo modo è possibile specificare il formato di serializzazione dell'adattatore personalizzato. È ad esempio possibile fare riferimento a un database anziché a un file oppure archiviare informazioni aggiuntive nel riferimento dell'adattatore. L'adattatore può inserire informazioni aggiuntive in `ReferenceContext`.  
  
 Quando si esegue la deserializzazione di un MBR, è necessario fornire un ReferenceContext che viene quindi archiviato nell'oggetto MBR. Quando si esegue la serializzazione di un MBR, il ReferenceContext archiviato viene usato dall'adattatore per generare la stringa. La stringa deserializzata non contiene tutte le informazioni incluse in ReferenceContext. Ad esempio, nell'adattatore semplice basato su file, ReferenceContext contiene un percorso del file radice che non è archiviato nella stringa MBR serializzata.  
  
 L'MBR viene deserializzato in due fasi:  
  
-   `ModelBusReferencePropertySerializer` è il serializzatore standard che gestisce l'intestazione MBR. Usa il contenitore delle proprietà `SerializationContext` DSL standard che è archiviato in `ReferenceContext` tramite la chiave `ModelBusReferencePropertySerializer.ModelBusLoadContextKey`. In particolare, `SerializationContext` deve contenere un'istanza di `ModelBus`.  
  
-   L'adattatore ModelBus gestisce la parte specifica dell'adattatore dell'MBR. Può usare le informazioni aggiuntive archiviate nel ContextReference dell'MBR. L'adapter semplice basato su file mantiene i percorsi di file radice utilizzando i tasti `FilePathLoadContextKey` e `FilePathSaveContextKey`.  
  
     Un riferimento a un adattatore in un file di modello è deserializzato solo quando viene usato.  
  
## <a name="to-create-a-model"></a>Per creare un modello  
  
### <a name="creating-opening-and-editing-a-model"></a>Creazione, apertura e modifica di un modello  
 Il frammento seguente è estratto dall'esempio relativo a State Machine nel sito Web VMSDK. Viene illustrato l'uso di ModelBusReferences per creare e aprire un modello e per ottenere il diagramma associato al modello.  
  
 In questo esempio il nome del DSL di destinazione è StateMachine. Diversi nomi sono derivati da esso, ad esempio il nome della classe del modello e il nome dell'adattatore ModelBus.  
  
```  
using Fabrikam.StateMachine.ModelBusAdapters;   
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Integration;  
using Microsoft.VisualStudio.Modeling.Integration.Shell;  
using Microsoft.VisualStudio.Modeling.Shell;  
...  
// Create a new model.  
ModelBusReference modelReference =   
   StateMachineAdapterManager    .CreateStateMachineModel(modelName, fileName);  
//Keep reference of new model in this model.  
using (Transaction t = ...)  
{  
  myModelElement.ReferenceProperty = modelReference;  
  t.Commit();  
}  
// Get the ModelBus service from Visual Studio.  
IModelBus modelBus = Microsoft.VisualStudio.Shell.Package.  
    GetGlobalService(typeof(SModelBus)) as IModelBus;  
// Get a modelbus adapter on the new model.  
ModelBusAdapter modelBusAdapter;  
modelBus.TryCreateAdapter(modelReference,   
    this.ServiceProvider, out modelBusAdapter);  
using (StateMachineAdapter adapter =   
      modelBusAdapter as StateMachineAdapter)  
{  
    if (adapter != null)  
    {  
        // Obtain a Diagram from the adapter.  
        Diagram targetDiagram =   
           ((StandardVsModelingDiagramView)  
                 adapter.GetDefaultView()  
            ).Diagram;  
  
        using (Transaction t =   
             targetDiagram.Store.TransactionManager  
                .BeginTransaction("Update diagram"))  
        {  
            DoUpdates(targetDiagram);  
            t.Commit();  
        }  
  
        // Display the new diagram.  
        adapter.GetDefaultView().Show();  
    }  
}  
```  
  
## <a name="validating-references"></a>Convalidare i riferimenti  
 BrokenReferenceDetector esegue il test di tutte le proprietà di dominio in un archivio che può contenere riferimenti ModelBus. Chiama l'azione specificata ogni volta che trova un'azione. Questo è particolarmente utile per i metodi di convalida. Il metodo di convalida seguente esegue un test sull'archivio nel tentativo di salvare i modelli e segnala i riferimenti interrotti nella finestra degli errori:  
  
```  
[ValidationMethod(ValidationCategories.Save)]  
public void ValidateModelBusReferences(ValidationContext context)  
{  
  BrokenReferenceDetector.DetectBrokenReferences(this.Store,  
    delegate(ModelElement element, // parent of property  
             DomainPropertyInfo property, // identifies property  
             ModelBusReference reference) // invalid reference  
    {   
      context.LogError(string.Format(INVALID_REF_FORMAT,   
             property.Name,   
             referenceState.Name,   
             new ModelBusReferenceTypeConverter().  
                 ConvertToInvariantString(reference)),   
         "Reference",   
         element);  
      });  
}}  
private const string INVALID_REF_FORMAT =   
    "The '{0}' domain property of ths ReferenceState instance "  
  + "named '{1}' contains reference value '{2}' which is invalid";  
```  
  
## <a name="actions-performed-by-the-modelbus-extension"></a>Azioni eseguite dall'estensione ModelBus  
 Le informazioni seguenti non sono essenziali ma potrebbero risultare utili se si fa un uso intensivo di ModelBus.  
  
 L'estensione ModelBus apporta le modifiche seguenti alla soluzione DSL.  
  
 Quando si fa clic sul diagramma della definizione DSL, fare clic su **Modelbus abilitare**, quindi selezionare **abilitare questo DSL utilizzare il ModelBus**:  
  
-   Nel progetto DSL, viene aggiunto un riferimento a **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
-   Nella definizione DSL viene aggiunto un riferimento di tipo esterno: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`.  
  
     È possibile visualizzare il riferimento in **Esplora DSL**in **tipi di dominio**. Per aggiungere manualmente riferimenti di tipo esterno, fare clic con il pulsante destro del mouse sul nodo radice.  
  
-   Viene aggiunto un nuovo file di modello, **Dsl\GeneratedCode\ModelBusReferencesSerialization.tt**.  
  
 Quando si imposta il tipo di una proprietà di dominio per l'oggetto ModelBusReference e quindi fare doppio clic su proprietà e fare clic su **oggetto ModelBusReference abilitare specifiche proprietà**:  
  
-   Alla proprietà di dominio vengono aggiunti numerosi attributi CLR ed è possibile visualizzarlo nel campo Attributi personalizzati nella finestra Proprietà. In **Dsl\GeneratedCode\DomainClasses.cs**, è possibile visualizzare gli attributi della dichiarazione di proprietà:  
  
    ```  
    [System.ComponentModel.TypeConverter(typeof(  
    Microsoft.VisualStudio.Modeling.Integration.ModelBusReferenceTypeConverter))]  
    [System.ComponentModel.Editor(typeof(  
      Microsoft.VisualStudio.Modeling.Integration.Picker  
      .ModelReferenceEditor // or ModelElementReferenceEditor  
      ), typeof(System.Drawing.Design.UITypeEditor))]  
    [Microsoft.VisualStudio.Modeling.Integration.Picker  
      .SupplyFileBasedBrowserConfiguration  
      ("Choose a model file", "Target model|*.target")]  
    ```  
  
 Scegliendo destro del mouse nel diagramma della definizione DSL, fare clic su **abilitare ModelBus**e selezionare **esporre questo DSL per il ModelBus**:  
  
-   Viene aggiunto un nuovo progetto `ModelBusAdapter` alla soluzione.  
  
-   Al progetto `ModelBusAdapter` viene aggiunto un riferimento a `DslPackage`. `ModelBusAdapter` include un riferimento a `Dsl`.  
  
-   In **DslPackage\source.extention.tt**, `|ModelBusAdapter|` viene aggiunto come componente MEF.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: aprire un modello dal File di codice programma](../modeling/how-to-open-a-model-from-file-in-program-code.md)   
 [Procedura: aggiungere un gestore di trascinamento e rilascio](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Uso di ModelBus di Visual Studio in un modello di testo](../modeling/using-visual-studio-modelbus-in-a-text-template.md)
