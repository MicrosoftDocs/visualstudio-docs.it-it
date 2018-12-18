---
title: Aggiunta di un Controller di Menu per una barra degli strumenti | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 63db98df400333216f5e753f8b6f82a61e785cd5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-menu-controller-to-a-toolbar"></a>Aggiunta di un Controller di Menu per una barra degli strumenti
Questa procedura dettagliata si basa il [aggiunta di una barra degli strumenti a una finestra degli strumenti](../extensibility/adding-a-toolbar-to-a-tool-window.md) procedura dettagliata e viene illustrato come aggiungere un controller di menu finestra degli strumenti. I passaggi illustrati di seguito è possibile applicare anche alla barra degli strumenti creati nel [aggiunta di una barra degli strumenti](../extensibility/adding-a-toolbar.md) procedura dettagliata.  
  
 Un controller di menu è un controllo di divisione. Il lato sinistro del controller di menu Mostra il comando utilizzato per ultimo e può essere eseguita facendovi clic sopra. La parte destra del controller di menu è una freccia che, quando si fa clic, viene aperto un elenco di comandi aggiuntivi. Quando si sceglie un comando nell'elenco, l'esecuzione del comando, e sostituisce il comando sul lato sinistro del controller di menu. In questo modo, il controller di menu opera come un pulsante di comando che mostra sempre il comando utilizzato per ultimo da un elenco.  
  
 I controller di menu possono essere visualizzati nei menu, ma vengono spesso utilizzati nelle barre degli strumenti.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-controller"></a>Creazione di un Controller di Menu  
  
#### <a name="to-create-a-menu-controller"></a>Per creare un controller di menu  
  
1.  Seguire le procedure descritte in [aggiunta di una barra degli strumenti a una finestra degli strumenti](../extensibility/adding-a-toolbar-to-a-tool-window.md) per creare una finestra degli strumenti con una barra degli strumenti.  
  
2.  In TWTestCommandPackage.vsct, passare alla sezione simboli. Nell'elemento GuidSymbol denominato **guidTWTestCommandPackageCmdSet**, dichiarare il controller di menu, gruppo di controller di menu e tre voci di menu.  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  Nella sezione menu, dopo l'ultima voce di menu, definire il controller di menu come menu.  
  
    ```xml  
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <CommandFlag>TextChanges</CommandFlag>  
        <CommandFlag>TextIsAnchorCommand</CommandFlag>  
        <Strings>  
            <ButtonText>Test Menu Controller</ButtonText>  
            <CommandName>Test Menu Controller</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     Il `TextChanges` e `TextIsAnchorCommand` flag devono essere inclusi per abilitare il controller di menu in modo da riflettere l'ultimo comando selezionato.  
  
4.  I gruppi di sezione, dopo l'ultima voce di gruppo, aggiungere il gruppo di controller di menu.  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     Impostando il controller di menu come elemento padre, tutti i comandi inseriti in questo gruppo verranno visualizzati nel controller di menu. Il `priority` attributo viene omesso, che imposta il valore predefinito pari a 0, perché sarà l'unico gruppo sul controller di menu.  
  
5.  Nella sezione pulsanti, dopo l'ultima voce di pulsante, aggiungere un elemento del pulsante per ognuna delle voci di menu.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 1</ButtonText>  
            <CommandName>MC Item 1</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 2</ButtonText>  
            <CommandName>MC Item 2</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 3</ButtonText>  
            <CommandName>MC Item 3</CommandName>  
        </Strings>  
    </Button>  
    ```  
  
6.  A questo punto, è possibile esaminare il controller di menu. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.  
  
    1.  Nel **visualizzazione / altre finestre** menu aprirlo **Test ToolWindow**.  
  
    2.  Il controller di menu viene visualizzato sulla barra degli strumenti nella finestra degli strumenti.  
  
    3.  Fare clic sulla freccia a destra del controller di menu per visualizzare i tre comandi possibili.  
  
     Si noti che, quando si sceglie un comando, il titolo del controller di menu cambia per visualizzare il comando. Nella sezione successiva, si aggiungerà il codice per attivare questi comandi.  
  
## <a name="implementing-the-menu-controller-commands"></a>Implementazione dei comandi di Controller di Menu  
  
1.  In TWTestCommandPackageGuids.cs, aggiungere gli ID di comando per i tre voci di menu dopo l'ID di comando esistenti.  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  In TWTestCommand.cs, aggiungere il codice seguente all'inizio della classe TWTestCommand.  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  Nel costruttore TWTestCommand, dopo l'ultima chiamata al `AddCommand` metodo, aggiungere il codice per inviare gli eventi per ogni comando tramite i gestori stesso.  
  
    ```csharp  
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=  
        TWTestCommandPackageGuids.cmdidMCItem3; i++)  
    {  
        CommandID cmdID = new  
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);  
        OleMenuCommand mc = new OleMenuCommand(new  
          EventHandler(OnMCItemClicked), cmdID);  
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);  
        commandService.AddCommand(mc);  
        // The first item is, by default, checked.   
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)  
        {  
            mc.Checked = true;  
            this.currentMCCommand = i;  
        }  
    }  
    ```  
  
4.  Aggiungere un gestore eventi alla classe TWTestCommand per contrassegnare il comando selezionato come selezionato.  
  
    ```csharp  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  Aggiungere un gestore eventi che consente di visualizzare una finestra di messaggio quando l'utente seleziona un comando nel controller di menu:  
  
    ```csharp  
    private void OnMCItemClicked(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            string selection;  
            switch (mc.CommandID.ID)  
            {  
                case c.cmdidMCItem1:  
                    selection = "Menu controller Item 1";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem2:  
                    selection = "Menu controller Item 2";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem3:  
                    selection = "Menu controller Item 3";  
                    break;  
  
                default:  
                    selection = "Unknown command";  
                    break;  
            }  
            this.currentMCCommand = mc.CommandID.ID;  
  
            IVsUIShell uiShell =  
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));  
            Guid clsid = Guid.Empty;  
            int result;  
            uiShell.ShowMessageBox(  
                       0,  
                       ref clsid,  
                       "Test Tool Window Toolbar Package",  
                       string.Format(CultureInfo.CurrentCulture,  
                                     "You selected {0}", selection),  
                       string.Empty,  
                       0,  
                       OLEMSGBUTTON.OLEMSGBUTTON_OK,  
                       OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
                       OLEMSGICON.OLEMSGICON_INFO,  
                       0,  
                       out result);  
        }  
    }  
    ```  
  
## <a name="testing-the-menu-controller"></a>Test Controller di Menu  
  
1.  Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.  
  
2.  Aprire il **ToolWindow Test** sul **visualizzazione / altre finestre** menu.  
  
     Il controller di menu e verrà visualizzato nella barra degli strumenti nella finestra degli strumenti **MC Item 1**.  
  
3.  Fare clic sul pulsante di controller di menu a sinistra della freccia.  
  
     Dovrebbe essere tre elementi, il primo dei quali è selezionato e include una casella di evidenziazione intorno relativa icona. Fare clic su **MC elemento 3**.  
  
     Verrà visualizzata una finestra di dialogo con il messaggio **è stato selezionato il controller di Menu elemento 3**. Si noti che il messaggio corrispondente al testo sul pulsante di controller di menu. Verrà visualizzato il pulsante di menu controller **MC elemento 3**.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta di una barra degli strumenti a una finestra degli strumenti](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Aggiunta di una barra degli strumenti](../extensibility/adding-a-toolbar.md)