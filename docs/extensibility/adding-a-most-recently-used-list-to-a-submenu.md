---
title: Aggiunta di elenco per un sottomenu utilizzati una più di recente | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 67eb08feff5d8edd1251c8fcff09d8f148b51b96
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-most-recently-used-list-to-a-submenu"></a>Aggiunta di una più recente di elenco per un sottomenu usati
Questa procedura dettagliata si basa su dimostrazioni in [aggiunta di un sottomenu a un Menu](../extensibility/adding-a-submenu-to-a-menu.md)e viene illustrato come aggiungere un elenco dinamico di un sottomenu. L'elenco dinamico costituisce la base per la creazione di un elenco più recente (MRU).  
  
 Un elenco di menu dinamico inizia con un segnaposto in un menu. Ogni volta che viene visualizzato il menu, l'ambiente di sviluppo integrato (IDE) di Visual Studio chiede il pacchetto VSPackage per tutti i comandi che devono essere visualizzati come il segnaposto. Un elenco dinamico può verificarsi in qualsiasi punto in un menu. Tuttavia, elenchi dinamici vengono in genere archiviati e visualizzati nel sottomenu o al fondo del menu. Tramite questi modelli di progettazione, si attiva l'elenco dei comandi per espandere e comprimere senza modificare la posizione di altri comandi del menu dinamico. In questa procedura dettagliata, viene visualizzato l'elenco MRU dinamico nella parte inferiore di un sottomenu esistente, separato dal resto del sottomenu da una riga.  
  
 Tecnicamente, un elenco dinamico può inoltre essere applicato a una barra degli strumenti. Tuttavia, se ne sconsiglia l'utilizzo di tali poiché una barra degli strumenti deve rimanere invariato, a meno che l'utente accetta i passaggi dettagliati per modificarlo.  
  
 Questa procedura dettagliata crea un elenco di quattro elementi che modificano l'ordine ogni volta che uno di essi (Sposta l'elemento selezionato nella parte superiore dell'elenco).  
  
 Per ulteriori informazioni sui menu e i file con estensione vsct, vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-an-extension"></a>Creazione di un'estensione  
  
-   Seguire le procedure in [aggiunta di un sottomenu a un Menu](../extensibility/adding-a-submenu-to-a-menu.md) per creare il sottomenu che viene modificato nelle procedure seguenti.  
  
 Le procedure descritte in questa procedura dettagliata si presuppongono che il nome del pacchetto VSPackage è `TopLevelMenu`, ovvero il nome utilizzato nel [aggiunta di un Menu alla barra dei Menu di Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).  
  
## <a name="creating-a-dynamic-item-list-command"></a>Creazione di un comando di elenco di voci dinamiche  
  
1.  Aprire TestCommandPackage.vsct.  
  
2.  Nel `Symbols` nella sezione di `GuidSymbol` nodo denominato guidTestCommandPackageCmdSet, aggiungere il simbolo per il `MRUListGroup` gruppo e `cmdidMRUList` comando, come indicato di seguito.  
  
    ```csharp  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  Nel `Groups` sezione, aggiungere il gruppo dichiarato dopo le voci di gruppo esistente.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  Nel `Buttons` sezione, aggiungere un nodo per rappresentare il comando appena dichiarato, dopo i movimenti pulsante esistente.  
  
    ```csharp  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"  
        type="Button" priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />  
        <CommandFlag>DynamicItemStart</CommandFlag>  
        <Strings>  
            <CommandName>cmdidMRUList</CommandName>  
            <ButtonText>MRU Placeholder</ButtonText>  
                </Strings>  
    </Button>  
    ```  
  
     Il `DynamicItemStart` flag è abilitato il comando deve essere generato in modo dinamico.  
  
5.  Compilare il progetto e avviare il debug per testare la visualizzazione del nuovo comando.  
  
     Nel **TestMenu** menu, fare clic su nuovo sottomenu, **sottomenu**, per visualizzare il nuovo comando **MRU segnaposto**. Dopo aver implementato un elenco dinamico di comandi nella procedura successiva, l'etichetta del comando verrà sostituita da tale elenco ogni volta che viene aperto il sottomenu.  
  
## <a name="filling-the-mru-list"></a>Riempimento di tale elenco  
  
1.  In TestCommandPackageGuids.cs, aggiungere le righe seguenti dopo l'ID di comando esistenti nel `TestCommandPackageGuids` definizione di classe.  
  
    ```csharp  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  In TestCommand.cs aggiungere la seguente istruzione using.  
  
    ```csharp  
    using System.Collections;  
    ```  
  
