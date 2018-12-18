---
title: Modifica del testo di un comando di Menu | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 48443396038e703ed226c035ede34861fe50fa61
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="changing-the-text-of-a-menu-command"></a>Modifica del testo di un comando di Menu
La procedura seguente viene illustrato come modificare l'etichetta di testo di un comando di menu utilizzando il <xref:System.ComponentModel.Design.IMenuCommandService> servizio.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>La modifica di un'etichetta di comando di menu con l'oggetto IMenuCommandService  
  
1.  Creare un progetto VSIX denominato `MenuText` con un comando di menu denominato **ChangeMenuText**. Per ulteriori informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Nel file .vstc, aggiungere il `TextChanges` flag per il comando di menu, come illustrato nell'esempio seguente.  
  
    ```xml  
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">  
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>TextChanges</CommandFlag>  
        <Strings>  
            <ButtonText>Invoke ChangeMenuText</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
3.  Nel file ChangeMenuText.cs, creare un gestore eventi che verrà chiamato prima che venga visualizzato il comando di menu.  
  
    ```csharp  
    private void OnBeforeQueryStatus(object sender, EventArgs e)  
    {  
        var myCommand = sender as OleMenuCommand;  
        if (null != myCommand)  
        {  
            myCommand.Text = "New Text";  
        }  
    }  
    ```  
  
     È inoltre possibile aggiornare lo stato del comando di menu in questo metodo modificando il <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, e <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> proprietà il <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> oggetto.  
  
4.  Nel costruttore ChangeMenuText, sostituire il codice di inizializzazione e la posizione comando originale con il codice che crea un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (anziché un `MenuCommand`) che rappresenta il comando di menu, aggiunge il <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> gestore eventi e offre il menu di comando per il servizio di comando di menu.  
  
     Ecco cosa dovrebbe risultare simile:  
  
    ```csharp  
    private ChangeMenuText(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.ShowMessageBox;  
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);  
            menuItem.BeforeQueryStatus +=  
                new EventHandler(OnBeforeQueryStatus);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
5.  Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale di Visual Studio.  
  
6.  Nel **strumenti** menu verrà visualizzato un comando denominato **ChangeMenuText richiamare**.  
  
7.  Fare clic sul comando. Verrà visualizzata la casella di messaggio annuncio che MenuItemCallback è stato chiamato. Appena si chiude la finestra di messaggio, si dovrebbe essere il nome del comando del menu Strumenti ora **nuovo testo**.
