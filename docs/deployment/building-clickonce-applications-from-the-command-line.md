---
title: Compilazione di applicazioni ClickOnce dalla riga di comando | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4488f32b135d766f494bc94946fbf77d42eb1e95
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="building-clickonce-applications-from-the-command-line"></a>Compilazione di applicazioni ClickOnce dalla riga di comando
In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], è possibile compilare progetti dalla riga di comando, anche se sono state create nell'ambiente di sviluppo integrato (IDE). In effetti, è possibile ricompilare un progetto creato con [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] in un altro computer che dispone solo di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] installato. Ciò consente di riprodurre una compilazione usando un processo automatizzato, ad esempio, in una compilazione centrale o tramite tecniche di scripting avanzate esulano dall'ambito di compilazione del progetto stesso.  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>Utilizzo di MSBuild per riprodurre le distribuzioni di applicazioni ClickOnce  
 Quando si richiama /target: Publish msbuild dalla riga di comando, indica al sistema di MSBuild per compilare il progetto e creare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione nella cartella di pubblicazione. Ciò equivale alla selezione di **pubblica** comando nell'IDE.  
  
 Questo comando esegue msbuild.exe, che si trova nel percorso nell'ambiente di prompt dei comandi di Visual Studio.  
  
 "target" è un indicatore a MSBuild come elaborare il comando. Le destinazioni principali sono la destinazione "build" e destinazione "pubblica". La destinazione build equivale a selezionare la compilazione comando (o premendo F5) nell'IDE. Se si desidera compilare il progetto, è possibile ottenere che digitando `msbuild`. Questo comando funziona perché la destinazione build è la destinazione predefinita per tutti i progetti generati da [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Ciò significa, in modo esplicito sarà necessario specificare la destinazione build. Pertanto, digitando `msbuild` è la stessa operazione tipizzazione `msbuild /target:build`.  
  
 Il `/target:publish` comando indica a MSBuild di richiamare la destinazione di pubblicazione. La destinazione di pubblicazione varia a seconda della destinazione build. Ciò significa che l'operazione di pubblicazione è un superset dell'operazione di compilazione. Ad esempio, se è stata apportata una modifica a uno dei file di origine Visual Basic o c#, l'assembly corrispondente verrà rigenerato automaticamente dall'operazione di pubblicazione.  
  
 Per informazioni sulla generazione di una procedura completa di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione utilizzando lo strumento da riga di comando Mage.exe per creare il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>Creazione e compilazione di un'applicazione ClickOnce di base utilizzando MSBuild  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>Per creare e pubblicare un progetto di ClickOnce  
  
1.  Fare clic su **nuovo progetto** dal **File** menu. Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2.  Selezionare **applicazione Windows** e denominarlo `CmdLineDemo`.  
  
3.  Dal **compilare** menu, fare clic su di **pubblica** comando.  
  
     Questo passaggio assicura che il progetto è configurato correttamente per produrre un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione dell'applicazione.  
  
     Verrà visualizzata la Pubblicazione guidata.  
  
4.  Nella pubblicazione guidata, fare clic su **fine**.  
  
     Visual Studio genera l'errore e Visualizza la pagina Web predefinita, denominata Publish.  
  
5.  Salvare il progetto e prendere nota del percorso di cartella in cui è archiviato.  
  
 Crea la procedura descritta sopra un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] progetto che è stato pubblicato per la prima volta. È ora possibile riprodurre la compilazione all'esterno dell'IDE.  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>Per ripetere la compilazione dalla riga di comando  
  
