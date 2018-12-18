---
title: Il caricamento di pacchetti VSPackage | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 008cd31bc3d9f909477089e608393f596bfb0682
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="loading-vspackages"></a>Il caricamento di pacchetti VSPackage
Pacchetti VSPackage vengono caricati in Visual Studio solo quando è richiesta la funzionalità. Ad esempio, un pacchetto VSPackage viene caricato quando Visual Studio Usa una factory del progetto o un servizio che implementa il pacchetto VSPackage. Questa funzionalità è denominata caricamento ritardato, che viene utilizzato ogni volta che è possibile migliorare le prestazioni.  
  
> [!NOTE]
>  Visual Studio è possibile determinare determinate informazioni VSPackage, ad esempio i comandi che offre un VSPackage, senza caricare il pacchetto VSPackage.  
  
 Pacchetti VSPackage impostabili per autoload in un contesto dell'interfaccia utente specifico, ad esempio, quando è aperta una soluzione. Il <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> questo contesto viene impostato dall'attributo.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Caricamento automatico un VSPackage in un contesto specifico  
  
-   Aggiungere il `ProvideAutoLoad` attributo per gli attributi di VSPackage:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Visualizzare i campi enumerati di <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> per un elenco di contesti dell'interfaccia utente e i relativi valori GUID.  
  
-   Impostare un punto di interruzione nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo.  
  
-   Compilare il pacchetto VSPackage e avviare il debug.  
  
-   Caricare una soluzione o crearne uno.  
  
     Il pacchetto VSPackage carica e si ferma in corrispondenza del punto di interruzione.  
  
## <a name="forcing-a-vspackage-to-load"></a>Utilizzo forzato di un VSPackage da caricare  
 In alcune circostanze potrebbe essere un pacchetto VSPackage forzare un altro VSPackage da caricare. Ad esempio, un VSPackage lightweight potrebbe caricare un VSPackage più grande in un contesto che non è disponibile come un CMDUIContext.  
  
 È possibile utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> metodo per forzare un VSPackage da caricare.  
  
-   Inserire questo codice nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> (metodo) del pacchetto VSPackage che impone un altro VSPackage caricare:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Quando viene inizializzato il pacchetto VSPackage, verrà imposto `PackageToBeLoaded` da caricare.  
  
     Non utilizzare il caricamento forzato per la comunicazione di VSPackage. Utilizzare [sull'utilizzo e la fornitura di servizi](../extensibility/using-and-providing-services.md) invece.
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)
