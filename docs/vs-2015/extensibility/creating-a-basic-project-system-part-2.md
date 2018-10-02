---
title: Creazione di un sistema di progetto di base, parte 2 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 324eb3c0af582e32318980dac675ac483f86f31f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532392"
---
# <a name="creating-a-basic-project-system-part-2"></a>Creazione di un sistema di progetto di base, parte 2
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [creazione di un sistema di progetto di base, parte 2](https://docs.microsoft.com/visualstudio/extensibility/creating-a-basic-project-system-part-2).  
  
La prima procedura dettagliata in questa serie [creazione di un sistema di progetto di base, parte 1](../extensibility/creating-a-basic-project-system-part-1.md), viene illustrato come creare un sistema di progetto di base. Questa procedura dettagliata si basa sul sistema del progetto di base mediante l'aggiunta di un modello di Visual Studio, una pagina delle proprietà e altre funzionalità. Prima di iniziare questo, è necessario completare la prima procedura dettagliata.  
  
 Questa procedura dettagliata viene illustrato come creare un tipo di progetto che ha il .myproj di estensione nome file progetto. Per completare la procedura dettagliata, non è necessario creare un proprio linguaggio perché la procedura dettagliata Usa il sistema di progetto Visual c# esistente.  
  
 Questa procedura dettagliata illustra come eseguire queste attività:  
  
-   Creare un modello di Visual Studio.  
  
-   Distribuire un modello di Visual Studio.  
  
-   Creare un nodo figlio di tipo di progetto nel **nuovo progetto** nella finestra di dialogo.  
  
-   Abilitare la sostituzione dei parametri nel modello di Visual Studio.  
  
-   Creare una pagina delle proprietà progetto.  
  
> [!NOTE]
>  I passaggi descritti in questa procedura dettagliata si basano su un progetto c#. Tuttavia, fatta eccezione per le specifiche, ad esempio estensioni di file e il codice, è possibile utilizzare gli stessi passaggi per un progetto Visual Basic.  
  
## <a name="creating-a-visual-studio-template"></a>Creazione di un modello di Visual Studio  
 [Creazione di un sistema di progetto di base, parte 1](../extensibility/creating-a-basic-project-system-part-1.md) viene illustrato come creare un modello di progetto di base e aggiungerlo al sistema del progetto. Viene inoltre illustrato come registrare questo modello con Visual Studio usando il <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attributo, che scrive il percorso completo della cartella \Templates\Projects\SimpleProject\ nel Registro di sistema.  
  
 Usando un modello di Visual Studio (file con estensione vstemplate) anziché un modello di progetto di base, è possibile controllare come viene visualizzato il modello nel **nuovo progetto** nella finestra di dialogo e modo in cui vengono sostituiti con i parametri del modello.  Un file con estensione vstemplate è un file XML che descrive la modalità file di origine devono essere incluse quando viene creato un progetto usando il modello di sistema di progetto. Il sistema di progetto stesso viene compilato mediante la raccolta di file con estensione vstemplate e i file di origine in un file con estensione zip e distribuito copiando il file con estensione zip in un percorso noto a Visual Studio. Questo processo è illustrato in dettaglio più avanti in questa procedura dettagliata.  
  
1.  Nelle [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aprire la soluzione SimpleProject creata seguendo [creazione di un sistema di progetto di base, parte 1](../extensibility/creating-a-basic-project-system-part-1.md).  
  
2.  Nel file SimpleProjectPackage.cs, trovare l'attributo ProvideProjectFactory. Sostituire il secondo parametro (il nome di progetto) con un valore null e il quarto parametro (il percorso alla cartella del modello di progetto) con ". \\\NullPath ", come indicato di seguito.  
  
    ```  
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,  
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",  
        ".\\NullPath",  
    LanguageVsTemplate = "SimpleProject")]  
    ```  
  
3.  Aggiungere un file XML denominato SimpleProject.vstemplate nella cartella \Templates\Projects\SimpleProject\.  
  
4.  Sostituire il contenuto di SimpleProject.vstemplate con il codice seguente.  
  
    ```xml  
    <VSTemplate Version="2.0.0" Type="Project"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
      <TemplateData>  
        <Name>SimpleProject Application</Name>  
        <Description>  
            A project for creating a SimpleProject application  
         </Description>  
         <Icon>SimpleProject.ico</Icon>  
         <ProjectType>SimpleProject</ProjectType>  
      </TemplateData>  
      <TemplateContent>  
        <Project File="SimpleProject.myproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
              Program.cs  
          </ProjectItem>  
          <ProjectItem ReplaceParameters="true" OpenInEditor="false">  
             AssemblyInfo.cs  
          </ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
5.  Nel **delle proprietà** finestra, seleziona tutti i cinque file nella cartella \Templates\Projects\SimpleProject\ e impostare il **azione di compilazione** a **ZipProject**.  
  
 ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
 Il \<TemplateData > sezione determina la posizione e l'aspetto del tipo di progetto SimpleProject nel **nuovo progetto** finestra di dialogo, come indicato di seguito:  
  
-   Il \<nome > il modello di progetto applicazione SimpleProject nomi degli elementi.  
  
-   Il \<descrizione > elemento contiene la descrizione che viene visualizzato nei **nuovo progetto** finestra di dialogo quando viene selezionato il modello di progetto.  
  
-   Il \<icona > elemento specifica l'icona visualizzata insieme al tipo di progetto SimpleProject.  
  
-   Il \<ProjectType > nomi di elementi di tipo di progetto nel **nuovo progetto** nella finestra di dialogo. Questo nome sostituisce il parametro name del progetto dell'attributo ProvideProjectFactory.  
  
    > [!NOTE]
    >  Il \<ProjectType > elemento deve corrispondere il `LanguageVsTemplate` argomento del `ProvideProjectFactory` attributo nel file SimpleProjectPackage.cs.  
  
 Il \<TemplateContent > sezione vengono descritti questi file vengono generati quando viene creato un nuovo progetto:  
  
-   SimpleProject.myproj  
  
-   Program.cs  
  
-   AssemblyInfo.cs  
  
 Tutti i tre file `ReplaceParameters` impostata su true, che consente la sostituzione dei parametri.  Il file Program.cs è `OpenInEditor` impostata su true, che fa sì che il file da aprire nell'editor del codice quando viene creato un progetto.  
  
 Per altre informazioni sugli elementi presenti nello schema del modello di Visual Studio, vedere la [riferimenti allo Schema di Visual Studio modello](../extensibility/visual-studio-template-schema-reference.md).  
  
> [!NOTE]
>  Se un progetto ha più di un modello di Visual Studio, ogni modello è in una cartella separata. Ogni file in tale cartella deve contenere il **Build Action** impostata su **ZipProject**.  
  
## <a name="adding-a-minimal-vsct-file"></a>Aggiunta di un File con estensione vsct minimo  
 Visual Studio deve essere eseguito in modalità di installazione per riconoscere un modello di Visual Studio nuovo o modificato. La modalità di installazione richiede un file con estensione vsct sia presente. Pertanto, è necessario aggiungere un file con estensione vsct minimo al progetto.  
  
1.  Aggiungere un file XML denominato SimpleProject.vsct al progetto SimpleProject.  
  
2.  Sostituire il contenuto del file SimpleProject.vsct con il codice seguente.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CommandTable  
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
    </CommandTable>  
    ```  
  
3.  Impostare il **Build Action** di questo file per **VSCTCompile**. È possibile farlo solo nel file con estensione csproj, non nel **proprietà** finestra. Assicurarsi che il **Build Action** di questo file è impostato su **None** a questo punto.  
  
    1.  Il pulsante destro del nodo SimpleProject e quindi fare clic su **SimpleProject.csproj modifica**.  
  
    2.  Nel file con estensione csproj, individuare l'elemento SimpleProject.vsct.  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  Modificare l'azione di compilazione specificando **VSCTCompile**.  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  il file di progetto e chiudere l'editor.  
  
    5.  Salva il nodo SimpleProject, quindi nella **Esplora soluzioni** fare clic su **Ricarica progetto**.  
  
## <a name="examining-the-visual-studio-template-build-steps"></a>Esaminare le istruzioni di compilazione di modelli di Visual Studio  
 Il sistema di compilazione progetto VSPackage Visual Studio in modalità di installazione viene eseguito in genere quando viene modificato il file con estensione vstemplate o viene ricompilato il progetto che contiene il file con estensione vstemplate. È possibile seguire la procedura, impostare il livello di dettaglio di MSBuild alla normalità o versione successiva.  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Espandere la **progetti e soluzioni** nodo e quindi selezionare **compila ed Esegui**.  
  
3.  Impostare **livello di dettaglio output di compilazione progetto MSBuild** al **normale**. Fare clic su **OK**.  
  
4.  Ricompilare il progetto SimpleProject.  
  
 L'istruzione di compilazione per creare il file di progetto con estensione zip dovrebbe essere simile al seguente.  
  
```  
ZipProjects:  
1>  Zipping ProjectTemplates  
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".  
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip  
1>ZipItems:  
1>  Zipping ItemTemplates  
1>  SimpleProject ->  
```  
  
## <a name="deploying-a-visual-studio-template"></a>Distribuzione di un modello di Visual Studio  
 Modelli di Visual Studio non contengono informazioni sul percorso. Pertanto, il file zip del modello deve essere distribuito in un percorso noto a Visual Studio. È in genere il percorso della cartella ProjectTemplates  **\<% LOCALAPPDATA % > \Microsoft\VisualStudio\14.0Exp\ProjectTemplates**.  
  
 Per distribuire la factory di progetto, il programma di installazione deve disporre dei privilegi di amministratore. Distribuisce i modelli sotto il nodo di installazione di Visual Studio: **...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates**.  
  
## <a name="testing-a-visual-studio-template"></a>Test di un modello di Visual Studio  
 Testare la factory di progetto per verificare se crea una gerarchia del progetto usando il modello di Visual Studio.  
  
1.  Reimpostare l'istanza sperimentale di Visual Studio SDK.  
  
     Sul [!INCLUDE[win7](../includes/win7-md.md)]: nel menu Start, individuare il **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools** cartella e quindi selezionare **reimpostare l'istanza di Microsoft Visual Studio sperimentale**.  
  
     Nelle versioni successive di Windows: nella schermata Start di, digitare **ripristinare Microsoft Visual Studio \<versione > istanza sperimentale**.  
  
2.  Viene visualizzata una finestra del prompt dei comandi. Quando vengono visualizzate le parole `Press any key to continue`, fare clic su INVIO. Dopo aver chiuso la finestra, aprire Visual Studio.  
  
3.  Ricompilare il progetto SimpleProject e avviare il debug. Viene visualizzata l'istanza sperimentale.  
  
4.  Nell'istanza sperimentale, creare un progetto SimpleProject. Nel **nuovo progetto** finestra di dialogo **SimpleProject**.  
  
5.  Verrà visualizzata una nuova istanza della SimpleProject.  
  
 ![](../extensibility/media/simpproj2-newproj.png "SimpProj2_NewProj")  
  
 ![](../extensibility/media/simpproj2-myproj.png "SimpProj2_MyProj")  
  
## <a name="creating-a-project-type-child-node"></a>Creazione di un nodo figlio del tipo progetto  
 È possibile aggiungere un nodo figlio a un nodo di tipo di progetto nel **nuovo progetto** nella finestra di dialogo.  Ad esempio, per il tipo di progetto SimpleProject, si potrebbero avere nodi figlio per le applicazioni console, applicazioni di finestra, le applicazioni web e così via.  
  
 I nodi figlio vengono creati alterare il file di progetto e aggiungendo \<OutputSubPath > gli elementi figlio di \<ZipProject > elementi. Quando un modello viene copiato durante la compilazione o la distribuzione, tutti i nodi figlio diventano una sottocartella della cartella dei modelli di progetto.  
  
 In questa sezione viene illustrato come creare un nodo figlio della Console per il tipo di progetto SimpleProject.  
  
1.  Rinominare la cartella \Templates\Projects\SimpleProject\ con \Templates\Projects\ConsoleApp\\.  
  
2.  Nel **delle proprietà** finestra, selezionare tutti i cinque file nella cartella \Templates\Projects\ConsoleApp\ e verificare che il **azione di compilazione** è impostata su **ZipProject**.  
  
3.  Nel file SimpleProject.vstemplate, aggiungere la riga seguente alla fine del \<TemplateData > sezione, appena prima del tag di chiusura.  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     In questo modo il modello di applicazione Console venga visualizzato nel nodo figlio Console e nel nodo padre SimpleProject, a un livello sopra il nodo figlio.  
  
4.  Salvare il file SimpleProject.vstemplate.  
  
5.  Nel file con estensione csproj, aggiungere \<OutputSubPath > a ciascuno degli elementi ZipProject. Scaricare il progetto, come in precedenza e modificare il file di progetto.  
  
6.  Individuare il \<ZipProject > elementi. A ogni \<ZipProject > elemento, aggiungere un \<OutputSubPath > elemento e assegnargli il valore di Console. Il ZipProject  
  
    ```  
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>  
    ```  
  
7.  Aggiungere quanto segue \<PropertyGroup > nel file di progetto:  
  
    ```  
    <PropertyGroup>  
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>  
    </PropertyGroup>  
    ```  
  
8.  Salvare il file di progetto e ricaricare il progetto.  
  
## <a name="testing-the-project-type-child-node"></a>Il nodo figlio del tipo progetto di test  
 Verificare il file di progetto modificato per verificare se il **Console** nodi figlio viene visualizzato nel **nuovo progetto** nella finestra di dialogo.  
  
1.  Eseguire la **reimpostare l'istanza Microsoft Visual Studio sperimentale** dello strumento.  
  
2.  Ricompilare il progetto SimpleProject e avviare il debug. L'istanza sperimentale dovrebbe essere visualizzato  
  
3.  Nel **nuovo progetto** finestra di dialogo, fare clic sui **SimpleProject** nodo. Il **applicazione Console** modello deve essere visualizzato nei **modelli** riquadro.  
  
4.  Espandere la **SimpleProject** nodo. Il **Console** nodo figlio deve essere visualizzato. Il **applicazione SimpleProject** modello continua ad apparire nel **modelli** riquadro.  
  
5.  . Fare clic su **annullare** e arrestare il debug  
  
 ![](../extensibility/media/simpproj2-rollup.png "SimpProj2_Rollup")  
  
 ![](../extensibility/media/simpproj2-subfolder.png "SimpProj2_Subfolder")  
  
## <a name="substituting-project-template-parameters"></a>Sostituzione di parametri di modello di progetto  
 [Creazione di un sistema di progetto di base, parte 1](../extensibility/creating-a-basic-project-system-part-1.md) è stato illustrato come sovrascrivere i `ProjectNode.AddFileFromTemplate` metodo per ottenere un tipo di base della sostituzione di parametri di modello. In questa sezione illustra come usare i parametri di modello di Visual Studio più sofisticati.  
  
 Quando si crea un progetto tramite un modello di Visual Studio il **nuovo progetto** nella finestra di dialogo modello i parametri vengono sostituiti con le stringhe per personalizzare il progetto. Un parametro di modello è un token speciale che inizia e finisce con un segno di dollaro, ad esempio, $ $time. I due parametri seguenti sono particolarmente utili per l'abilitazione della personalizzazione nei progetti che si basano sul modello:  
  
-   $ $GUID [1-10] viene sostituito da un nuovo Guid. È possibile specificare fino a 10 GUID univoci, ad esempio, $guid1$.  
  
-   $safeprojectname$ è il nome specificato da un utente di **nuovo progetto** nella finestra di dialogo modificata per rimuovere i caratteri non sicuri e gli spazi.  
  
 Per un elenco completo dei parametri dei modelli, vedere [Parametri di modelli](../ide/template-parameters.md).  Se si desidera creare il proprio parametro di modello personalizzato, vedere [NIB: procedura: passare parametri personalizzati ai modelli](http://msdn.microsoft.com/en-us/5bc2ad11-84c7-4683-a276-e5e00d85d8fb).  
  
#### <a name="to-substitute-project-template-parameters"></a>Per sostituire i parametri di modello di progetto  
  
1.  Nel file SimpleProjectNode.cs, rimuovere il `AddFileFromTemplate` (metodo).  
  
2.  Nel file \Templates\Projects\ConsoleApp\SimpleProject.myproj, individuare il \<RootNamespace > proprietà e modificarne il valore su $ $safeprojectname.  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  Nel file \Templates\Projects\SimpleProject\Program.cs, sostituire il contenuto del file con il codice seguente:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace $safeprojectname$  
    {  
        [Guid("$guid1$")]  
        public class $safeprojectname$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
4.  Ricompilare il progetto SimpleProject e avviare il debug. L'istanza sperimentale dovrebbe essere visualizzato.  
  
5.  Creare una nuova applicazione SimpleProject Console. (Nelle **tipi di progetto** riquadro, selezionare **SimpleProject**. Nella sezione **modelli di Visual Studio installati**, selezionare **applicazione Console**.)  
  
6.  Aprire Program.cs nel progetto appena creato. Dovrebbe essere simile al seguente (i valori GUID nel file saranno diversa.):  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace Console_Application1  
    {  
        [Guid("00000000-0000-0000-00000000-00000000)"]  
        public class Console_Application1  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
## <a name="creating-a-project-property-page"></a>Creazione di una pagina delle proprietà progetto  
 È possibile creare una pagina delle proprietà per il tipo di progetto in modo che gli utenti possono visualizzare e modificare le proprietà nei progetti basati su modello. Questa sezione illustra come creare una pagina delle proprietà indipendenti dalla configurazione. Questa pagina delle proprietà di base usa una griglia delle proprietà per visualizzare le proprietà pubbliche che esposta nella classe della pagina proprietà.  
  
 Derivare la classe di pagina di proprietà dal `SettingsPage` classe di base. Griglia delle proprietà fornita dal `SettingsPage` classe è a conoscenza dei tipi di dati più primitivi e sa come visualizzarli.  Inoltre, il `SettingsPage` classe in grado di rendere persistenti i valori delle proprietà del file di progetto.  
  
 La pagina delle proprietà create in questa sezione consente di modificare e salvare le proprietà del progetto:  
  
-   AssemblyName  
  
-   OutputType  
  
-   RootNamespace.  
  
1.  Nel file SimpleProjectPackage.cs, aggiungere questo `ProvideObject` dell'attributo di `SimpleProjectPackage` classe:  
  
    ```  
    [ProvideObject(typeof(GeneralPropertyPage))]  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
     Questo registra la classe delle pagine proprietà `GeneralPropertyPage` con COM.  
  
2.  Nel file SimpleProjectNode.cs, aggiungere questi due metodi sottoposti a override per il `SimpleProjectNode` classe:  
  
    ```  
    protected override Guid[] GetConfigurationIndependentPropertyPages()  
    {  
        Guid[] result = new Guid[1];  
        result[0] = typeof(GeneralPropertyPage).GUID;  
        return result;  
    }  
    protected override Guid[] GetPriorityProjectDesignerPages()  
    {  
        Guid[] result = new Guid[1];  
        result[0] = typeof(GeneralPropertyPage).GUID;  
         return result;  
    }  
    ```  
  
     Entrambi questi metodi restituiscono una matrice di GUID pagina delle proprietà.  Il GUID GeneralPropertyPage è l'unico elemento nella matrice, in modo che il **pagine delle proprietà** nella finestra di dialogo visualizzerà solo una pagina.  
  
3.  Aggiungere un file di classe denominato GeneralPropertyPage.cs al progetto SimpleProject.  
  
4.  Sostituire il contenuto di questo file usando il codice seguente:  
  
    ```  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Project;  
    using System.ComponentModel;  
  
    namespace SimpleProject  
    {  
        [ComVisible(true)]  
        [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]  
        public class GeneralPropertyPage : SettingsPage  
        {  
            private string assemblyName;  
            private OutputType outputType;  
            private string defaultNamespace;  
  
            public GeneralPropertyPage()  
            {  
                this.Name = "General";  
            }  
  
            [Category("AssemblyName")]  
            [DisplayName("AssemblyName")]  
            [Description("The output file holding assembly metadata.")]  
            public string AssemblyName  
            {  
                get { return this.assemblyName; }  
            }  
            [Category("Application")]  
            [DisplayName("OutputType")]  
            [Description("The type of application to build.")]  
            public OutputType OutputType  
            {  
                get { return this.outputType; }  
                set { this.outputType = value; this.IsDirty = true; }  
            }  
            [Category("Application")]  
            [DisplayName("DefaultNamespace")]  
            [Description("Specifies the default namespace for added items.")]  
            public string DefaultNamespace  
            {  
                get { return this.defaultNamespace; }  
                set { this.defaultNamespace = value; this.IsDirty = true; }  
            }  
  
            protected override void BindProperties()  
            {  
                this.assemblyName = this.ProjectMgr.GetProjectProperty(  
    "AssemblyName", true);  
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty(  
    "RootNamespace", false);  
  
                string outputType = this.ProjectMgr.GetProjectProperty(  
    "OutputType", false);  
                this.outputType =   
    (OutputType)Enum.Parse(typeof(OutputType), outputType);  
            }  
  
            protected override int ApplyChanges()  
            {  
                this.ProjectMgr.SetProjectProperty(  
    "AssemblyName", this.assemblyName);  
                this.ProjectMgr.SetProjectProperty(  
    "OutputType", this.outputType.ToString());  
                this.ProjectMgr.SetProjectProperty(  
    "RootNamespace", this.defaultNamespace);  
                this.IsDirty = false;  
  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    ```  
  
     Il `GeneralPropertyPage` classe espone tre proprietà pubbliche AssemblyName OutputType e RootNamespace. Poiché AssemblyName non dispone di alcun metodo set, viene visualizzato come proprietà di sola lettura. OutputType è costante enumerata, viene visualizzato come elenco a discesa.  
  
     Il `SettingsPage` classe di base fornisce `ProjectMgr` per rendere persistenti le proprietà. Il `BindProperties` Usa metodo `ProjectMgr` per recuperare i valori della proprietà persistente e impostare le proprietà corrispondenti.  Il `ApplyChanges` Usa metodo `ProjectMgr` per ottenere i valori delle proprietà e renderli persistenti nel file di progetto. Impostare la proprietà metodo imposta `IsDirty` su true per indicare che le proprietà devono essere resi persistenti.  Persistenza si verifica quando si salva il progetto o soluzione.  
  
5.  Ricompilare la soluzione SimpleProject e avviare il debug. L'istanza sperimentale dovrebbe essere visualizzato.  
  
6.  Nell'istanza sperimentale, creare una nuova applicazione SimpleProject.  
  
7.  Visual Studio chiama la factory di progetto per creare un progetto usando il modello di Visual Studio. Il nuovo file Program.cs è aperto nell'editor del codice.  
  
8.  Fare clic sul nodo del progetto in **Esplora soluzioni**, quindi fare clic su **proprietà**. Verrà visualizzata la finestra di dialogo **Pagine delle proprietà**.  
  
 ![](../extensibility/media/simpproj2-proppage.png "SimpProj2_PropPage")  
  
## <a name="testing-the-project-property-page"></a>Pagina delle proprietà del progetto di test  
 A questo punto è possibile verificare se è possibile modificare e modificare i valori delle proprietà.  
  
1.  Nel **pagine delle proprietà MyConsoleApplication** della finestra di dialogo Modifica il **DefaultNamespace** a **MyApplication**.  
  
2.  Selezionare il **OutputType** proprietà e quindi selezionare **libreria di classi**.  
  
3.  Fare clic su **Apply**, quindi fare clic su **OK**.  
  
4.  Riaprire il **pagine delle proprietà** dialogo casella e verificare che le modifiche sono state rese persistenti.  
  
5.  Chiudere l'istanza sperimentale di Visual Studio.  
  
6.  Riaprire l'istanza sperimentale.  
  
7.  Riaprire il **pagine delle proprietà** dialogo casella e verificare che le modifiche sono state rese persistenti.  
  
8.  Chiudere l'istanza sperimentale di Visual Studio.  
  
 ![](../extensibility/media/simpproj2-proppage2.png "SimpProj2_PropPage2")

