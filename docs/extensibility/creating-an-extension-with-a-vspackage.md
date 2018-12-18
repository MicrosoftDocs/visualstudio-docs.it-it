---
title: Creazione di un'estensione con un pacchetto VSPackage | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 706cdcd26df18af9ccd79b5bf83890c47b1faf57
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-an-extension-with-a-vspackage"></a>Creazione di un'estensione con un pacchetto VSPackage
Questa procedura dettagliata viene illustrato come creare un progetto VSIX e aggiungere un elemento di progetto VSPackage. Si utilizzerà il pacchetto VSPackage per ottenere il servizio Shell dell'interfaccia utente per visualizzare una finestra di messaggio.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vspackage"></a>Creazione di un pacchetto VSPackage  
  
1.  Creare un progetto VSIX denominato **FirstPackage**. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** nella finestra di dialogo **Visual c# / Extensibility**.  
  
2.  Quando si apre il progetto, aggiungere un modello di elemento di pacchetto di Visual Studio denominato **FirstPackage**. Nel **Esplora**del mouse sul nodo del progetto e scegliere **Aggiungi / nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra di dialogo, passa a **Visual c# / Extensibility** e selezionare **pacchetto di Visual Studio**. Nel **nome** campo nella parte inferiore della finestra, modificare il nome del file di comando in **FirstPackage.cs**.  
  
3.  Compilare il progetto e avviare il debug.  
  
     Viene visualizzata l'istanza sperimentale di Visual Studio. Per ulteriori informazioni sull'istanza sperimentale, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
4.  Nell'istanza sperimentale, aprire il **strumenti / estensioni e aggiornamenti** finestra. Verrà visualizzato il **FirstPackage** estensione qui. (Se si apre **estensioni e aggiornamenti** nell'istanza di lavoro di Visual Studio, non verrà visualizzato **FirstPackage**).  
  
## <a name="loading-the-vspackage"></a>Caricare il pacchetto VSPackage  
 A questo punto l'estensione non viene caricato, poiché non c'è niente che causa il caricamento. In genere, è possibile caricare un'estensione quando si interagisce con la relativa interfaccia utente (scelta di un comando di menu, aprire una finestra degli strumenti) oppure specificando che il pacchetto VSPackage devono essere caricati in un contesto dell'interfaccia utente specifico. Per ulteriori informazioni sul caricamento dei contesti di VSPackage e dell'interfaccia utente, vedere [VSPackage durante il caricamento](../extensibility/loading-vspackages.md). Per questa procedura, vi mostreremo come caricare un pacchetto VSPackage quando è aperta una soluzione.  
  
1.  Aprire il file FirstPackage.cs. Cercare la dichiarazione della classe FirstPackage. Sostituire gli attributi esistenti con i seguenti:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackage.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Aggiungere un messaggio che consente di sapere che ha caricato il pacchetto VSPackage. Metodo Initialize () del pacchetto VSPackage utilizziamo a tale scopo, in quanto è possibile ottenere servizi di Visual Studio solo dopo che è stato collocato il pacchetto VSPackage. (Per ulteriori informazioni su servizi, vedere [procedura: ottenere un servizio](../extensibility/how-to-get-a-service.md).) Sostituire il metodo Initialize () di FirstPackage con il codice che ottiene il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> service, ottiene il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia e chiama il relativo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> (metodo).  
  
    ```csharp  
    protected override void Initialize()  
    {  
        base.Initialize();  
  
        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "FirstPackage",  
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result));  
    }  
    ```  
  
3.  Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.  
  
4.  Aprire una soluzione nell'istanza sperimentale. Verrà visualizzato un messaggio che afferma **Initialize () all'interno del pacchetto prima**.