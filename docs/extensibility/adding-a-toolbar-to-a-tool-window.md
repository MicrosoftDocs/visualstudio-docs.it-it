---
title: Aggiunta di una barra degli strumenti a una finestra degli strumenti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
caps.latest.revision: "48"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 07b5eea4fe6d5f58ec4b05563af253aeef0c5f6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-toolbar-to-a-tool-window"></a>Aggiunta di una barra degli strumenti a una finestra degli strumenti
Questa procedura dettagliata illustra come aggiungere una barra degli strumenti a una finestra degli strumenti.  
  
 Una barra degli strumenti è una striscia orizzontale o verticale che contiene i pulsanti associati a comandi. La lunghezza di una barra degli strumenti in una finestra degli strumenti è sempre quella della larghezza o altezza della finestra degli strumenti, a seconda della posizione in cui è ancorata la barra degli strumenti.  
  
 A differenza delle barre degli strumenti nell'IDE, una barra degli strumenti in una finestra degli strumenti deve essere ancorato e non può essere spostato o personalizzato. Se il pacchetto VSPackage è scritto in codice umanaged, la barra degli strumenti può essere ancorata in qualsiasi lato.  
  
 Per ulteriori informazioni su come aggiungere una barra degli strumenti, vedere [aggiunta di una barra degli strumenti](../extensibility/adding-a-toolbar.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>Creazione di una barra degli strumenti per una finestra degli strumenti  
  
1.  Creare un progetto VSIX denominato `TWToolbar` che include entrambi un comando di menu denominato **TWTestCommand** e una finestra degli strumenti denominata **TestToolWindow**. Per ulteriori informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md) e [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md). È necessario aggiungere il modello di elemento di comando prima di aggiungere il modello di finestra dello strumento.  
  
2.  In TWTestCommandPackage.vsct, cercare la sezione di simboli. Nel nodo GuidSymbol denominato guidTWTestCommandPackageCmdSet dichiarare una barra degli strumenti e un gruppo della barra degli strumenti, come indicato di seguito.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  Nella parte superiore del `Commands` sezione, creare un `Menus` sezione. Aggiungere un `Menu` elemento per definire la barra degli strumenti.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     Barre degli strumenti non possono essere annidati come sottomenu. Pertanto, non è necessario assegnare un elemento padre. Inoltre, non è necessario impostare la priorità, perché l'utente può spostare le barre degli strumenti. In genere, la posizione iniziale di una barra degli strumenti è definita a livello di codice, ma le successive modifiche apportate dall'utente vengono mantenute.  
  
4.  Nella sezione gruppi, definire un gruppo per contenere i comandi della barra degli strumenti.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  Nella sezione pulsanti, modificare l'elemento padre dell'elemento Button esistente al gruppo della barra degli strumenti in modo che venga visualizzata la barra degli strumenti.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Per impostazione predefinita, se una barra degli strumenti non dispone di alcun comando, non visualizzata.  
  
     Poiché la nuova barra degli strumenti non viene aggiunta automaticamente per la finestra degli strumenti, è necessario aggiungere in modo esplicito la barra degli strumenti. Questo è discusso nella sezione seguente.  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>Aggiunta la barra degli strumenti per la finestra degli strumenti  
  
1.  Aggiungere le righe seguenti in TWTestCommandPackageGuids.cs.  
  
    ```csharp  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  In TestToolWindow.cs aggiungere la seguente istruzione using.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    ```  
  
3.  Nel costruttore TestToolWindow aggiungere la riga seguente.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>La barra degli strumenti di test nella finestra degli strumenti  
  
1.  Compilare il progetto e avviare il debug. L'istanza sperimentale di Visual Studio dovrebbe essere visualizzato.  
  
2.  Nel **visualizzazione / altre finestre** menu, fare clic su **ToolWindow Test** per visualizzare la finestra degli strumenti.  
  
     Verrà visualizzata una barra degli strumenti (sembra che l'icona predefinita) nella parte superiore sinistra della finestra degli strumenti, sotto il titolo.  
  
3.  Sulla barra degli strumenti, fare clic sull'icona per visualizzare il messaggio **TWTestCommandPackage all'interno di TWToolbar.TWTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta di una barra degli strumenti](../extensibility/adding-a-toolbar.md)