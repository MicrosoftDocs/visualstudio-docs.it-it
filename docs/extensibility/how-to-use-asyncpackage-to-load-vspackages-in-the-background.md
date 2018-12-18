---
title: 'Procedura: utilizzare AsyncPackage per caricare in Background VSPackage | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.technology: vs-ide-sdk
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: gregvanl
ms.author: gregvanl
ms.workload:
- vssdk
ms.openlocfilehash: bc014b2072c5e6472d17095f0c0789c35116a3c6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Procedura: utilizzare AsyncPackage per caricare i pacchetti VSPackage in Background
I/o disco può comportare il caricamento e l'inizializzazione di un pacchetto di Visual Studio. Se questo tipo i/o viene eseguita nel thread dell'interfaccia utente, può causare problemi di velocità di risposta. Per risolvere questo problema, Visual Studio 2015 è stato introdotto il <xref:Microsoft.VisualStudio.Shell.AsyncPackage> classe che consente il caricamento del pacchetto in un thread in background.  
  
## <a name="creating-an-asyncpackage"></a>Creazione di un AsyncPackage  
 È possibile avviare la creazione di un progetto VSIX (**File > Nuovo > progetto > Visual c# > estendibilità > progetto VSIX**) e l'aggiunta di un pacchetto VSPackage al progetto (fare clic con il pulsante destro sul progetto e **Aggiungi/nuovo elemento / elemento c# / Pacchetto di Studio Extensibility/Visual**). È quindi possibile creare i servizi e aggiungere i servizi per il pacchetto.  
  
1.  Il pacchetto da derivare <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.  
  
2.  Se si desidera fornire servizi a cui l'esecuzione di query può causare il pacchetto da caricare:  
  
     Per indicare a Visual Studio che il pacchetto è sicuro per il caricamento in background e per acconsentire questo comportamento, il <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> deve impostare **AllowsBackgroundLoading** proprietà su true nel costruttore dell'attributo.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     Per indicare a Visual Studio che è possibile creare un'istanza del servizio in un thread in background, è necessario impostare il <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> impostata su true il <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> costruttore.  
  
    ```csharp  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  Se si sta caricando tramite contesti dell'interfaccia utente, quindi è necessario specificare **PackageAutoLoadFlags.BackgroundLoad** per il <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> o il valore (0x2) nei flag scritto con il valore della voce di caricamento automatico del pacchetto.  
  
    ```csharp  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  Nel caso di operazioni di inizializzazione asincrona da eseguire, è necessario eseguire l'override <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Rimuovere il **Initialize** metodo fornito dal modello di progetto VSIX. (Il **Initialize** metodo **AsyncPackage** è sealed). È possibile utilizzare uno qualsiasi del <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> metodi per aggiungere servizi asincroni per il pacchetto.  
  
     Nota: Per chiamare **base. InitializeAsync()**, è possibile modificare il codice sorgente per:  
  
    ```csharp  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  È necessario prestare attenzione a non verificare RPC (Remote Procedure Call) dal codice di inizializzazione asincrona (in **InitializeAsync**). Questi può verificarsi quando si chiama <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> direttamente o indirettamente.  Quando sono necessari i carichi di sincronizzazione, il thread dell'interfaccia utente verrà bloccato tramite <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. Il modello di blocco predefinito Disabilita RPC. Ciò significa che se si tenta di utilizzare una chiamata RPC dalle attività asincrone, è un deadlock se il thread dell'interfaccia utente è in attesa per il pacchetto da caricare. L'alternativa generale consiste nell'effettuare il marshalling del codice per il thread dell'interfaccia utente se necessario utilizzando simile **Factory delle attività attive**del <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> o un altro meccanismo che non utilizza una chiamata RPC.  Non utilizzare **ThreadHelper.Generic.Invoke** o in genere di bloccare il thread chiamante è in attesa di ottenere nel thread UI.  
  
     Nota: È consigliabile evitare di utilizzare **GetService** o **QueryService** nel **InitializeAsync** metodo. Se è necessario utilizzare tali, è necessario passare al thread dell'interfaccia utente prima di tutto. L'alternativa consiste nell'utilizzare <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> dal **AsyncPackage** (eseguendo il cast a <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)  
  
 In c#: Creare un AsyncPackage:  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]       
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]   
public sealed class TestPackage : AsyncPackage   
{   
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)   
    {               
        this.AddService(typeof(SMyTestService), CreateService, true);   
        return Task.FromResult<object>(null);   
    }   
}  
```  
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Convertire un VSPackage esistente AsyncPackage  
 La maggior parte delle operazioni è analoga alla creazione di un nuovo **AsyncPackage**. È necessario seguire i passaggi da 1 a 5. Inoltre, è necessario richiedere prestare particolare attenzione nei casi seguenti:  
  
1.  Ricordarsi di rimuovere il **inizializzare** override era nel pacchetto.  
  
2.  Evitare i deadlock: potrebbe essere nascosta RPC nel codice che ora eseguite in un thread in background. È necessario assicurarsi che se si effettua una chiamata RPC (ad esempio **GetService**), è necessario passare al thread principale (1) o (2) utilizzare la versione asincrona dell'API, se presente (ad esempio **GetServiceAsync**).  
  
3.  Non passare tra thread troppo frequentemente. Provare a localizzare il lavoro che può verificarsi in un thread in background. In questo modo si riduce il tempo di caricamento.  
  
## <a name="querying-services-from-asyncpackage"></a>Query sui servizi di AsyncPackage  
 Un **AsyncPackage** può o non è possibile caricare in modo asincrono in base al chiamante. Ad esempio,  
  
-   Se il chiamante chiamato **GetService** o **QueryService** (entrambe le API sincrone) o  
  
-   Se il chiamante chiamato **IVsShell::LoadPackage** (o **IVsShell5::LoadPackageWithContext**) o  
  
-   Il carico viene attivato da un contesto dell'interfaccia utente, ma non è stato specificato che carica in modo asincrono è il meccanismo di contesto dell'interfaccia utente  
  
 quindi il pacchetto verrà caricato in modo sincrono.  
  
 Si noti che il pacchetto ha ancora un'opportunità (in fase di inizializzazione asincrona) per eseguire il lavoro dal thread UI, anche se il thread dell'interfaccia utente verranno bloccato per il completamento di operazioni. Se il chiamante utilizza **IAsyncServiceProvider** a query in modo asincrono per il servizio, quindi l'inizializzazione e carico verrà eseguiti in modo asincrono presupponendo che non bloccare immediatamente nell'oggetto attività risultante.  
  
 In c#: Come eseguire una query in modo asincrono di servizio:  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```
  
