---
title: Aggiunta di un menu di scelta rapida in una finestra degli strumenti | Microsoft Docs
description: Informazioni su come aggiungere un menu di scelta rapida a una finestra degli strumenti in Visual Studio che viene visualizzata quando si fa clic con il pulsante destro del mouse su un pulsante, una casella di testo o uno sfondo della finestra.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3ba0eb2324812ca7536b361d602bb683d627c743
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097617"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Aggiungere un menu di scelta rapida in una finestra degli strumenti
In questa procedura dettagliata viene inserito un menu di scelta rapida in una finestra degli strumenti. Un menu di scelta rapida è un menu visualizzato quando un utente fa clic con il pulsante destro del mouse su un pulsante, una casella di testo o uno sfondo della finestra. I comandi di un menu di scelta rapida hanno lo stesso comportamento dei comandi di altri menu o barre degli strumenti. Per supportare un menu di scelta rapida, specificarlo nel file con *estensione vsct* e visualizzarlo in risposta al clic con il pulsante destro del mouse.

Una finestra degli strumenti è costituita da un controllo utente WPF in una classe della finestra degli strumenti personalizzata che eredita da <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> .

Questa procedura dettagliata illustra come creare un menu di scelta rapida come menu di Visual Studio, dichiarando voci di menu nel file con *estensione vsct* e quindi usando il Framework di pacchetto gestito per implementarli nella classe che definisce la finestra degli strumenti. Questo approccio semplifica l'accesso ai comandi di Visual Studio, agli elementi dell'interfaccia utente e al modello a oggetti di automazione.

In alternativa, se il menu di scelta rapida non accede alla funzionalità di Visual Studio, è possibile usare la <xref:System.Windows.FrameworkElement.ContextMenu%2A> proprietà di un elemento XAML nel controllo utente. Per altre informazioni, vedere [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).

## <a name="prerequisites"></a>Prerequisiti
A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-tool-window-shortcut-menu-package"></a>Creare il pacchetto del menu di scelta rapida della finestra degli strumenti

