---
title: Modifica dell'aspetto di un comando | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4a19793f16991bc61636a929822757823728a926
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="changing-the-appearance-of-a-command"></a>Modifica dell'aspetto di un comando
È possibile fornire feedback all'utente modificando l'aspetto di un comando. È ad esempio, un comando per un aspetto diverso quando non è disponibile. È possibile rendere i comandi disponibili o non disponibile, nascondere o visualizzarli, o selezionare o deselezionare le dal menu.  
  
 Per modificare l'aspetto di un comando, eseguire una delle azioni seguenti:  
  
-   Specifica i flag appropriati nella definizione di comando nel file tabella di comando.  
  
-   Utilizzare il <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> servizio.  
  
-   Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia e modificare gli oggetti comando non elaborato.  
  
 La procedura seguente viene illustrato come individuare e aggiornare l'aspetto di un comando tramite il Framework di pacchetto gestito (MPF).  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>Per modificare l'aspetto di un comando di menu  
  
1.  Seguire le istruzioni in [la modifica del testo di un comando di Menu](../extensibility/changing-the-text-of-a-menu-command.md) per creare una voce di menu denominato `New Text`.  
  
2.  Nel file ChangeMenuText.cs, aggiungere la seguente istruzione using:  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3.  Nel file ChangeMenuTextPackageGuids.cs, aggiungere la riga seguente:  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  Nel file ChangeMenuText.cs, sostituire il codice nel metodo ShowMessageBox con gli elementi seguenti:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  Ottenere il comando che si desidera aggiornare il <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> dell'oggetto e quindi impostare le proprietà appropriate per l'oggetto comando. Ad esempio, il metodo seguente rende il comando specificato da un comando di VSPackage impostare disponibile o non disponibile. Il codice seguente viene eseguita il voce di menu denominata `New Text` disponibile dopo che è stato fatto clic.  
  
    ```csharp  
    public bool ChangeMyCommand(int cmdID, bool enableCmd)  
    {  
        bool cmdUpdated = false;  
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))  
            as OleMenuCommandService;  
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);  
        MenuCommand mc = mcs.FindCommand(newCmdID);  
        if (mc != null)  
        {  
            mc.Enabled = enableCmd;  
            cmdUpdated = true;  
        }  
        return cmdUpdated;    }  
    }  
    ```  
  
6.  Compilare il progetto e avviare il debug. L'istanza sperimentale di Visual Studio dovrebbe essere visualizzato.  
  
7.  Nel **strumenti** menu, fare clic sul **richiamare ChangeMenuText** comando. A questo punto il nome del comando è **ChangeMenuText richiamare**, in modo che il gestore del comando non chiama ChangeMyCommand().  
  
8.  Nel **strumenti** menu dovrebbe essere **nuovo testo**. Fare clic su **nuovo testo**. Il comando dovrebbe ora essere grigio.  
  
## <a name="see-also"></a>Vedere anche  
 [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Come VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)   
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)