1.  Chiudere [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
2.  Da Windows **avviare** menu, fare clic su **tutti i programmi**, quindi **Microsoft Visual Studio**, quindi **Visual Studio Tools**, quindi **Prompt dei comandi di visual Studio**. Verrà aperto un prompt dei comandi nella cartella principale dell'utente corrente.  
  
3.  Nel **prompt dei comandi di Visual Studio**, modificare la directory corrente per il percorso del progetto appena generato. Ad esempio, digitare `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.  
  
4.  Per rimuovere i file esistenti generati "per creare e pubblicare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] progetto," tipo `rmdir /s publish`.  
  
     Questo passaggio è facoltativo, ma garantisce che tutti i nuovi file sono stati generati dalla compilazione da riga di comando.  
  
5.  Digitare `msbuild /target:publish`.  
  
 I passaggi precedenti produrrà una procedura completa di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione dell'applicazione in una sottocartella del progetto denominata P**ubblica**. CmdLineDemo. Application è il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto di distribuzione. La cartella CmdLineDemo 1.0.0.0 contiene i file CmdLineDemo.exe e CmdLineDemo.exe.manifest, ossia il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto dell'applicazione. Setup.exe è il programma di avvio automatico, che per impostazione predefinita è configurato per l'installazione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. La cartella DotNetFX contiene i file ridistribuibili per il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Questo è l'intero set di file che necessari per distribuire l'applicazione sul Web o tramite CD/DVD o UNC.  
  
## <a name="publishing-properties"></a>Proprietà di pubblicazione  
 Quando si pubblica l'applicazione nelle procedure precedenti, le proprietà seguenti vengono inserite nel file di progetto per la pubblicazione guidata. Queste proprietà influiscono direttamente sul modo in cui il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verrà generata l'applicazione.  
  
 In CmdLineDemo.vbproj / CmdLineDemo.csproj:  
  
```  
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>  
<GenerateManifests>true</GenerateManifests>  
<TargetZone>LocalIntranet</TargetZone>  
<PublisherName>Microsoft</PublisherName>  
<ProductName>CmdLineDemo</ProductName>  
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>  
<Install>true</Install>  
<ApplicationVersion>1.0.0.*</ApplicationVersion>  
<ApplicationRevision>1</ApplicationRevision>  
<UpdateEnabled>true</UpdateEnabled>  
<UpdateRequired>false</UpdateRequired>  
<UpdateMode>Foreground</UpdateMode>  
<UpdateInterval>7</UpdateInterval>  
<UpdateIntervalUnits>Days</UpdateIntervalUnits>  
<UpdateUrlEnabled>false</UpdateUrlEnabled>  
<IsWebBootstrapper>true</IsWebBootstrapper>  
<BootstrapperEnabled>true</BootstrapperEnabled>  
```  
  
 È possibile eseguire l'override di una di queste proprietà nella riga di comando senza modificare il file di progetto stesso. Ad esempio, si creerà la seguente il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione dell'applicazione senza il programma di avvio automatico:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Le proprietà di pubblicazione sono controllate in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dal **pubblica**, **sicurezza**, e **firma** pagine delle proprietà di **Progettazione progetti** . Di seguito è riportata una descrizione delle proprietà di pubblicazione, insieme a un'indicazione di ognuno di essi nelle varie pagine delle proprietà della finestra di progettazione dell'applicazione:  
  
-   `AssemblyOriginatorKeyFile` Determina il file di chiave utilizzato per firmare il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesti dell'applicazione. La stessa chiave può essere utilizzata anche per assegnare un nome sicuro all'assembly. Questa proprietà è impostata sul **firma** pagina della finestra di **Progettazione progetti**.  
  
 Le seguenti proprietà vengono impostate sul **sicurezza** pagina:  
  
-   **Abilitare le impostazioni di sicurezza ClickOnce** determina se [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesti vengono generati. Quando un progetto viene creato inizialmente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la generazione del manifesto è disattivata per impostazione predefinita. La procedura guidata verrà attivato automaticamente questo flag viene pubblicato per la prima volta.  
  
-   **TargetZone** determina il livello di trust essere emessa nel [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto dell'applicazione. I valori possibili sono "Internet", "LocalIntranet" e "Custom". Internet e Intranet locale provocherà un set di autorizzazioni predefinito per essere emessa nel [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto dell'applicazione. LocalIntranet è il valore predefinito e l'attendibilità totale. Custom specifica che solo le autorizzazioni in modo esplicito specificate nel file app. manifest base essere emessa nel [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto dell'applicazione. Il file app. manifest è un file manifesto parziale contenente solo le definizioni di informazioni di trust. È un file nascosto, aggiunto automaticamente al progetto quando si configurano le autorizzazioni nel **sicurezza** pagina.  
  
 Le seguenti proprietà vengono impostate sul **pubblica** pagina:  
  
-   `PublishUrl` rappresenta la posizione in cui verrà pubblicata per l'applicazione nell'IDE. Viene inserito nella [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] il manifesto dell'applicazione se non si specifica il `InstallUrl` o `UpdateUrl` proprietà specificata.  
  
-   `ApplicationVersion` Specifica la versione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. Questo è un numero di versione di quattro cifre. Se l'ultima cifra è un "*", quindi il `ApplicationRevision` verrà sostituito con il valore inserito nel manifesto in fase di compilazione.  
  
-   `ApplicationRevision` Specifica la revisione. Si tratta di un numero intero viene incrementato ogni volta che pubblica nell'IDE. Si noti che non è viene incrementato automaticamente per le compilazioni eseguite dalla riga di comando.  
  
-   `Install` Determina se l'applicazione è un'applicazione installata o eseguita dal Web.  
  
-   `InstallUrl` (non illustrata) è il percorso in cui gli utenti installeranno l'applicazione da. Se specificato, questo valore viene copiato nel programma setup.exe di `IsWebBootstrapper` proprietà è abilitata. Viene inoltre inserito nel manifesto dell'applicazione, se il `UpdateUrl` non è specificato.  
  
-   `SupportUrl` (non illustrata) è il percorso collegato la **Aggiungi/Rimuovi programmi** finestra di dialogo per un'applicazione installata.  
  
 Le seguenti proprietà vengono impostate **Aggiornamenti applicazione** la finestra di dialogo, accessibile dal **pubblica** pagina.  
  
-   `UpdateEnabled` indica se l'applicazione deve verificare gli aggiornamenti.  
  
-   `UpdateMode` Specifica se gli aggiornamenti in primo piano o in Background.  
  
-   `UpdateInterval` Specifica la frequenza di controllare la disponibilità di aggiornamenti.  
  
-   `UpdateIntervalUnits` Specifica se il `UpdateInterval` valore è espresso in unità di ore, giorni o settimane.  
  
-   `UpdateUrl` (non illustrata) è il percorso da cui l'applicazione riceverà gli aggiornamenti. Se specificato, questo valore viene inserito nel manifesto dell'applicazione.  
  
-   Le seguenti proprietà vengono impostate **opzioni di pubblicazione** la finestra di dialogo, accessibile dal **pubblica** pagina.  
  
-   `PublisherName` Specifica il nome del server di pubblicazione visualizzato nel messaggio visualizzato quando si installa o esegue l'applicazione. Nel caso di un'applicazione installata, viene anche utilizzato per specificare il nome della cartella di **avviare** menu.  
  
-   `ProductName` Specifica il nome del prodotto visualizzato nel messaggio visualizzato quando si installa o esegue l'applicazione. Nel caso di un'applicazione installata, viene anche utilizzato per specificare il nome del collegamento di **avviare** menu.  
  
-   Le seguenti proprietà vengono impostate **prerequisiti** la finestra di dialogo, accessibile dal **pubblica** pagina.  
  
-   `BootstrapperEnabled` Determina se generare setup.exe automatico.  
  
-   `IsWebBootstrapper` Determina se il programma di avvio automatico setup.exe funziona tramite Web o in modalità basata su disco.  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL e UpdateUrl non  
 Nella tabella seguente illustra le quattro opzioni di URL per la distribuzione ClickOnce.  
  
|Opzione URL|Descrizione|  
|----------------|-----------------|  
|`PublishURL`|Obbligatorio se si pubblica l'applicazione ClickOnce per un sito Web.|  
|`InstallURL`|Facoltativo. Impostare questa opzione URL se il sito dell'installazione è diverso da quello di `PublishURL`. Ad esempio, è possibile impostare il `PublishURL` su un percorso FTP e un set il `InstallURL` a un URL di Web.|  
|`SupportURL`|Facoltativo. Impostare questa opzione URL se il sito del supporto tecnico è diverso da quello di `PublishURL`. Ad esempio, è possibile impostare il `SupportURL` al sito Web del supporto clienti dell'azienda.|  
|`UpdateURL`|Facoltativo. Impostare questa opzione URL se il percorso di aggiornamento è diverso da quello di `InstallURL`. Ad esempio, è possibile impostare il `PublishURL` su un percorso FTP e un set il `UpdateURL` a un URL di Web.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)