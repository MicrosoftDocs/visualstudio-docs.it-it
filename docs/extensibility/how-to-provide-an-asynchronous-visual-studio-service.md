---
title: 'Procedura: fornire un servizio di Visual Studio asincrona | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b4754ccf4a7a66151ad8fb351996c1520dc9483c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Procedura: fornire un servizio di Visual Studio asincrona
Se si desidera ottenere un servizio senza bloccare il thread dell'interfaccia utente, è necessario creare un servizio asincrono e caricare il pacchetto in un thread in background. Per questo scopo è possibile utilizzare un <xref:Microsoft.VisualStudio.Shell.AsyncPackage> piuttosto che un <xref:Microsoft.VisualStudio.Shell.Package>, aggiungere il servizio con metodi asincroni speciale del pacchetto asincrona.
  
 Per informazioni su come fornire servizi di Visual Studio sincroni, vedere [procedura: fornire un servizio](../extensibility/how-to-provide-a-service.md).  
  
## <a name="implementing-an-asynchronous-service"></a>Implementazione di un servizio asincrono  
  
1.  Creare un progetto VSIX (**File > Nuovo > progetto > c# > Extensiblity > progetto VSIX**). Denominare il progetto **TestAsync**.  
  
2.  Aggiungere al progetto un pacchetto VSPackage. Selezionare il nodo del progetto nel **Esplora** e fare clic su **Aggiungi > Nuovo elemento > elementi di Visual c# > estendibilità > pacchetto di Visual Studio**. Nome del file **TestAsyncPackage.cs**.  
  
3.  In TestAsyncPackage.cs, modificare il pacchetto da cui ereditare AsyncPackage anziché pacchetto:  
  
    ```csharp  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  Per implementare un servizio, è necessario creare tre tipi:  
  
    -   Un'interfaccia che identifica il servizio. Molte di queste interfacce sono vuote, vale a dire, non hanno nessun metodo vengono utilizzate solo per le query del servizio.
  
    -   Un'interfaccia che descrive l'interfaccia del servizio. Questa interfaccia include i metodi da implementare.  
  
    -   Una classe che implementa il servizio e l'interfaccia del servizio.  
  
5.  Nell'esempio seguente viene illustrata un'implementazione di base dei tre tipi. Il costruttore della classe del servizio deve impostare il provider del servizio. In questo esempio il servizio verrà aggiunto solo al file di codice del pacchetto.  
  
6.  Aggiungere le seguenti istruzioni using al file del pacchetto:  
  
    ```csharp  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```  
  
7.  Di seguito è riportata l'implementazione del servizio asincrona. Si noti che è necessario impostare il provider del servizio asincrono anziché il provider del servizio sincrone nel costruttore:  
  
    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService  
    {  
        private IAsyncServiceProvider asyncServiceProvider;  
        
        public TextWriterService(IAsyncServiceProvider provider)  
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;  
        }
        
        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            // We have to use JoinableTaskFactory as code will switch to main thread in some parts
            await ThreadHelper.JoinableTaskFactory.RunAsync(async () =>
            {
                await TaskScheduler.Default;
                // do background operations that involve IO or other async methods
                
                await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);               
                // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
                // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.
                
                IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
                // use Visual Studio services to continue initialization
            });
        }
        
        public async Task WriteLineAsync(string path, string line)  
        {  
            StreamWriter writer = new StreamWriter(path);  
            await writer.WriteLineAsync(line);  
            writer.Close();  
        }  
    }  

    public interface STextWriterService  
    {  
    }  
    
    public interface ITextWriterService   
    {  
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);  
    }  
    ```  
  
## <a name="registering-a-service"></a>La registrazione di un servizio  
 Per registrare un servizio, aggiungere il <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> per il pacchetto che fornisce il servizio. Diversi per la registrazione di un servizio sincrone, è necessario assicurarsi che sia il pacchetto di servizio supporta il caricamento asincrono:
  
-   È necessario aggiungere il **AllowsBackgroundLoading = true** campo per il <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> per assicurare pacchetto può essere inizializzato in modo asincrono per ulteriori informazioni sul PackageRegistrationAttribute, vedere [registrazione e Annullamento della registrazione VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
-   È necessario aggiungere il **IsAsyncQueryable = true** campo il <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> affinché l'istanza del servizio può essere inizializzata in modo asincrono.

 Di seguito è riportato un esempio di un AsyncPackage con una registrazione servizio asincrone:
  
```csharp  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## <a name="adding-a-service"></a>Aggiunta di un servizio  
  
1.  In TestAsyncPackage.cs, rimuovere il `Initialize()` ed eseguire l'override di `InitializeAsync()` metodo. Aggiungere il servizio e aggiungere un metodo di callback per creare i servizi. Di seguito è riportato un esempio dell'inizializzatore asincrona di aggiunta di un servizio:  
  
    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }  
  
    ```  
  
2.  Aggiungere un riferimento a Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.  
  
3.  Implementare il metodo di callback come un metodo asincrono che crea e restituisce il servizio.  
  
    ```csharp  
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        TextWriterService service = new TextWriterService(this);  
        await service.InitializeAsync(cancellationToken);
        return service;
    }  
  
    ```  
  
## <a name="using-a-service"></a>Utilizzo di un servizio  
 È ora possibile ottenere il servizio e utilizzare i relativi metodi.  
  
1.  Viene illustrato questo nell'inizializzatore, ma è possibile ottenere il servizio in qualsiasi punto che si desidera utilizzare il servizio.  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync(<userpath>), "this is a test");  
  
    }  
  
    ```  
  
     Non dimenticare di modificare  *\<userpath >* per un nome di file e un percorso appropriato nel computer.  
  
2.  Compilare ed eseguire il codice. Quando viene visualizzata l'istanza sperimentale di Visual Studio, aprire una soluzione. In questo modo il AsyncPackage per autoload. Quando è stato eseguito l'inizializzatore, si deve trovare un file nel percorso specificato.  
  
## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Utilizzo di un servizio asincrono in un gestore del comando  
 Di seguito è riportato un esempio di come utilizzare un servizio asincrono in un comando di menu. È possibile utilizzare la procedura qui illustrata per utilizzare il servizio in altri metodi non asincrona.  
  
1.  Aggiungere un comando di menu al progetto. (Nel **Esplora**, selezionare il nodo del progetto, pulsante destro del mouse e selezionare **Aggiungi / nuovo elemento / Extensibility personalizzati di comando /**.) Denominare il file di comando **TestAsyncCommand.cs.**  
  
2.  Il modello di comando personalizzato aggiunge nuovamente il `Initialize()` metodo al file TestAsyncPackage.cs per inizializzare il comando. Il metodo Initialize (), copiare la riga che inizializza il comando. Il codice dovrebbe essere simile al seguente:  
  
    ```csharp
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Spostare la riga di `InitializeAsync()` metodo nel file AsyncPackageForService.cs. Poiché si tratta di un'inizializzazione asincrona, è necessario passare al thread principale prima di inizializzare il comando utilizzando <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Dovrebbe risultare simile al seguente:  
  
    ```csharp  
  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  

        ITextWriterService textService =   
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync((<userpath>, "this is a test");  
  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        TestAsyncCommand.Initialize(this);
    }  
  
    ```  
  
3.  Eliminare il `Initialize()` metodo.  
  
4.  Nel file TestAsyncCommand.cs, trovare il `MenuItemCallback()` metodo. Eliminare il corpo del metodo.  
  
5.  Aggiungere un'istruzione using:  
  
    ```csharp 
    using System.IO;  
    ```  
  
6.  Aggiungere un metodo asincrono denominato `UseTextWriterAsync()`, che ottiene il servizio e utilizza i metodi:  
  
    ```csharp  
    private async System.Threading.Tasks.Task UseTextWriterAsync()  
    {  
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =   
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))  
              as ITextWriterService;  

        // don't forget to change <userpath> to a local path  
        await textService.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  Chiamare questo metodo dal `MenuItemCallback()` metodo:  
  
    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        UseTextWriterAsync();  
    }  
  
    ```  
  
8.  Compilare la soluzione e avviare il debug. Quando viene visualizzata l'istanza sperimentale di Visual Studio, passare al **strumenti** menu e cercare il **richiamare TestAsyncCommand** voce di menu. Quando viene selezionata, il TextWriterService scrive il file specificato. (Non necessario aprire una soluzione, poiché il comando richiamato comporta il pacchetto da caricare.)  
  
## <a name="see-also"></a>Vedere anche  
 [Uso e fornitura di servizi](../extensibility/using-and-providing-services.md)
