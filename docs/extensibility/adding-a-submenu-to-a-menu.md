---
title: Aggiunta di un sottomenu a un Menu | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f6998c275aead7b12b107f700e699f5a82edd84e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-submenu-to-a-menu"></a>Aggiunta di un sottomenu a un Menu
Questa procedura dettagliata si basa sulla dimostrazione in [aggiunta di un Menu alla barra dei Menu di Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) viene mostrato come aggiungere un sottomenu di **TestMenu** menu.  
  
 Un menu secondario che verrà visualizzato in un altro menu è un sottomenu. Un sottomenu può essere identificato da una freccia che segue il relativo nome. Scegliendo il nome, il sottomenu e i relativi comandi da visualizzare.  
  
 Questa procedura dettagliata crea un sottomenu in un menu nella barra dei menu di Visual Studio e inserisce un nuovo comando dal sottomenu. La procedura dettagliata implementa anche il nuovo comando.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="adding-a-submenu-to-a-menu"></a>Aggiunta di un sottomenu a un Menu  
  
1.  Seguire i passaggi in [aggiunta di un Menu alla barra dei Menu di Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) per creare l'elemento di progetto e menu. I passaggi descritti in questa procedura dettagliata si presuppongono che il nome del progetto VSIX sia `TopLevelMenu`.  
  
2.  Aprire TestCommandPackage.vsct. Nel `<Symbols>` sezione, aggiungere un `<IDSymbol>` elemento per il sottomenu, uno per il gruppo di sottomenu e uno per il comando, tutto il `<GuidSymbol>` nodo denominato "guidTopLevelMenuCmdSet". Si tratta del nodo stesso che contiene il `<IDSymbol>` elemento per il menu di primo livello.  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  Aggiungere il sottomenu appena creato per il `<Menus>` sezione.  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     La coppia GUID/ID dell'elemento padre specifica il gruppo di menu che è stato generato in [aggiunta di un Menu alla barra dei Menu di Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), ed è un figlio del menu di primo livello.  
  
4.  Aggiungere il gruppo di menu definito nel passaggio 2 per il `<Groups>` sezione e renderlo un elemento figlio del sottomenu.  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  Aggiungere un nuovo `<Button>` elemento per il `<Buttons>` sezione per definire il comando creato nel passaggio 2 come voce del sottomenu.  
  
    ```xml  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <Strings>  
           <CommandName>cmdidTestSubCommand</CommandName>  
           <ButtonText>Test Sub Command</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
6.  Compilare la soluzione e avviare il debug. Verrà visualizzata l'istanza sperimentale.  
  
7.  Fare clic su **TestMenu** per visualizzare un sottomenu nuovo denominato **sottomenu**. Fare clic su **sottomenu** per aprire il sottomenu e visualizzare un nuovo comando **Test sottocomando**. Si noti che facendo clic su **Test sottocomando** non esegue alcuna operazione.  
  
## <a name="adding-a-command"></a>L'aggiunta di un comando  
  
1.  Aprire TestCommand.cs e aggiungere il seguente ID di comando dopo l'ID del comando.  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  Aggiungere il sottocomando. Trovare il costruttore di comando. Aggiungere le seguenti righe solo dopo la chiamata al `AddCommand` metodo.  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     Il `SubItemCallback` verrà definito il gestore del comando in un secondo momento. Il costruttore dovrebbe risultare simile al seguente:  
  
    ```csharp  
    private TestCommand(Package package)  
            {  
                if (package == null)  
                {  
                    throw new ArgumentNullException("package");  
                }  
  
                this.package = package;  
  
                OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
                if (commandService != null)  
                {  
                    var menuCommandID = new CommandID(CommandSet, CommandId);  
                    var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);  
                    commandService.AddCommand(menuItem);  
                    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3.  Aggiungere SubItemCallback(). Si tratta del metodo che viene chiamato quando si seleziona il comando nuovo nel sottomenu.  
  
    ```csharp  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "TestCommand",  
            string.Format(CultureInfo.CurrentCulture,  
            "Inside TestCommand.SubItemCallback()",  
            this.ToString()),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result);  
    }  
    ```  
  
4.  Compilare il progetto e avviare il debug. L'istanza sperimentale dovrebbe essere visualizzato.  
  
5.  Nel **TestMenu** menu, fare clic su **sottomenu** e quindi fare clic su **Test sottocomando**. Una finestra di messaggio dovrà essere visualizzato e visualizzare il testo, "Test comando all'interno di TestCommand.SubItemCallback()".  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta di un Menu alla barra dei Menu di Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
