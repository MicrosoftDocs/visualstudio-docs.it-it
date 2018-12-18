---
title: Aprire una finestra degli strumenti dinamiche | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c96250c79ea283117254a96875c3a1f03f4cb30b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="opening-a-dynamic-tool-window"></a>Aprire una finestra degli strumenti dinamiche
Le finestre degli strumenti sono in genere aperto da un comando in un menu o un equivalente di tasti di scelta rapida. In alcuni casi, tuttavia, potrebbe essere una finestra degli strumenti visualizzata ogni volta che si applica uno specifico contesto UI e si chiude quando il contesto dell'interfaccia utente non è più valido. Le finestre degli strumenti come questi vengono chiamate *dinamica* o *visibili automaticamente*.  
  
> [!NOTE]
>  Per un elenco di contesti dell'interfaccia utente predefiniti, vedere <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>. Per il  
  
 Se si desidera aprire una finestra degli strumenti dinamiche all'avvio ed è possibile che l'errore durante la creazione, è necessario implementare la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> interfaccia e testare le condizioni di errore nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> metodo. Affinché la shell di sapere che si dispone di una finestra degli strumenti dinamiche che deve essere aperta all'avvio, è necessario aggiungere il `SupportsDynamicToolOwner` valore (impostato su 1) per la registrazione del pacchetto. Questo valore non è una parte dello standard <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, pertanto è necessario creare un attributo personalizzato per aggiungerlo. Per ulteriori informazioni sugli attributi personalizzati, vedere [utilizzando un attributo di registrazione personalizzato per registrare un'estensione](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).  
  
 Utilizzare <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> per aprire una finestra degli strumenti. La finestra degli strumenti viene creata in base alle esigenze.  
  
> [!NOTE]
>  Una finestra degli strumenti dinamica può essere chiusa dall'utente. Se si desidera creare un comando di menu per l'utente è possibile riaprire la finestra degli strumenti, il comando di menu deve essere abilitato nello stesso contesto dell'interfaccia utente che apre la finestra degli strumenti e disabilitata in caso contrario.  
  
### <a name="to-open-a-dynamic-tool-window"></a>Per aprire una finestra degli strumenti dinamiche  
  
1.  Creare un progetto VSIX denominato **DynamicToolWindow** e aggiungere un modello di elemento della finestra dello strumento denominato **DynamicWindowPane.cs**. Per ulteriori informazioni, vedere [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  Nel file DynamicWindowPanePackage.cs, individuare la dichiarazione di DynamicWindowPanePackage. Aggiungere il <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> e gli attributi T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute per registrare la finestra degli strumenti.  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackageGuids.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     In questo modo viene registrata la finestra degli strumenti denominata DynamicWindowPane come finestra temporanea che non è persistente quando Visual Studio viene chiuso e riaperto. Viene aperto DynamicWindowPane ogni volta che <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> applica e chiusa in caso contrario.  
  
3.  Compilare il progetto e avviare il debug. L'istanza sperimentale dovrebbe essere visualizzato. La finestra degli strumenti non verrà visualizzato.  
  
4.  Aprire un progetto nell'istanza sperimentale. Della finestra dello strumento.