1. Creare un progetto VSIX denominato `TWShortcutMenu` e aggiungere un modello di finestra degli strumenti denominato **ShortcutMenu** . Per ulteriori informazioni sulla creazione di una finestra degli strumenti, vedere [creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="specifying-the-shortcut-menu"></a>Impostazione del menu di scelta rapida
Un menu di scelta rapida, ad esempio quello illustrato in questa procedura dettagliata, consente all'utente di effettuare una selezione da un elenco di colori utilizzati per riempire lo sfondo della finestra degli strumenti.

1. In *ShortcutMenuPackage. vsct* trovare nell'elemento GuidSymbol denominato guidShortcutMenuPackageCmdSet e dichiarare il menu di scelta rapida, il gruppo di menu di scelta rapida e le opzioni di menu. L'elemento GuidSymbol dovrebbe ora essere simile al seguente:

    ```xml
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />
        <IDSymbol name="ColorMenu" value="0x1000"/>
        <IDSymbol name="ColorGroup" value="0x1100"/>
        <IDSymbol name="cmdidRed" value="0x102"/>
        <IDSymbol name="cmdidYellow" value="0x103"/>
        <IDSymbol name="cmdidBlue" value="0x104"/>
    </GuidSymbol>
    ```

2. Immediatamente prima dell'elemento Buttons, creare un elemento menus e quindi definire il menu di scelta rapida.

    ```vb
    <Menus>
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">
        <Strings>
          <ButtonText>Color change</ButtonText>
          <CommandName>ColorChange</CommandName>
        </Strings>
      </Menu>
    </Menus>
    ```

    Un menu di scelta rapida non dispone di un elemento padre perché non fa parte di un menu o di una barra degli strumenti.

3. Creare un elemento groups con un elemento Group contenente le voci del menu di scelta rapida e associare il gruppo al menu di scelta rapida.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. Nell'elemento Buttons (pulsanti) definire i singoli comandi che verranno visualizzati nel menu di scelta rapida. L'elemento Button dovrebbe essere simile al seguente:

    ```xml
    <Buttons>
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
            <Icon guid="guidImages" id="bmpPic1" />
            <Strings>
                <ButtonText>ShortcutMenu</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Red</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Yellow</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Blue</ButtonText>
            </Strings>
        </Button>
    </Buttons>
    ```

5. In *ShortcutMenuCommand. cs* aggiungere le definizioni per il GUID del set di comandi, il menu di scelta rapida e le voci di menu.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Questi sono gli stessi ID di comando definiti nella sezione symbols del file *ShortcutMenuPackage. vsct* . Il gruppo di contesto non è incluso perché è necessario solo nel file con *estensione vsct* .

## <a name="implementing-the-shortcut-menu"></a>Implementazione del menu di scelta rapida
 Questa sezione implementa il menu di scelta rapida e i relativi comandi.

1. In *ShortcutMenu. cs* la finestra degli strumenti può ottenere il servizio di comando di menu, ma il controllo in essa contenuto non può. Nei passaggi seguenti viene illustrato come rendere disponibile il servizio comando di menu per il controllo utente.

2. In *ShortcutMenu. cs* aggiungere le direttive using seguenti:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Eseguire l'override del metodo Initialize () della finestra degli strumenti per ottenere il servizio dei comandi di menu e aggiungere il controllo, passando il servizio di comando di menu al costruttore:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. Nel costruttore della finestra degli strumenti ShortcutMenu rimuovere la riga che aggiunge il controllo. Il costruttore dovrebbe ora essere simile al seguente:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. In *ShortcutMenuControl. XAML. cs* aggiungere un campo privato per il servizio comando di menu e modificare il costruttore del controllo in modo da scegliere il servizio comando di menu. Usare quindi il servizio comando di menu per aggiungere i comandi del menu di scelta rapida. Il costruttore ShortcutMenuControl dovrebbe ora essere simile al codice seguente. Il gestore comando verrà definito in un secondo momento.

    ```csharp
    public ShortcutMenuControl(OleMenuCommandService service)
    {
        this.InitializeComponent();
        commandService = service;

        if (null !=commandService)
        {
            // Create an alias for the command set guid.
            Guid guid = new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet);

            // Create the command IDs.
            var red = new CommandID(guid, ShortcutMenuCommand.cmdidRed);
            var yellow = new CommandID(guid, ShortcutMenuCommand.cmdidYellow);
            var blue = new CommandID(guid, ShortcutMenuCommand.cmdidBlue);

            // Add a command for each command ID.
            commandService.AddCommand(new MenuCommand(ChangeColor, red));
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));
        }
    }
    ```

6. In *ShortcutMenuControl. XAML* aggiungere un <xref:System.Windows.UIElement.MouseRightButtonDown> evento all'elemento di livello principale <xref:System.Windows.Controls.UserControl> . Il file XAML dovrebbe ora essere simile al seguente:

    ```vb
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            Background="{DynamicResource VsBrush.Window}"
            Foreground="{DynamicResource VsBrush.WindowText}"
            mc:Ignorable="d"
            d:DesignHeight="300" d:DesignWidth="300"
            Name="MyToolWindow"
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">
        <Grid>
            <StackPanel Orientation="Vertical">
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>
            </StackPanel>
        </Grid>
    </UserControl>
    ```

7. In *ShortcutMenuControl. XAML. cs* aggiungere uno stub per il gestore eventi.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Aggiungere le direttive using seguenti allo stesso file:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. Implementare l' `MyToolWindowMouseRightButtonDown` evento come indicato di seguito.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
        if (null != commandService)
        {
            CommandID menuID = new CommandID(
                new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet),
                ShortcutMenuCommand.ColorMenu);
            Point p = this.PointToScreen(e.GetPosition(this));
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);
        }
    }
    ```

    Viene creato un <xref:System.ComponentModel.Design.CommandID> oggetto per il menu di scelta rapida, viene identificato il percorso del clic del mouse e viene aperto il menu di scelta rapida in tale posizione utilizzando il <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> metodo.

10. Implementare il gestore di comandi.

    ```csharp
    private void ChangeColor(object sender, EventArgs e)
    {
        var mc = sender as MenuCommand;

        switch (mc.CommandID.ID)
        {
            case ShortcutMenuCommand.cmdidRed:
                MyToolWindow.Background = Brushes.Red;
                break;
            case ShortcutMenuCommand.cmdidYellow:
                MyToolWindow.Background = Brushes.Yellow;
                break;
            case ShortcutMenuCommand.cmdidBlue:
                MyToolWindow.Background = Brushes.Blue;
                break;
        }
    }
    ```

    In questo caso, solo un metodo gestisce gli eventi per tutte le voci di menu identificando <xref:System.ComponentModel.Design.CommandID> e impostando di conseguenza il colore di sfondo. Se le voci di menu contenevano comandi non correlati, sarebbe stato creato un gestore eventi separato per ogni comando.

## <a name="test-the-tool-window-features"></a>Testare le funzionalità della finestra degli strumenti

1. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

2. Nell'istanza sperimentale, fare clic su **Visualizza/altre finestre**, quindi fare clic su **ShortcutMenu**. Questa operazione dovrebbe visualizzare la finestra degli strumenti.

3. Fare clic con il pulsante destro del mouse nel corpo della finestra degli strumenti. Verrà visualizzato un menu di scelta rapida con un elenco di colori.

4. Fare clic su un colore nel menu di scelta rapida. Il colore di sfondo della finestra degli strumenti deve essere impostato sul colore selezionato.

## <a name="see-also"></a>Vedi anche
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
- [Uso e fornitura di servizi](../extensibility/using-and-providing-services.md)