3.  Aggiungere il codice seguente nel costruttore TestCommand dopo l'ultima chiamata AddCommand. Il `InitMRUMenu` verranno definiti in un secondo momento  
  
    ```csharp  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  Aggiungere il codice seguente nella classe TestCommand. Questo codice inizializza l'elenco di stringhe che rappresentano gli elementi da visualizzare nell'elenco MRU.  
  
    ```csharp  
    private int numMRUItems = 4;  
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;  
    private ArrayList mruList;  
  
    private void InitializeMRUList()  
    {  
        if (null == this.mruList)  
        {  
            this.mruList = new ArrayList();  
            if (null != this.mruList)  
            {  
                for (int i = 0; i < this.numMRUItems; i++)  
                {  
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,  
                        "Item {0}", i + 1));  
                }  
            }  
        }  
    }  
    ```  
  
5.  Dopo il `InitializeMRUList` metodo, aggiungere il `InitMRUMenu` metodo. Consente di inizializzare i comandi di menu elenco MRU.  
  
    ```csharp  
    private void InitMRUMenu(OleMenuCommandService mcs)  
    {  
        InitializeMRUList();  
        for (int i = 0; i < this.numMRUItems; i++)  
        {  
            var cmdID = new CommandID(  
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);  
            var mc = new OleMenuCommand(  
                new EventHandler(OnMRUExec), cmdID);  
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);  
            mcs.AddCommand(mc);  
        }  
    }  
    ```  
  
     È necessario creare un oggetto del comando di menu per ogni articolo possibili nell'elenco MRU. Le chiamate a IDE il `OnMRUQueryStatus` metodo per ogni elemento nell'elenco MRU fino a quando non sono presenti più elementi. Nel codice gestito, l'unico modo per l'ambiente IDE di sapere che non sono presenti più elementi è prima di creare tutti gli elementi possibili. Se si desidera, è possibile contrassegnare innanzitutto elementi aggiuntivi come non visibili in utilizzando `mc.Visible = false;` dopo aver creato il comando di menu. Questi elementi possono quindi essere reso visibili in un secondo momento utilizzando `mc.Visible = true;` nel `OnMRUQueryStatus` metodo.  
  
6.  Dopo il `InitMRUMenu` metodo, aggiungere il seguente `OnMRUQueryStatus` metodo. Questo è il gestore che imposta il testo per ogni elemento di recente.  
  
    ```csharp  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  Dopo il `OnMRUQueryStatus` metodo, aggiungere il seguente `OnMRUExec` metodo. Questo è il gestore per la selezione di un elemento di recente. Questo metodo consente di spostare l'elemento selezionato nella parte superiore dell'elenco e quindi Visualizza l'elemento selezionato in una finestra di messaggio.  
  
    ```csharp  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
                for (int i = MRUItemIndex; i > 0; i--)  
                {  
                    this.mruList[i] = this.mruList[i - 1];  
                }  
                this.mruList[0] = selection;  
                System.Windows.Forms.MessageBox.Show(  
                    string.Format(CultureInfo.CurrentCulture,  
                                  "Selected {0}", selection));  
            }  
        }  
    }  
  
    ```  
  
## <a name="testing-the-mru-list"></a>TALE elenco di test  
  
#### <a name="to-test-the-mru-menu-list"></a>Per testare l'elenco di menu MRU  
  
1.  Compilare il progetto e avviare il debug  
  
2.  Nel **TestMenu** menu, fare clic su **TestCommand richiamare**. Questa operazione consente di visualizzare una finestra di messaggio che indica che il comando è stato selezionato.  
  
    > [!NOTE]
    >  Questo passaggio è necessario forzare il pacchetto VSPackage per caricare e visualizzare correttamente tale elenco. Se si ignora questo passaggio, tale elenco non viene visualizzato.  
  
3.  Nel **Menu Test** menu, fare clic su **sottomenu**. Viene visualizzato un elenco di quattro elementi alla fine del sottomenu, di sotto di un separatore. Quando fa clic su **elemento 3**, una finestra di messaggio dovrà essere visualizzato e visualizzare il testo, "Selected Item 3". (Se non viene visualizzato l'elenco di quattro elementi, assicurarsi di aver seguito le istruzioni nel passaggio precedente.)  
  
4.  Aprire di nuovo il sottomenu. Si noti che **elemento 3** è ora nella parte superiore dell'elenco e gli altri elementi effettuato il push di una posizione verso il basso. Fare clic su **elemento 3** nuovamente e notare che la finestra di messaggio Visualizza ancora "Selected Item 3", che indica che il testo è stato spostato correttamente nella nuova posizione con l'etichetta del comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta dinamica di voci di menu](../extensibility/dynamically-adding-menu-items.md)