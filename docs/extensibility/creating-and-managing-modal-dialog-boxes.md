---
title: Creazione e la gestione delle finestre di dialogo modale | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14b1e39e4479b0b6b909c625e1e8b6ad19955d30
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-and-managing-modal-dialog-boxes"></a>Creazione e la gestione delle finestre di dialogo modale
Quando si crea una finestra di dialogo modale in Visual Studio, è necessario assicurarsi che la finestra padre della finestra di dialogo è disabilitata quando viene visualizzata la finestra di dialogo, quindi abilitare nuovamente la finestra padre dopo aver chiuso la finestra di dialogo. Se non farlo, si potrebbe ricevere l'errore: "Microsoft Visual Studio non è stato chiuso perché è attiva una finestra di dialogo modale. Chiudere la finestra di dialogo attiva e riprovare."  
  
 Esistono due modi. Se si dispone di una finestra di dialogo WPF, è consigliabile derivare da <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>e quindi chiamare <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> per visualizzare la finestra di dialogo. In questo caso, non è necessario gestire lo stato modale della finestra padre.  
  
 Se la finestra di dialogo non WPF, o per un altro motivo non è possibile derivare la finestra di dialogo classe <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, quindi è necessario ottenere l'elemento padre della finestra di dialogo chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> e gestire personalmente, lo stato modale chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> metodo con un parametro pari a 0 (false) prima di visualizzare la finestra di dialogo e la chiamata al metodo con un parametro di 1 (true) dopo aver chiuso la finestra di dialogo.  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>Creazione di una finestra di dialogo derivate da DialogWindow  
  
1.  Creare un progetto VSIX denominato **OpenDialogTest** e aggiungere un comando di menu denominato **OpenDialog**. Per ulteriori informazioni su come eseguire questa operazione, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Utilizzare il <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> (classe), è necessario aggiungere riferimenti agli assembly seguenti (nella scheda Framework del **Aggiungi riferimento** la finestra di dialogo):  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   System.Xaml  
  
3.  In OpenDialog.cs, aggiungere la seguente `using` istruzione:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4.  Dichiarare una classe denominata **TestDialogWindow** che deriva da <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:  
  
    ```csharp  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5.  Per essere in grado di ridurre e ingrandire la finestra di dialogo, impostare <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> e <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> su true:  
  
    ```csharp  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6.  Nel **OpenDialog.ShowMessageBox** (metodo), sostituire il codice esistente con il seguente:  
  
    ```csharp  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7.  Compilare ed eseguire l'applicazione. L'istanza sperimentale di Visual Studio dovrebbe essere visualizzato. Nel **strumenti** menu dell'istanza sperimentale dovrebbe essere un comando denominato **OpenDialog richiamare**. Quando si fa clic su questo comando, si dovrebbe vedere la finestra di dialogo. Dovrebbe essere possibile ridurre al minimo e ingrandire la finestra.  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>Creazione e gestione di una finestra di dialogo non derivata da DialogWindow  
  
1.  Per questa procedura, è possibile utilizzare il **OpenDialogTest** soluzione creata nella procedura precedente, con i riferimenti all'assembly stesso.  
  
2.  Aggiungere il seguente `using` dichiarazioni:  
  
    ```csharp  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3.  Creare una classe denominata **TestDialogWindow2** che deriva da <xref:System.Windows.Window>:  
  
    ```csharp  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4.  Aggiungere un riferimento a privata <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5.  Aggiungere un costruttore che imposta il riferimento <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```csharp  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6.  Nel **OpenDialog.ShowMessageBox** (metodo), sostituire il codice esistente con il seguente:  
  
    ```csharp  
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));  
  
    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);  
    //get the owner of this dialog  
    IntPtr hwnd;  
    uiShell.GetDialogOwnerHwnd(out hwnd);  
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;  
    uiShell.EnableModeless(0);  
    try  
    {  
        WindowHelper.ShowModal(testDialog2, hwnd);  
    }  
    finally  
    {  
        // This will take place after the window is closed.  
        uiShell.EnableModeless(1);  
    }  
    ```  
  
7.  Compilare ed eseguire l'applicazione. Nel **strumenti** menu verrà visualizzato un comando denominato **OpenDialog richiamare**. Quando si fa clic su questo comando, si dovrebbe vedere la finestra di dialogo.