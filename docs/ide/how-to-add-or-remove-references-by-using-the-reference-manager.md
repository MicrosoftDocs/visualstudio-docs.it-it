---
title: 'Procedura: Aggiungere o rimuovere riferimenti mediante Gestione riferimenti | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- C# projects, references
- references [Visual Studio], adding
- assemblies [Visual Studio], references
- Visual Basic projects, references
- project references, adding
- referencing components, adding references
- project references, removing
- referencing assemblies
- referencing components, removing references
- references [Visual Studio], removing
- referencing components, assemblies not listed
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 83c90ee535830f6747a7f847ac649078be03451e
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Procedura: Aggiungere o rimuovere riferimenti tramite Gestione riferimenti

È possibile usare la finestra di dialogo **Gestione riferimenti** per aggiungere e gestire riferimenti a componenti sviluppati da esperti indipendenti, da Microsoft o da altre società. Se si sviluppa un’app Universal Windows, il progetto fa riferimento automaticamente a tutte le DLL SDK Windows corrette. Se si sviluppa un'applicazione .NET, il progetto fa automaticamente riferimento a mscorlib. dll. Alcune API .NET vengono esposte nei componenti che è necessario aggiungere manualmente. I riferimenti ai componenti COM o ai componenti personalizzati devono essere aggiunti manualmente.

## <a name="reference-manager-dialog-box"></a>Finestra di dialogo Gestione riferimenti

Sul lato sinistro della finestra di dialogo **Gestione riferimenti** sono disponibili categorie diverse a seconda del tipo di progetto:

- Assembly, con i sottogruppi Estensioni e Framework.

- Nella scheda COM sono elencati tutti i componenti COM a cui è possibile fare riferimento.

- Soluzione, con il sottogruppo Progetti.

- Windows, con il Sottogruppo di base ed Estensioni. È possibile esplorare i riferimenti in Windows SDK o negli SDK di estensione tramite il **visualizzatore oggetti**.

- Visualizzazione, con il sottogruppo Recenti.

## <a name="adding-and-removing-a-reference"></a>Aggiunta e rimozione di un riferimento

### <a name="to-add-a-reference"></a>Per aggiungere un riferimento

1. In **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul nodo Riferimenti e scegliere **Aggiungi riferimento**.

2. Specificare i riferimenti da aggiungere e scegliere **OK**.

   Verrà visualizzata la finestra della **Gestione riferimenti** che elenca i riferimenti disponibili in base al gruppo.

## <a name="assemblies-tab"></a>Scheda Assembly

La scheda **Assembly** elenca tutti gli assembly di .NET Framework disponibili per riferimento. Nella scheda **Assembly** non vengono elencati gli assembly della Global Assembly Cache (GAC) in quanto questi assembly fanno parte dell'ambiente di runtime. Se si distribuisce o si copia un'applicazione che contiene un riferimento a un assembly registrato nella Global Assembly Cache, tale assembly non verrà distribuito o copiato con l'applicazione, indipendentemente dall'impostazione dell'opzione Copia localmente. Per altre informazioni, vedere [Gestione dei riferimenti in un progetto](../ide/managing-references-in-a-project.md).

Quando si aggiunge manualmente un riferimento a uno qualsiasi degli spazi dei nomi EnvDTE (EnvDTE, EnvDTE80, EnvDTE90, EnvDTE90a o EnvDTE100), impostare la proprietà **Incorpora tipi di interoperabilità** su **False** nella finestra Proprietà. L'impostazione di questa proprietà su **True** può causare problemi di compilazione dovuti ad alcune proprietà EnvDTE che non possono essere incorporate.

Tutti i progetti desktop contengono un riferimento implicito a mscorlib. I progetti di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] contengono un riferimento implicito a Microsoft.VisualBasic. Tutti i progetti contengono un riferimento implicito a System.Core, anche se è stato rimosso dall'elenco di riferimenti.

Se un tipo di progetto non supporta gli assembly, la scheda non verrà visualizzata nella finestra di dialogo **Gestione riferimenti**.

La scheda Assembly è costituita da due sottoschede:

