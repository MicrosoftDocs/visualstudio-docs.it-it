---
title: 'Procedura: ottenere un servizio | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cdf5bd925a034a64d8605c675704a0e894308ea3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-get-a-service"></a>Procedura: ottenere un servizio
È spesso necessario ottenere servizi di Visual Studio per accedere alle funzionalità diverse. In generale, un servizio di Visual Studio fornisce una o più interfacce che è possibile utilizzare. È possibile ottenere la maggior parte dei servizi da un pacchetto VSPackage.  
  
 Un VSPackage che deriva da <xref:Microsoft.VisualStudio.Shell.Package> e che è stato individuato correttamente può richiedere qualsiasi servizio globale. Poiché la classe del pacchetto implementa <xref:System.IServiceProvider>, qualsiasi VSPackage che deriva dal pacchetto è anche un provider di servizi.  
  
 Quando Visual Studio viene caricato un <xref:Microsoft.VisualStudio.Shell.Package>, passa un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> dell'oggetto per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodo durante l'inizializzazione. Si tratta di *posa* il pacchetto VSPackage. Classe del pacchetto esegue il wrapping di questo provider di servizi e fornisce il <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodo per i servizi.  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Recupero di un servizio da un VSPackage inizializzato  
  
1.  Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX, che conterrà gli asset di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `GetServiceExtension`. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** nella finestra di dialogo **Visual c# > Extensibility**.  
  
2.  Aggiungere un modello di elemento di comando personalizzato denominato **GetServiceCommand**. Nel **Aggiungi nuovo elemento** finestra di dialogo, passa a **Visual c# > estendibilità** e selezionare **comando personalizzato**. Nel **nome** campo nella parte inferiore della finestra, modificare il nome del file di comando in **GetServiceCommand.cs**. Per ulteriori informazioni su come creare un comando personalizzato, [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  In GetServiceCommand.cs, rimuovere il corpo del metodo MenuItemCommand e aggiungere il codice seguente:  
  
    ```csharp  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Questo codice ottiene un servizio SVsActivityLog e ne esegue il cast a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaccia, che consente di scrivere nel log attività. Per un esempio, vedere [procedura: utilizzare il registro attività](../extensibility/how-to-use-the-activity-log.md).  
  
4.  Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.  
  
5.  Dal menu Strumenti dell'istanza sperimentale, trovare il **GetServiceCommand richiamare** pulsante. Quando si fa clic su questo pulsante, si verrà visualizzata una finestra di messaggio che afferma **trovare il servizio registro attività.**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Recupero di un servizio da un contenitore di controllo o finestra dello strumento  
 In alcuni casi potrebbe essere necessario ottenere un servizio da una finestra degli strumenti o controllo contenitore che non è stato individuato, altrimenti è stato individuato con un provider di servizi che non conosce il servizio desiderato. Ad esempio, è possibile scrivere per la registrazione delle attività all'interno di un controllo.  
  
 Il metodo statico <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metodo si basa su un provider di servizio memorizzato nella cache che viene inizializzato la prima volta che un VSPackage è derivato da <xref:Microsoft.VisualStudio.Shell.Package> viene individuato.  
  
 Poiché prima che il pacchetto VSPackage viene individuato, viene chiamato il costruttore di VSPackage, servizi globali sono in genere non sono disponibili all'interno del costruttore di VSPackage. Vedere [procedura: risolvere i problemi relativi a servizi](../extensibility/how-to-troubleshoot-services.md) per una soluzione alternativa.  
  
 Di seguito è riportato un esempio della modalità per ottenere un servizio in una finestra degli strumenti o un altro elemento non VSPackage.  
  
```csharp  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>Recupero di un servizio dall'oggetto DTE  
 È inoltre possibile ottenere servizi da <xref:EnvDTE.DTEClass> oggetto. Tuttavia, è necessario ottenere l'oggetto DTE come un servizio da un pacchetto VSPackage o chiamando il metodo statico <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metodo.  
  
 Implementa l'oggetto DTE <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, che è possibile utilizzare per eseguire query per un servizio utilizzando <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.  
  
 Di seguito viene illustrato come ottenere un servizio dall'oggetto DTE.  
  
```csharp  
// Start with the DTE object, for example:   
// using EnvDTE;  
// DTE dte = (DTE)GetService(typeof(DTE));  
  
ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
if (sp != null)  
{  
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log != null)  
    {   
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: fornire un servizio](../extensibility/how-to-provide-a-service.md)   
 [Utilizzando e servizi](../extensibility/using-and-providing-services.md)   
 [Nozioni fondamentali sui servizi](../extensibility/internals/service-essentials.md)