1. In **Framework** sono elencati tutti gli assembly che costituiscono il framework di destinazione.

    I progetti per le app Windows 8.x Store contengono riferimenti a tutti gli assembly di [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] di destinazione per impostazione predefinita al momento della creazione del progetto. Nei progetti gestiti, un nodo di sola lettura nella cartella Riferimenti di **Esplora soluzioni** indica il riferimento all'intero framework. Nella scheda Framework, pertanto, non verranno enumerati gli assembly provenienti dal framework e verrà invece visualizzato il messaggio seguente: "Si è già fatto riferimento a tutti gli assembly del framework. Utilizzare Visualizzatore oggetti per esplorare i riferimenti nel framework". Per i progetti desktop, nella scheda Framework vengono enumerati gli assembly dal framework di destinazione e l'utente dovrà aggiungere i riferimenti necessari all'applicazione.

2. In **Estensioni** sono elencati tutti gli assembly che i fornitori esterni di componenti e di controlli hanno sviluppato per estendere il framework di destinazione. A seconda dello scopo dell'applicazione utente, potrebbero essere necessari questi assembly.

   Estensioni viene popolata enumerando gli assembly che sono registrati nei seguenti percorsi:

   Computer a 32 bit:
   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]

   Computer a 64 bit:
   - HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
   - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies] E versioni precedenti di [Target Framework Identifier]

   Ad esempio, se un progetto è destinato a .NET Framework 4 in un computer a 32 bit, Estensioni enumera gli assembly che sono registrati in \Microsoft\\.NETFramework\v4.0\AssemblyFoldersEx\\, \Microsoft\\.NETFramework\v3.5\AssemblyFoldersEx\\, \Microsoft\\.NETFramework\v3.0\AssemblyFoldersEx\\ e \Microsoft\\.NETFramework\v2.0\AssemblyFoldersEx\\.

Alcuni componenti nell'elenco potrebbero non essere visualizzati, a seconda della versione di .NET Framework del progetto. Ciò può verificarsi nelle seguenti condizioni:

- Un componente che usa una versione recente di .NET Framework è incompatibile con un progetto destinato a una versione di .NET Framework precedente.

    Per informazioni sulla modifica della versione di .NET Framework di destinazione per un progetto, vedere [Procedura: Destinare una versione di .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

- Un componente che usa [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] è incompatibile con un progetto destinato a [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)].

    Quando si crea una nuova applicazione, alcuni progetti sono destinati a [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] per impostazione predefinita.

- Evitare di aggiungere riferimenti a file agli output di altri progetti della stessa soluzione, poiché potrebbero verificarsi errori di compilazione. Usare invece la scheda **Progetti** della finestra di dialogo **Aggiungi riferimento** per creare riferimenti da progetto a progetto. Tale procedura facilita lo sviluppo in team, consentendo una migliore gestione delle librerie di classi create nei progetti. Per altre informazioni, vedere [Risoluzione dei problemi relativi ai riferimenti interrotti](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> In Visual Studio 2015 o versioni successive, viene creato un riferimento al file anziché un riferimento al progetto se la versione di destinazione di .NET Framework di un progetto è 4.5 o versioni successive e la versione di destinazione dell'altro progetto è 2, 3, 3.5 o 4.0.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Per visualizzare un assembly nella finestra di dialogo Aggiungi riferimento

- Spostare o copiare l'assembly in una o più delle seguenti posizioni:

    - La directory del progetto corrente. È possibile trovare questi assembly tramite la scheda **Sfoglia** .

    - Altre directory di progetto nella stessa soluzione. È possibile trovare questi assembly tramite la scheda **Progetti**.

    \- oppure -

- Impostare una chiave del Registro di sistema che specifica il percorso degli assembly da visualizzare:

   Per un sistema operativo a 32 bit, aggiungere una delle seguenti chiavi del Registro di sistema.

   - [HKEY_CURRENT_USER\SOFTWARE\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"

   - [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"

   Per un sistema operativo a 64 bit, aggiungere una delle seguenti chiavi del Registro di sistema in un hive del Registro di sistema a 32 bit.

   - [HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"

   - [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"

   *VersionMinimum* corrisponde alla versione minima applicabile di .NET Framework. Se il valore di *VersionMinimum* è v3.0, le cartelle specificate in AssemblyFoldersEx si applicano ai progetti destinati a .NET Framework 3.0 e versioni successive.

   *AssemblyLocation* è la directory degli assembly che si vuole visualizzare nella finestra di dialogo **Aggiungi riferimento**, ad esempio C:\MyAssemblies\\.

   Se la chiave del Registro di sistema viene creata nel nodo HKEY_LOCAL_MACHINE, tutti gli utenti possono visualizzare gli assembly nel percorso specificato nella finestra di dialogo **Aggiungi riferimento**. Se la chiave del Registro di sistema viene creata nel nodo HKEY_CURRENT_USER, ha effetto solo sull'impostazione dell'utente corrente.

   Aprire di nuovo la finestra di dialogo **Aggiungi riferimento**. Gli assembly dovrebbero essere visibili nella scheda **.NET**. In caso contrario, assicurarsi che gli assembly si trovino nella directory *AssemblyLocation* specificata, riavviare Visual Studio e riprovare.

## <a name="com-tab"></a>Scheda COM

Nella scheda COM sono elencati tutti i componenti COM a cui è possibile fare riferimento. Se si desidera aggiungere un riferimento a una DLL COM registrata che contiene un manifesto interno, annullare prima di tutto la registrazione della DLL. In caso contrario, Visual Studio aggiungerà il riferimento all'assembly come controllo ActiveX e non come DLL nativa.

Se un tipo di progetto non supporta il modello COM, la scheda non verrà visualizzata nella finestra di dialogo **Gestione riferimenti**.

## <a name="solution-tab"></a>Scheda Soluzione

Nella scheda Soluzione sono elencati tutti i progetti compatibili all'interno della soluzione corrente, nella sottoscheda Progetti.

Un progetto può fare riferimento a un altro progetto destinato a una versione differente di .NET Framework. Ad esempio, è possibile creare un progetto destinato a [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] ma che fa riferimento a un assembly compilato per .NET Framework 2. Tuttavia, il progetto .NET Framework 2 non può fare riferimento a un progetto [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]. Per altre informazioni, vedere [Cenni preliminari sul multitargeting](../ide/visual-studio-multi-targeting-overview.md).

Un progetto destinato a [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] è incompatibile con un progetto destinato a [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].

Viene creato un riferimento al file anziché un riferimento al progetto se un progetto è destinato a .NET Framework 4 e un altro progetto è destinato a una versione precedente.

Un progetto destinato a [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] non può aggiungere un riferimento a un progetto destinato a .NET Framework e viceversa.

## <a name="windows-tab"></a>Scheda Windows.

Nella scheda Windows sono elencati tutti gli SDK specifici alle piattaforme nelle quali vengono eseguiti i sistemi operativi Windows.

È possibile generare un file WinMD in Visual Studio in due modi:

- **Progetti gestiti per app Windows 8.x Store**: i progetti per app Windows 8.x Store possono generare file binari WinMD impostando Proprietà progetto &#124; Tipo di output = WinMD File. Il nome del file WinMD deve essere lo spazio dei nomi superset di tutti gli spazi dei nomi in esso contenuti. Ad esempio, se un progetto è costituito dagli spazi dei nomi A.B e A.B.C, i nomi possibili per il file WinMD generato saranno A.winmd e A.B.winmd. Se un utente immette un valore per Proprietà progetti &#124; Nome assembly o per Proprietà progetti &#124; Spazio dei nomi disgiunto dal set di spazi dei nomi nel progetto o non è presente alcuno spazio dei nomi superset all'interno di un progetto, viene generato un avviso di compilazione: "A.winmd" non è un nome file winmd valido per questo assembly. Tutti i tipi presenti in un file di metadati di Windows devono esistere in uno spazio dei nomi secondario del nome file. Impossibile trovare nel runtime i tipi che non esistono in questo spazio dei nomi secondario. In questo assembly, lo spazio dei nomi comune più piccolo è "CSWSClassLibrary1". Un progetto desktop Visual Basic o C# può usare solo file WinMD generati tramite SDK Windows 8, noti come WinMD del produttore, e non può generare WinMD.

- **Progetti nativi per app Windows 8.x Store**: un file WinMD nativo è costituito solo da metadati. L'implementazione esiste in un file DLL distinto. È possibile produrre i file binari nativi scegliendo il modello di progetto del componente Windows Runtime nella finestra di dialogo **Nuovo progetto** o iniziando da un progetto vuoto e modificando le proprietà del progetto per generare un file WinMD. Se il progetto è costituito da spazi dei nomi disgiunti, un errore di compilazione indicherà all'utente di combinare gli spazi dei nomi o di eseguire lo strumento MSMerge.

La scheda Windows è costituita da due sottogruppi.

### <a name="core-subgroup"></a>Sottogruppo di base

Nel Sottogruppo di base sono elencati tutti i file WinMD (per gli elementi Windows Runtime) nell'SDK per la versione di Windows di destinazione.

I progetti per app Windows 8.x Store contengono riferimenti a tutti i file WinMD in Windows 8 SDK per impostazione predefinita al momento della creazione del progetto. Nei progetti gestiti, un nodo di sola lettura nella cartella Riferimenti di **Esplora soluzioni** indica il riferimento all'intero Windows 8 SDK. Di conseguenza, in Sottogruppo di base in Gestione riferimenti non verrà enumerato alcuno degli assembly da Windows 8 SDK e verrà visualizzato invece il messaggio "‪Si è già fatto riferimento all'SDK Windows. Utilizzare Visualizzatore oggetti per esplorare i riferimenti nell'SDK Windows".

Per impostazione predefinita, nei progetti desktop la sezione Sottogruppo di base non viene visualizzata . È possibile aggiungere Windows Runtime aprendo il menu di scelta rapida del nodo del progetto, scegliendo **Scarica progetto**, aggiungendo il frammento seguente e riaprendo il progetto (nel nodo del progetto scegliere **Ricarica progetto**). Quando si apre la finestra di dialogo **Gestione riferimenti**, viene visualizzato il sottogruppo di base.

```xml
<PropertyGroup>
  <TargetPlatformVersion>8.0</TargetPlatformVersion>
</PropertyGroup>
```

Assicurarsi di selezionare la casella di controllo **Windows** in questo sottogruppo. A questo punto dovrebbe essere possibile utilizzare gli elementi Windows Runtime. Tuttavia, è possibile che si desideri aggiungere System.Runtime, in cui Windows Runtime definisce alcune classi e interfacce standard, come IEnumerable, che sono utilizzate in tutte le librerie di Windows Runtime. Per informazioni su come aggiungere System.Runtime, vedere [App desktop gestite e Windows Runtime](http://msdn.microsoft.com/library/windows/apps/jj856306.aspx#consuming_standard_windows_runtime_types).

### <a name="extensions-subgroup"></a>Sottogruppo Estensioni

In Estensioni sono elencati gli SDK che estendono la piattaforma Windows di destinazione. Questa scheda viene visualizzata solo per i progetti di app Windows 8.x Store. Nei progetti desktop questa scheda non viene visualizzata perché tali progetti possono utilizzare solo file con estensione winmd del produttore.

Un SDK è una raccolta di file che in Visual Studio vengono trattati come un singolo componente. Nella scheda Estensioni, gli SDK che si applicano al progetto da cui è stata aperta la finestra di dialogo **Gestione riferimenti** sono elencati come voci singole. Una volta aggiunto a un progetto, tutto il contenuto dell'SDK viene utilizzato da Visual Studio in modo tale che l'utente non deve eseguire nuove azioni per sfruttare il contenuto dell'SDK in IntelliSense, nella casella degli strumenti, nelle finestre di progettazione, nel Visualizzatore oggetti, nella compilazione, nella distribuzione, nel debug e nella creazione del pacchetto. Per informazioni su come visualizzare l'SDK nella scheda Estensioni, vedere [Creating a Software Development Kit](../extensibility/creating-a-software-development-kit.md) (Creazione di un Software Development Kit).

> [!NOTE]
> Se un progetto fa riferimento a un SDK che dipende da un altro SDK, Visual Studio utilizzerà il secondo SDK solo se l'utente aggiunge manualmente un riferimento a quest'ultimo. Quando un utente sceglie un SDK nella scheda **Estensioni**, la finestra di dialogo **Gestione riferimenti** consente di identificare le dipendenze dall'SDK elencando non solo il nome e la versione dell'SDK ma anche il nome di tutte le dipendenze dell'SDK nel riquadro dei dettagli. Se l'utente non annota le dipendenze e aggiunge solo l'SDK, MSBuild chiede di aggiungere le dipendenze.

Se un tipo di progetto non supporta **Estensioni**, la scheda non viene visualizzata nella finestra di dialogo **Gestione riferimenti**.

## <a name="browse-button"></a>Pulsante Sfoglia

È possibile usare il pulsante **Sfoglia** per passare a un componente nel file system.

Un progetto può fare riferimento a un componente destinato a una versione differente di .NET Framework. Ad esempio, è possibile creare un'applicazione destinata a .NET Framework 4.7, che fa riferimento a un componente destinato a .NET Framework 4. Per altre informazioni, vedere [Cenni preliminari sul multitargeting](../ide/visual-studio-multi-targeting-overview.md).

Evitare di aggiungere riferimenti di file agli output di un altro progetto della stessa soluzione, poiché questa tattica potrebbe causare errori di compilazione. Usare invece la scheda **Soluzione** della finestra di dialogo **Gestione riferimenti** per creare riferimenti da progetto a progetto. Si facilita così lo sviluppo in team, consentendo una migliore gestione delle librerie di classi create nei progetti. Per altre informazioni, vedere [Risoluzione dei problemi relativi ai riferimenti interrotti](../ide/troubleshooting-broken-references.md).

Non è possibile individuare un SDK e aggiungerlo al progetto. È possibile solo individuare un file, ad esempio un assembly o un file .winmd, e aggiungerlo al progetto.

Nella creazione di un riferimento di file a un WinMD, il layout previsto è quello in cui i file *NomeFile*.winmd, *NomeFile*.dll e *NomeFile*.pri si trovino l'uno accanto all'altro. Se si fa riferimento a un WinMD nei seguenti scenari, un set incompleto di file verrà copiato nella directory di output del progetto e, di conseguenza, si verificheranno errori di runtime e di compilazione.

- **Componente nativo**: un progetto nativo crea un WinMD per ogni set di spazi dei nomi disgiunto e una sola DLL costituita dall'implementazione. I file WinMD avranno nomi diversi. Durante la creazione del riferimento a questo file di componente nativo, MSBuild non sarà in grado di riconoscere che WinMD con nome diverso sono in realtà un unico componente. Di conseguenza, saranno copiati solo i file *NomeFile*.dll e *NomeFile*.winmd con lo stesso nome e si verificheranno errori di runtime. Per risolvere questo problema, creare un SDK di estensione. Per altre informazioni, vedere [Creating a Software Development Kit](../extensibility/creating-a-software-development-kit.md) (Creazione di un Software Development Kit).

- **Uso di controlli**: un controllo XAML consiste minimo di *NomeFile*.winmd, *NomeFile*.dll, *NomeFile*.pri, *NomeXaml*.xaml e *NomeImmagine*.jpg. Quando il progetto viene compilato, i file di risorse associati al riferimento a file non vengono copiati nella directory di output del progetto. Verranno copiati solo i file *NomeFile*.winmd, *NomeFile*.dll e *NomeFile*.pri. Verrà registrato un errore di compilazione per informare l'utente dell'assenza delle risorse *NomeXaml*.xaml e *NomeImmagine*.jpg. Per ottenere i risultati desiderati, l'utente dovrà copiare manualmente questi file di risorse nella directory di output del progetto per compilazione e debug/runtime. Per risolvere questo problema, creare un SDK di estensione seguendo i passaggi in [Creating a Software Development Kit](../extensibility/creating-a-software-development-kit.md) (Creazione di un Software Development Kit) o modificare il file di progetto per aggiungere la proprietà seguente:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Se si aggiunge la proprietà, la compilazione potrebbe essere eseguita più lentamente.

## <a name="recent"></a>Recenti

Le schede Assembly, COM, Windows e Sfoglia supportano tutte una scheda Recenti nella quale viene enumerato l'elenco di componenti aggiunti ai progetti di recente.

## <a name="search"></a>Cerca

La barra di ricerca della finestra di dialogo **Gestione riferimenti** viene abilitata nella scheda attiva. Ad esempio, se un utente digita "sistema" nella barra di ricerca mentre è attiva la scheda **Soluzione**, verranno restituiti risultati solo se la soluzione è costituita da un nome di progetto contenente il termine "sistema".

## <a name="see-also"></a>Vedere anche

[Gestione dei riferimenti in un progetto](../ide/managing-references-in-a-project.md)
